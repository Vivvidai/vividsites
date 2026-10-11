Build HALFTONE — a drop-in animated WebGL background. Ship it as ONE
self-contained HTML file: one <canvas>, one inline <script>, one inline <style>. Raw
WebGL2, NO library, no build step, no CDN, no module graph. It has to drop into a page
whose build system you know nothing about, so it brings nothing with it.

═══ WHAT IT IS ═══
Two real halftone separations at a 60-degree offset over a domain-warped tone field, with the dots swelling into solid ink under the cursor. One full-screen triangle, no library.

Two real halftone separations at a 60-degree offset over a domain-warped tone
field. Each separation rotates into its own screen angle, tiles, and grows a dot
from the centre of each cell — the dot RADIUS carries the tone, which is what gives
the print moire where the two angles overlap. AREA, not radius, is proportional to
tone: a dot covering fraction t of a unit cell has radius sqrt(t/PI) = 0.564*sqrt(t),
and a larger coefficient makes mid-grey come out almost solid so the field reads as
black paper with holes in it. fwidth() on the cell coordinate keeps the dot edge one
pixel wide at any DPR. The cursor OPENS the screen — tone rises toward it, the dots
swell into a solid, and it reads as ink pooling rather than as a spotlight.

═══ THE FIVE THINGS THAT BREAK A DROP-IN BACKGROUND ═══

1. A BACKGROUND ON BOTH <html> AND <body>. Set one on each and body's stops being
   propagated to the viewport — it starts painting as an ordinary element box, which sits
   ABOVE the root stacking context's negative-z layer, and a canvas at `z-index: -1`
   disappears completely behind it. The page renders as a flat colour that looks exactly
   like a deliberate solid fill, with no error anywhere. Put the clear colour on <html>
   only. If the host page's <body> already has a background, give the canvas
   `z-index: 0` and the host's content `position: relative; z-index: 1` instead.

2. TWO TRIANGLES FOR A FULL-SCREEN QUAD. Two triangles rasterise a seam of duplicated
   fragments down the shared diagonal and cost an extra vertex. ONE oversized triangle
   from gl_VertexID covers the clip volume exactly once and needs no buffers, no
   attributes and no VAO:
       vec2 p = vec2((gl_VertexID << 1) & 2, gl_VertexID & 2);
       gl_Position = vec4(p * 2.0 - 1.0, 0.0, 1.0);

3. DPR CLAMPED ONCE. A 2x cap on a 3440px display is 47 million fragments a frame. Clamp
   TWICE — by device tier, then by AREA (`sqrt(MAX_FRAGMENTS / (w*h))`). A background
   that costs more than the page in front of it is a bug however good it looks.

4. `x += (target - x) * k` FOR THE POINTER EASE. That is only the intended speed at
   60fps; on a 120Hz panel it converges twice as fast and the lag — which IS the effect —
   is gone. Use `1 - pow(1 - k, dt * 60)`.

5. A BACKTICK ANYWHERE IN THE GLSL, INCLUDING IN A COMMENT. It ends the template literal
   the shader is interpolated into and the page dies with a JavaScript syntax error a
   hundred lines from the cause. The shader is fine; the symptom is "Unexpected
   identifier".

Also: gate the pointer on `(hover: hover) and (pointer: fine)` AND on "has the pointer
ever moved" — an ungated pointer sits at the default position forever and aims every
effect at one spot. Honour `prefers-reduced-motion` by feeding a FIXED time value rather
than by not drawing: a still frame of the field is the right answer, a blank canvas is
not. And if `getContext("webgl2")` returns null, set the clear colour on the canvas and
stop — the page behind it still works, which is the whole contract.

═══ THE FRAGMENT SHADER — VERBATIM ═══
#version 300 es
precision highp float;
out vec4 O;
uniform vec2 uRes; uniform float uTime; uniform vec2 uPointer; uniform float uOn;
uniform vec3 uPaper, uInkA, uInkB; uniform float uCell, uAngle, uBloom, uGrain;

float h21(vec2 p){ return fract(sin(dot(p, vec2(127.1,311.7))) * 43758.5453); }
float vn(vec2 p){
  vec2 i = floor(p), f = fract(p); vec2 u = f*f*(3.0-2.0*f);
  return mix(mix(h21(i), h21(i+vec2(1,0)), u.x),
             mix(h21(i+vec2(0,1)), h21(i+vec2(1,1)), u.x), u.y);
}
float fbm(vec2 p){
  float v = 0.0, a = 0.55;
  for (int i = 0; i < 4; i++){ v += a * vn(p); p = p * 2.01 + 9.1; a *= 0.5; }
  return v;
}
mat2 rot(float a){ float c = cos(a), s = sin(a); return mat2(c, -s, s, c); }

/* One separation of a halftone screen: rotate into the screen's own angle,
   tile, and grow a dot from the centre of each cell. The dot RADIUS carries
   the tone — this is a real screen, not a texture of dots multiplied by a
   gradient, which is what gives it the print moire when two angles overlap. */
float screenDot(vec2 sp, float tone, float ang, float cell){
  vec2 g = rot(ang) * sp / cell;
  vec2 c = fract(g) - 0.5;
  /* Area, not radius, carries the tone: a dot covering fraction t of a unit
     cell has radius sqrt(t/PI) = 0.564*sqrt(t). Using a bigger coefficient
     makes mid-grey come out almost solid, and the whole field reads as black
     paper with a few holes in it. */
  float r = sqrt(max(0.0, tone)) * 0.564;
  /* fwidth on the CELL coordinate keeps the dot edge one pixel wide at any
     DPR. A constant smoothstep width makes the whole field crawl on a
     retina display and look soft on a 1x one. */
  float aa = fwidth(g.x) * 1.2 + 0.0015;
  return smoothstep(r + aa, r - aa, length(c));
}

void main(){
  vec2 uv = gl_FragCoord.xy / uRes;
  vec2 sp = (gl_FragCoord.xy - 0.5 * uRes) / uRes.y;

  float t = uTime * 0.06;
  vec2 w = vec2(fbm(sp * 1.3 + t), fbm(sp * 1.3 - t + 5.2)) - 0.5;
  float field = fbm(sp * 1.9 + w * 0.9 + vec2(0.0, t * 1.4));

  /* The cursor OPENS the screen: tone rises toward it, so the dots swell into
     a solid and the field reads as ink pooling rather than as a spotlight. */
  vec2 pw = (uPointer - 0.5) * vec2(uRes.x / uRes.y, 1.0);
  float d = length(sp - pw);
  float bloom = exp(-(d * d) / (uBloom * uBloom)) * uOn;

  float tone = clamp(field * 1.15 - 0.30 + bloom * 0.62, 0.0, 1.0);

  /* Two separations at the classic 15 and 75 degree offset. One screen is a
     dot pattern; two at different angles is a PRINT. */
  float a = screenDot(sp, tone,               uAngle,           uCell);
  float b = screenDot(sp, tone * 0.72,        uAngle + 1.0472,  uCell * 1.18);

  vec3 col = uPaper;
  col = mix(col, uInkB, b * 0.42);
  col = mix(col, uInkA, a);

  col += (h21(gl_FragCoord.xy + fract(uTime) * 17.9) - 0.5) * uGrain;
  O = vec4(clamp(col, 0.0, 1.0), 1.0);
}

═══ THE HARNESS — VERBATIM ═══
Wrap the harness AND the per-background setup in one IIFE. The no-WebGL2 path is an
early `return` inside it; written as an `else` block it scopes every helper below it and
the setup code that follows cannot see any of them.

/* ── the smallest honest WebGL2 harness ─────────────────────────────────
   Raw WebGL2, no library. A background that pulls in 600KB of three.js to
   draw one full-screen triangle is not a background, it is a dependency. */
const RM = matchMedia('(prefers-reduced-motion: reduce)').matches;
const COARSE = matchMedia('(hover: none) and (pointer: coarse)').matches;
const FINE = matchMedia('(hover: hover) and (pointer: fine)').matches;
const MOBILE = innerWidth < 768 || COARSE;

const cv = document.getElementById('bg');
const gl = cv.getContext('webgl2', { antialias: false, alpha: false,
                                     powerPreference: 'high-performance' });
/* No WebGL2 is not an error the visitor should see as a black rectangle.
   Fall back to the flat clear colour and bail — the page it is behind still
   works, which is the whole contract of a background.
   This is an early RETURN inside the wrapping IIFE, not an `else` block: an
   else block scopes every helper below it, and the site's own main.js is
   concatenated after and cannot see any of them. */
if (!gl) { cv.style.background = CFG.clear; return; }

const VERT = `#version 300 es
/* ONE triangle, not a quad. Two triangles rasterise a seam of duplicated
   fragments down the diagonal and cost an extra vertex; a single oversized
   triangle covers the clip volume exactly once. */
void main(){
  vec2 p = vec2((gl_VertexID << 1) & 2, gl_VertexID & 2);
  gl_Position = vec4(p * 2.0 - 1.0, 0.0, 1.0);
}`;

function compile(type, src) {
  const sh = gl.createShader(type);
  gl.shaderSource(sh, src);
  gl.compileShader(sh);
  if (!gl.getShaderParameter(sh, gl.COMPILE_STATUS)) {
    /* Line-numbered, because a raw GLSL log gives you `0:74` and a wall of
       text you then have to count through by hand. */
    const log = gl.getShaderInfoLog(sh) || '';
    console.error(log + '\n' + src.split('\n')
      .map((l, i) => String(i + 1).padStart(3) + ' | ' + l).join('\n'));
    throw new Error('shader: ' + log.split('\n')[0]);
  }
  return sh;
}
const prog = gl.createProgram();
gl.attachShader(prog, compile(gl.VERTEX_SHADER, VERT));
gl.attachShader(prog, compile(gl.FRAGMENT_SHADER, FRAG));
gl.linkProgram(prog);
if (!gl.getProgramParameter(prog, gl.LINK_STATUS)) {
  throw new Error('link: ' + gl.getProgramInfoLog(prog));
}
gl.useProgram(prog);
const U = {};
for (let i = 0, n = gl.getProgramParameter(prog, gl.ACTIVE_UNIFORMS); i < n; i++) {
  const nm = gl.getActiveUniform(prog, i).name.replace(/\[0\]$/, '');
  U[nm] = gl.getUniformLocation(prog, nm);
}
const rgb = h => {
  const n = parseInt(h.slice(1), 16);
  return [((n >> 16) & 255) / 255, ((n >> 8) & 255) / 255, (n & 255) / 255];
};

/* DPR clamped twice — by tier, then by AREA. A 2x cap on a 3440px display is
   47 million fragments a frame, and a background that costs more than the
   page it is behind is a bug however pretty it is. */
const MAX_FRAG = CFG.maxFragments || 2.6e6;
let W = 0, H = 0, DPR = 1;
function fit() {
  const w = cv.clientWidth || innerWidth, h = cv.clientHeight || innerHeight;
  const byTier = Math.min(devicePixelRatio || 1, MOBILE ? 1.25 : (CFG.dprCap || 1.75));
  const byArea = Math.sqrt(MAX_FRAG / Math.max(1, w * h));
  const dpr = Math.max(0.6, Math.min(byTier, byArea));
  const nw = Math.round(w * dpr), nh = Math.round(h * dpr);
  if (nw === W && nh === H) return false;
  W = nw; H = nh; DPR = dpr;
  cv.width = W; cv.height = H;
  gl.viewport(0, 0, W, H);
  return true;
}
fit();
/* Safari fires resize every time the URL bar collapses, so on a coarse
   pointer a height-only change is ignored entirely. */
let lastW = innerWidth;
addEventListener('resize', () => {
  if (MOBILE && innerWidth === lastW) return;
  lastW = innerWidth; fit();
}, { passive: true });

const P = { x: 0.5, y: 0.5, tx: 0.5, ty: 0.5, on: 0 };
if (FINE && !MOBILE && CFG.pointer !== false) {
  addEventListener('pointermove', e => {
    P.tx = e.clientX / innerWidth;
    P.ty = 1 - e.clientY / innerHeight;
    P.on = 1;
  }, { passive: true });
}

const t0 = performance.now();
let last = t0, budget = 1000 / (MOBILE ? 30 : (CFG.fps || 60));
function loop(now) {
  requestAnimationFrame(loop);
  if (now - last < budget) return;
  const dt = Math.min(0.05, (now - last) / 1000) || 0.016;
  last = now;
  /* Frame-rate independent damping. `x += (t-x)*k` is only the intended speed
     at 60fps; on a 120Hz panel every eased value on the page is wrong. */
  const k = 1 - Math.pow(1 - 0.08, dt * 60);
  P.x += (P.tx - P.x) * k;
  P.y += (P.ty - P.y) * k;
  draw((now - t0) / 1000, dt);
}

═══ THE PER-BACKGROUND SETUP ═══
gl.uniform3fv(U.uPaper, rgb(CFG.paper));
gl.uniform3fv(U.uInkA, rgb(CFG.inkA));
gl.uniform3fv(U.uInkB, rgb(CFG.inkB));
gl.uniform1f(U.uCell, CFG.cell);
gl.uniform1f(U.uAngle, CFG.angle);
gl.uniform1f(U.uBloom, CFG.bloom);
gl.uniform1f(U.uGrain, CFG.grain);
function draw(t) {
  if (fit()) gl.viewport(0, 0, W, H);
  gl.uniform2f(U.uRes, W, H);
  gl.uniform1f(U.uTime, RM ? 5.0 : t);
  gl.uniform2f(U.uPointer, P.x, P.y);
  gl.uniform1f(U.uOn, P.on);
  gl.drawArrays(gl.TRIANGLES, 0, 3);
}
draw(0);
requestAnimationFrame(loop);

═══ FIXED PARAMETERS (BAKE THESE IN) ═══
clear = #f2efe7
ink = #1a1713
paper = #f2efe7
inkA = #151310
inkB = #d8442e
cell = 0.0145
angle = 0.2618
bloom = 0.34
grain = 0.012
dprCap = 1.5
maxFragments = 2400000
fps = 60

═══ DELIBERATELY ABSENT ═══
No library, no npm package, no CSS framework, no images, no fonts, no network
requests of any kind. The file is the product and it works offline.
