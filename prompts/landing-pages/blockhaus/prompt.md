# Build spec: BLOCKHAUS — a Lisbon 3D and interactive studio whose one-page site opens on a dark rounded window holding a live physics pile of glossy toy blocks, rings, capsules and pebbles that your cursor shoves, a click bursts apart with a lime flash and a drag ploughs through, then draws a twisted paper ribbon across the page, grows a showreel to full window and stacks fifty-eight toys into a little house that floods orange into the footer

Recreate this site as a single HTML file: one `index.html`, three.js r169 (0.169.0, `build/three.module.js`) from jsDelivr through
an import map (`three` and `three/addons/`), loaded with dynamic `import()` only AFTER the page's own UI is wired, with seven addons
(RoundedBoxGeometry, RoomEnvironment, EffectComposer, RenderPass, OutputPass, UnrealBloomPass, GTAOPass), Lenis 1.1.13 from jsDelivr
as a classic script, General Sans 400/500/600 from Fontshare and JetBrains Mono 400/500 from Google Fonts, twenty hosted files (a
designed hero still, a finale still, a reel poster, the 26-second reel as an mp4, and eight project key arts, each in a 1600 px and
an 800 px cut), and everything else written in the file: THREE separate three.js renderers, all procedural (no models, no
textures) — a hero toybox of 62 bodies (34 on phones) moved by a hand-written compound-sphere solver (spring to the pile, contact
impulses with restitution, friction and spin, a kinematic cursor sphere, a radial burst on click) under a PMREM room environment,
a soft shadow map and GTAO; a fixed page-space orthographic canvas that draws two flat twisted paper ribbons as you scroll, one
with a project card glued to its tip; and a pinned finale where 58 toy pieces fall and stack into a gabled house while 420
instanced toys orbit it and a neon halo blooms, ending in an orange circle flood. Around them: a loader where four rounded blocks
drop and stack into the logo glyph over a rolling three-digit counter; an SVG `path()` notch cut out of the hero window for the
headline tab; a pinned reel whose card grows from a thumbnail to the full window while "Show" and "reel" ride its edges and turn
white exactly inside it; a Grid / Index work toggle with a cursor-following peek; a rolling status ticker with live Lisbon time; a
hide-on-scroll header, a tile menu, a scroll gauge and a footer whose giant line rolls letter by letter. One requestAnimationFrame
loop steps Lenis and every system from `window.scrollY`; every scroll section is scrubbed, not timed; reveals are CSS transitions
toggled by an IntersectionObserver; the loader and the entrance use the Web Animations API; no tween library, no build step, no
framework. Every number below is the shipped build's, and the code is quoted whole.

## What it is
Blockhaus is a fictional 3D and interactive studio in Lisbon, and this is its one-page site, opening on a dark rounded window filled with a live physics pile of glossy toy blocks, rings, capsules and pebbles that your cursor pushes and a click scatters with a lime flash. Below it a paper ribbon draws itself across the page carrying a project card, a showreel grows from a thumbnail to the full window, eight projects sit in a grid that flips into an index, and a pinned finale stacks fifty-eight toy pieces into a little house before an orange flood becomes the footer.

- **The loader**: an ink screen. Four 44 px rounded blocks drop from 60vh above and stack into a 2 × 2 glyph (the last one orange)
  with a squash-and-settle, one at each quarter of the count; a huge General Sans counter `000 → 100` rolls digit by digit
  bottom-right; a mono note `Blockhaus / stacking the toybox` bottom-left. At 100 an orange wipe rises from the bottom, then the
  whole curtain pulls up off the page.
- **The hero** is a rounded window (`#16161A`, radius 20) under the fixed chrome, 72 px gutters, with its bottom-left corner cut
  away into a notch that holds the headline "Play-grade 3D / for *curious* brands." (curious in orange). Inside, a close camera
  (FOV 30) looks at a pile of 62 toys that overflows the frame: rounded cubes, long bricks, fat rings, capsules and squashed
  pebbles in glossy orange, satin bone, matte graphite, piano black and sheen lilac. They fall in from above as the curtain lifts,
  then breathe in a slow churn. Your cursor is an invisible sphere that shoves pieces aside and spins them; pressing makes it 30%
  bigger, so a drag ploughs a trench; a click (under 8 px, under 400 ms) bursts everything outward from that point and the orange
  pieces flash chartreuse for about 0.7 s. The camera leans up to .45 toward the cursor. Mono chips bottom-right (`push`,
  `click to scatter`, `press to shove`), a caption top-left `Fig. 00: the toybox`, and under the window a meta row: `Studio:
  Lisbon / Hong Kong`, `Est. 2017`, `Web · 3D · Motion · Physics`, `Scroll ↓` with a looping arrow.
- **The chrome**: the wordmark (a 2 × 2 block glyph, one block orange, and `blockhaus` at 30 px / 600) left; a centred mono ticker
  that rolls every 3.2 s through the booking line (computed from today: `Now booking Q1 ’27 · 3 seats left`), `Studio time 14:05
  Lisbon`, `Recently: Shoal Atlas is live`, `Toys built this year: 214`; right, an ink capsule `Start a project ↗` with a pulsing
  orange dot and a round paper menu button whose 2 × 2 dots turn into a rotated diamond of circles when open. The menu is a paper
  card of four tiles (`01 / Home` Toybox, `02 / Work` Play, `03 / Studio` People, `04 / Contact` Say hi), a newsletter row and an
  ink row `Blockhaus Lab: experiments ↗`. The header hides on the way down, returns on the way up and turns paper-on-ink over
  the finale. A mono scroll gauge bottom-right counts `000`–`100` beside a 64 px bar.
- **The statement**: "Serious craft, / built for play." at up to 152 px (second line indented 20vw), and a lead paragraph with a
  `How we play` pill in the right column. While it scrolls in, a flat paper ribbon (lilac face, orange back, one half-turn flip)
  draws itself in from the right edge, sweeping down to the left column, with a 360 px card (`Now playing: Shoal Atlas`) glued to
  its drawing tip, tilting with the tangent.
- **The reel**: a 280vh pinned stage. A small card (about 346 × 214 at 1440) sits mid-screen flanked by "Show" and "reel" in ink
  up to 180 px; as you scroll, the card grows to the full window, the two words ride its edges into opposite corners and turn
  white exactly where the card covers them, four crosshair ticks pin its corners and `Reel ’26: 00:26` / `Six worlds, half a
  minute` fade in. A 112 px orange `Play` disc follows the cursor over the card; a click opens a full-screen player.
- **Selected play (08)**: a staggered 12-column grid (7/5, then 5/7) of eight project cards that wipe up from a 12% clip, each with
  a `01 / 08` chip, an orange ↗ chip on hover, a mono discipline line and year, and the title with a sliding orange arrow. A Grid
  / Index toggle swaps to a ruled list whose rows fill with ink on hover while a 300 px preview follows the cursor.
- **The second statement**: "Things worth / touching, made to / outlast a scroll." with a tilted card (`Lab note 14: soft-body
  laces`) and two paragraphs; a second ribbon (orange face, lilac back) loops through it.
- **The finale**, "Fig. 01: the haus": a 480vh pinned dark stage. Centred caps "EVERY BLOCK / IS A DECISION. / STACK THEM WITH
  CARE" burst outward, each word along its own line from the centre, and fade as the camera orbits down; 58 toys fall in by
  height and stack into a gabled house (walls, round orange windows, a door gap, a brick roof, a capsule ridge, a lilac chimney, a
  ring weathervane, a garden) while a counter climbs `00 / 58 blocks placed` to `58 / 58`; 420 small toys orbit it in a storm and
  a neon orange-and-lilac halo opens behind it under bloom. "Fifty-eight blocks. / Zero *glue.*" shows, the storm rushes in, an
  orange circle grows from the centre to fill the screen, and the orange footer slides up over it.
- **The footer**: `Got something that should be touched?`, "Let's build it!" at up to 214 px whose letters roll up on hover, four
  columns (studio address, emails, follow links, a newsletter capsule) and a base row.

The palette is warm bone `#EEEBE4` (the page), paper `#F7F5F0` (pills, menu, chips), ink `#121212` and the hero window `#16161A`,
with ONE accent, signal orange `#FF5A1F`: the glyph block, the CTA dot, the headline's "curious", the play disc, the hover chips,
the toy plastic, the halo, the flood and the whole footer. Lilac `#B8A6FF` is the second colour, spent only in 3D (ribbon faces,
lilac toys, the halo's inner ring, the finale fill light); chartreuse `#D4FF3A` exists only as the click flash. Muted copy is
`#3A3936` and `#77736B`; rules are ink at .14; the finale is `#0E0E10`.

## Shell, libraries, fonts
The head. The watchdog is a classic script that runs before anything else (see Failure); Lenis is a classic script in the head;
the import map only names three.js, which the module imports dynamically later. There is no favicon.

```html
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>Blockhaus: play-grade 3D studio</title>
<meta name="description" content="Blockhaus is a small 3D and interactive studio. We build websites, launches and installations you can push, pull and poke.">
<meta name="theme-color" content="#EEEBE4">
<link rel="preconnect" href="https://api.fontshare.com" crossorigin>
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://api.fontshare.com/v2/css?f[]=general-sans@400,500,600&display=swap" rel="stylesheet">
<link href="https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500&display=swap" rel="stylesheet">
<link rel="preload" as="image" href="https://www.vividsites.app/media/flagship/blockhaus/hero-still.jpg">
<style>
/* the tokens and the whole stylesheet below */
</style>
<script>
/* watchdog, outside the module: if three.js / WebGL never boots, lift the loader onto the designed still */
window.__t0 = performance.now();
(function(){ try { var c = document.createElement('canvas'); if (!(c.getContext('webgl2') || c.getContext('webgl'))) document.documentElement.classList.add('nogl'); } catch (e) { document.documentElement.classList.add('nogl'); } })();
setTimeout(function(){
  if (window.__booted || window.__lifted) return;
  document.documentElement.classList.add('nogl', 'boot-fail');
  var l = document.getElementById('loader');
  if (l) { l.style.transition = 'opacity .6s'; l.style.opacity = '0'; setTimeout(function(){ l.style.display = 'none'; }, 650); }
  document.body && document.body.classList.remove('locked');
  window.__lifted = 'watchdog';
}, 10000);
</script>
<script src="https://cdn.jsdelivr.net/npm/lenis@1.1.13/dist/lenis.min.js"></script>
<script type="importmap">
{"imports":{
  "three":"https://cdn.jsdelivr.net/npm/three@0.169.0/build/three.module.js",
  "three/addons/":"https://cdn.jsdelivr.net/npm/three@0.169.0/examples/jsm/"
}}
</script>
</head>
```
At the end of `<body>`: ONE module script holding every system in the order of the sections below.
Faces: **General Sans** from the Fontshare CSS API — 400 for the display statements, section heads, project titles, reel words and
body; 500 for the hero headline, the loader count, menu tiles, pills, the finale caps and the footer line; 600 for the wordmark.
**JetBrains Mono** 400/500 from Google Fonts for every label (`.mono`: 11.5 px, 500, `.02em`, uppercase).

## Tokens and root
No rem ladder: px and `clamp()`. `--g` is the gutter, `clamp(16px, 5vw, 72px)` (72 at 1440); `--r` the window radius 20 (14 on
phones); `--ease` `cubic-bezier(.16,1,.3,1)` is the one curve for every CSS transition. `html` carries the bone; `body` is
transparent so the fixed ribbon canvas behind `main` shows through every light section. `body.locked` holds the scroll until the
loader lifts.

```css
:root{
  --bone:#EEEBE4; --bone-2:#E4E0D7; --paper:#F7F5F0; --ink:#121212; --ink-2:#3A3936; --mute:#77736B;
  --win:#16161A; --orange:#FF5A1F; --lilac:#B8A6FF; --lime:#D4FF3A;
  --g:clamp(16px,5vw,72px); --r:20px;
  --sans:"General Sans","Helvetica Neue",Arial,sans-serif;
  --mono:"JetBrains Mono",ui-monospace,Menlo,monospace;
  --ease:cubic-bezier(.16,1,.3,1);
}
*{box-sizing:border-box;margin:0;padding:0}
html{background:var(--bone);color:var(--ink);-webkit-text-size-adjust:100%}
html.lenis,html.lenis body{height:auto}
.lenis.lenis-smooth{scroll-behavior:auto!important}
body{font-family:var(--sans);font-weight:400;background:transparent;overflow-x:hidden;-webkit-font-smoothing:antialiased;text-rendering:optimizeLegibility}
body.locked{overflow:hidden}
a{color:inherit;text-decoration:none}
button{font:inherit;color:inherit;background:none;border:0;cursor:pointer}
img,video,canvas{display:block}
::selection{background:var(--orange);color:#fff}
.mono{font-family:var(--mono);font-size:11.5px;letter-spacing:.02em;text-transform:uppercase;font-weight:500}
```

## The whole stylesheet
Quote it as is. Layering: the ribbon canvas is fixed at z 1 UNDER `main` (z 2), so the ribbons pass behind the copy; the ribbon's
rider card is fixed at z 3 above it; the peek card z 30, the gauge 40, the menu 49, the chrome 50, the player 80, the loader 100.
Line reveals are `.ln` masks whose inner span sits at `translateY(105%)` until an ancestor gets `.in` (1.1 s on the ease, lines
80 ms apart); `.fade` rises 24 px. The finale's grain is an SVG turbulence tile at .07 stepped through four offsets by a CSS
keyframe. `.nogl` (no WebGL, or three.js failed) hides the canvases and puts the finale still behind the end title; `.boot-fail`
(the watchdog fired) shows every reveal. The finale still loads as a CSS background from its hosted URL.

```css
/* ---------- loader ---------- */
#loader{position:fixed;inset:0;z-index:100;background:var(--ink);color:var(--bone);overflow:hidden}
#loader .stack{position:absolute;left:50%;top:44%;width:96px;height:96px;transform:translate(-50%,-50%)}
#loader .blk{position:absolute;width:44px;height:44px;border-radius:12px;background:var(--bone);opacity:0;transform:translateY(-60vh)}
#loader .blk:nth-child(1){left:0;top:52px}
#loader .blk:nth-child(2){left:52px;top:52px}
#loader .blk:nth-child(3){left:0;top:0}
#loader .blk:nth-child(4){left:52px;top:0;background:var(--orange)}
#loader .lcount{position:absolute;right:calc(var(--g) - .06em);bottom:28px;font-size:clamp(88px,13vw,190px);font-weight:500;letter-spacing:-.05em;line-height:1;display:flex;overflow:hidden;height:1em}
#loader .lcount .dg{display:block;height:1em;overflow:hidden;width:.6em;text-align:center}
#loader .lcount .dg i{display:block;font-style:normal;transition:transform .32s var(--ease)}
#loader .lnote{position:absolute;left:var(--g);bottom:44px;color:#8A867E}
#loader .lcount .dg i{line-height:1}
#loader .lnote b{color:var(--bone);font-weight:500}
#loader .lwipe{position:absolute;inset:0;background:var(--orange);transform:scaleY(0);transform-origin:50% 100%}

/* ---------- chrome ---------- */
.chrome{position:fixed;left:0;right:0;top:0;z-index:50;height:120px;padding:44px var(--g) 0;display:flex;align-items:flex-start;justify-content:space-between;pointer-events:none;transition:color .4s,transform .7s var(--ease)}
.chrome.hid{transform:translateY(-130%)}
.chrome>*{pointer-events:auto}
.wm{display:flex;align-items:center;gap:12px;font-weight:600;font-size:30px;letter-spacing:-.045em;line-height:44px}
.glyph{display:grid;grid-template-columns:repeat(2,10px);gap:3px}
.glyph i{width:10px;height:10px;border-radius:3px;background:currentColor}
.glyph i:nth-child(2){background:var(--orange)}
.ticker{position:absolute;left:50%;top:44px;transform:translateX(-50%);height:44px;display:flex;align-items:center;gap:10px;pointer-events:none}
.ticker .tw{height:16px;overflow:hidden;position:relative;width:300px}
.ticker .tw span{position:absolute;left:0;top:0;white-space:nowrap;transition:transform .8s var(--ease),opacity .8s}
.ticker .sq{width:7px;height:7px;border-radius:2px;background:var(--orange);flex:none}
.cta{display:flex;align-items:center;gap:10px}
.talk{height:44px;padding:0 20px 0 18px;border-radius:44px;background:var(--ink);color:var(--paper);display:flex;align-items:center;gap:12px;font-size:14px;font-weight:500;letter-spacing:-.005em;transition:transform .5s var(--ease)}
.talk .dot{width:8px;height:8px;border-radius:50%;background:var(--orange);box-shadow:0 0 0 0 rgba(255,90,31,.6);animation:pulse 2.2s infinite}
@keyframes pulse{0%{box-shadow:0 0 0 0 rgba(255,90,31,.55)}70%{box-shadow:0 0 0 9px rgba(255,90,31,0)}100%{box-shadow:0 0 0 0 rgba(255,90,31,0)}}
.talk .ar{display:inline-block;transition:transform .5s var(--ease)}
.talk:hover .ar{transform:translate(2px,-2px)}
.mbtn{width:44px;height:44px;border-radius:50%;background:var(--paper);display:grid;place-items:center;transition:background .3s, transform .6s var(--ease)}
.mbtn .g4{display:grid;grid-template-columns:repeat(2,6px);gap:4px;transition:transform .6s var(--ease)}
.mbtn .g4 i{width:6px;height:6px;border-radius:2px;background:var(--ink);transition:transform .5s var(--ease),border-radius .5s}
.mbtn:hover .g4 i:nth-child(1){transform:translate(-1px,-1px)}
.mbtn:hover .g4 i:nth-child(4){transform:translate(1px,1px)}
body.menu-open .mbtn .g4{transform:rotate(45deg)}
body.menu-open .mbtn .g4 i{border-radius:50%}
.chrome.dark{color:var(--paper)}
.chrome.dark .talk{background:var(--paper);color:var(--ink)}

/* menu */
#menu{position:fixed;z-index:49;top:100px;right:var(--g);width:min(440px,calc(100vw - 2*var(--g)));background:var(--paper);border-radius:22px;padding:10px;box-shadow:0 30px 80px -30px rgba(18,18,18,.35);transform-origin:100% 0;transform:scale(.92) translateY(-8px);opacity:0;visibility:hidden;transition:transform .55s var(--ease),opacity .35s,visibility 0s .55s}
body.menu-open #menu{transform:none;opacity:1;visibility:visible;transition:transform .55s var(--ease),opacity .25s,visibility 0s}
#menu .tiles{display:grid;grid-template-columns:1fr 1fr;gap:8px}
#menu .tile{position:relative;height:128px;border-radius:14px;background:var(--bone);padding:14px 16px;display:flex;flex-direction:column;justify-content:space-between;overflow:hidden;transition:background .35s}
#menu .tile b{font-weight:500;font-size:34px;letter-spacing:-.04em;line-height:1}
#menu .tile .mono{color:var(--mute)}
#menu .tile:hover{background:var(--ink);color:var(--paper)}
#menu .tile:hover .mono{color:var(--orange)}
#menu .tile.on::after{content:"";position:absolute;right:16px;top:16px;width:8px;height:8px;border-radius:2px;background:var(--orange)}
#menu .nl{margin-top:8px;border-radius:14px;background:var(--bone);padding:16px;display:flex;gap:10px;align-items:center;justify-content:space-between}
#menu .nl p{font-size:15px;line-height:1.25;letter-spacing:-.01em}
#menu .nl form{display:flex;align-items:center;background:var(--paper);border-radius:40px;height:40px;padding:0 4px 0 14px;flex:1;max-width:220px}
#menu .nl input{border:0;background:none;outline:0;font:inherit;font-size:13px;width:100%}
#menu .nl button{width:32px;height:32px;border-radius:50%;background:var(--ink);color:var(--paper);flex:none}
#menu .mrow{margin-top:8px;display:flex;justify-content:space-between;align-items:center;border-radius:14px;background:var(--ink);color:var(--paper);padding:14px 16px}

/* gauge */
.gauge{position:fixed;right:22px;bottom:28px;z-index:40;display:flex;align-items:flex-end;gap:10px;color:var(--ink);transition:color .4s;pointer-events:none}
.gauge .trk{width:2px;height:64px;background:rgba(18,18,18,.14);border-radius:2px;position:relative;overflow:hidden}
.gauge .trk i{position:absolute;left:0;top:0;width:2px;height:100%;background:currentColor;transform-origin:50% 0;transform:scaleY(0)}
.gauge.dark{color:var(--paper)}
.gauge.dark .trk{background:rgba(255,255,255,.18)}

main{position:relative;z-index:2}
#ribbon{position:fixed;inset:0;width:100vw;height:100vh;z-index:1;pointer-events:none}

/* ---------- hero ---------- */
.hero{position:relative;height:100vh;min-height:640px;padding:120px var(--g) 0}
.win{position:relative;height:calc(100% - 72px);border-radius:var(--r);background:var(--win);overflow:hidden;transform-origin:50% 40%}
.win canvas{position:absolute;inset:0;width:100%;height:100%;touch-action:pan-y}
.win .still{position:absolute;inset:0;width:100%;height:100%;object-fit:cover}
.win.live .still{opacity:0;transition:opacity .6s}
.win .hint{position:absolute;right:22px;bottom:20px;display:flex;gap:8px;pointer-events:none}
.win .hint span{height:30px;padding:0 12px;border-radius:30px;display:flex;align-items:center;background:rgba(247,245,240,.1);color:rgba(247,245,240,.82);backdrop-filter:blur(10px);-webkit-backdrop-filter:blur(10px)}
.win .hint span b{width:6px;height:6px;border-radius:2px;background:var(--orange);margin-right:8px}
.win .corner{position:absolute;left:22px;top:20px;color:rgba(247,245,240,.6);pointer-events:none}
.tab{position:absolute;left:var(--g);bottom:72px;padding:26px 30px 0 0;pointer-events:none;z-index:2}
.tab h1{font-weight:500;font-size:clamp(34px,4.1vw,60px);line-height:.98;letter-spacing:-.045em}
.tab h1 em{font-style:normal;color:var(--orange)}
.hrow{position:absolute;left:var(--g);right:var(--g);bottom:0;height:72px;display:grid;grid-template-columns:repeat(4,1fr);align-items:center}
.hrow>div{display:flex;align-items:center;gap:10px}
.hrow>div:nth-child(2){justify-content:center}
.hrow>div:nth-child(3){justify-content:center}
.hrow>div:last-child{justify-content:flex-end}
.hrow .bk{width:7px;height:7px;border-radius:2px;background:var(--ink)}
.hrow .bk.o{background:var(--orange)}
.hrow .scroll{display:flex;gap:6px;align-items:center}
.hrow .scroll i{display:block;width:10px;height:14px;position:relative;overflow:hidden}
.hrow .scroll i::before{content:"↓";position:absolute;left:0;top:0;font-style:normal;animation:dn 1.6s var(--ease) infinite}
@keyframes dn{0%{transform:translateY(-100%)}50%{transform:none}100%{transform:translateY(100%)}}

/* ---------- reveal lines ---------- */
.ln{display:block;overflow:hidden;padding-bottom:.08em;margin-bottom:-.08em}
.ln>span{display:inline-block;transform:translateY(105%);transition:transform 1.1s var(--ease)}
.in .ln>span{transform:none}
.in .ln:nth-child(2)>span{transition-delay:.08s}
.in .ln:nth-child(3)>span{transition-delay:.16s}
.fade{opacity:0;transform:translateY(24px);transition:opacity 1s var(--ease),transform 1.1s var(--ease)}
.in .fade,.fade.in{opacity:1;transform:none}

/* ---------- statement ---------- */
.stmt{position:relative;padding:24vh var(--g) 22vh}
.big{font-weight:400;font-size:clamp(52px,10.4vw,152px);line-height:.98;letter-spacing:-.05em}
.stmt .big .ln:nth-child(2){padding-left:20vw}
.cols{display:grid;grid-template-columns:49fr 51fr;margin-top:clamp(48px,9vh,110px)}
.cols .txt{max-width:620px}
.lead{font-size:clamp(18px,1.46vw,21px);line-height:1.43;letter-spacing:-.012em;color:var(--ink)}
.lead+.lead{margin-top:1em}
.pill{display:inline-flex;align-items:center;gap:12px;height:48px;padding:0 24px 0 22px;border-radius:48px;background:var(--paper);font-size:14px;font-weight:500;margin-top:40px;transition:background .35s,color .35s;box-shadow:0 1px 0 rgba(18,18,18,.04)}
.pill i{width:7px;height:7px;border-radius:2px;background:var(--ink);transition:transform .5s var(--ease),background .3s}
.pill:hover{background:var(--ink);color:var(--paper)}
.pill:hover i{background:var(--orange);transform:rotate(45deg)}
.rider{position:fixed;left:0;top:0;z-index:3;width:clamp(240px,25vw,360px);aspect-ratio:36/25;border-radius:16px;overflow:hidden;pointer-events:none;opacity:0;will-change:transform;box-shadow:0 30px 60px -30px rgba(18,18,18,.45);background:#ddd}
.rider img{width:100%;height:100%;object-fit:cover}
.rider .rl{position:absolute;left:12px;bottom:10px;color:#fff;text-shadow:0 1px 8px rgba(0,0,0,.4)}
.stmt-spacer{height:clamp(160px,22vw,320px)}

/* ---------- reel ---------- */
.reel{position:relative;height:280vh}
.reel .stick{position:sticky;top:0;height:100vh;overflow:hidden}
.reel .card{position:absolute;left:50%;top:50%;border-radius:var(--r);overflow:hidden;background:#222;will-change:width,height,transform;cursor:none}
.reel .card video,.reel .card img{position:absolute;inset:0;width:100%;height:100%;object-fit:cover}
.reel .card::after{content:"";position:absolute;inset:0;background:linear-gradient(180deg,rgba(0,0,0,.12),rgba(0,0,0,0) 30%,rgba(0,0,0,0) 70%,rgba(0,0,0,.22))}
.reel .words{position:absolute;inset:0;pointer-events:none;z-index:2}
.reel .words.w{color:#fff;z-index:3}
.reel .wd{position:absolute;top:50%;font-weight:400;font-size:clamp(64px,12.4vw,180px);letter-spacing:-.055em;line-height:1;transform:translateY(-52%);white-space:nowrap}
.reel .playb{position:absolute;left:0;top:0;z-index:4;width:112px;height:112px;margin:-56px 0 0 -56px;border-radius:50%;background:var(--orange);color:#fff;display:grid;place-items:center;pointer-events:none;transform:scale(0);transition:transform .45s var(--ease)}
.reel .playb span{display:flex;flex-direction:column;align-items:center;gap:4px}
.reel .playb svg{width:18px;height:18px}
.reel .playb.on{transform:scale(1)}
.reel .meta{position:absolute;left:var(--g);right:var(--g);bottom:26px;display:flex;justify-content:space-between;z-index:4;pointer-events:none}
.reel .tmark{position:absolute;z-index:3;width:11px;height:11px;pointer-events:none}
.reel .tmark::before,.reel .tmark::after{content:"";position:absolute;background:var(--ink)}
.reel .tmark::before{left:5px;top:0;width:1px;height:11px}
.reel .tmark::after{left:0;top:5px;width:11px;height:1px}

/* ---------- work ---------- */
.work{position:relative;padding:18vh var(--g) 14vh}
.whead{display:flex;align-items:flex-end;justify-content:space-between;gap:24px;margin-bottom:72px}
.whead h2{font-weight:400;font-size:clamp(46px,5.6vw,82px);letter-spacing:-.05em;line-height:.95}
.whead h2 sup{font-family:var(--mono);font-size:13px;letter-spacing:0;vertical-align:top;position:relative;top:.5em;margin-left:8px;color:var(--orange)}
.whead .r{display:flex;flex-direction:column;align-items:flex-end;gap:18px}
.whead .blurb{max-width:300px;text-align:right;color:var(--ink-2);line-height:1.5}
.tog{display:flex;background:var(--paper);border-radius:44px;padding:4px;position:relative}
.tog button{position:relative;z-index:1;height:36px;padding:0 18px;border-radius:36px;font-size:13px;font-weight:500;transition:color .4s}
.tog button.on{color:var(--paper)}
.tog .kn{position:absolute;top:4px;left:4px;height:36px;border-radius:36px;background:var(--ink);transition:transform .55s var(--ease),width .55s var(--ease)}
.grid{display:grid;grid-template-columns:repeat(12,1fr);column-gap:30px;row-gap:84px;align-items:start}
.grid .pc{grid-column:span 7}
.grid .pc:nth-child(4n+2),.grid .pc:nth-child(4n+3){grid-column:span 5;margin-top:96px}
.grid .pc:nth-child(4n+2) .im,.grid .pc:nth-child(4n+3) .im{aspect-ratio:5/5.6}
.pc{display:block;position:relative}
.pc .im{position:relative;border-radius:var(--r);overflow:hidden;aspect-ratio:4/3;background:var(--bone-2);transform:translateZ(0)}
.pc.wide .im{aspect-ratio:16/11}
.pc .im img{width:100%;height:100%;object-fit:cover;transform:scale(1.08);transition:transform 1.2s var(--ease)}
.pc:hover .im img{transform:scale(1.03)}
.pc .chip{position:absolute;right:16px;top:16px;width:52px;height:52px;border-radius:50%;background:var(--orange);color:#fff;display:grid;place-items:center;font-size:20px;transform:scale(0) rotate(-45deg);transition:transform .55s var(--ease)}
.pc:hover .chip{transform:none}
.pc .idx{position:absolute;left:16px;top:16px;height:28px;padding:0 10px;border-radius:28px;display:flex;align-items:center;background:rgba(247,245,240,.88);backdrop-filter:blur(8px);-webkit-backdrop-filter:blur(8px)}
.pc .tags{margin-top:20px;color:var(--ink-2);display:flex;justify-content:space-between}
.pc h3{margin-top:6px;font-weight:400;font-size:clamp(28px,2.9vw,42px);letter-spacing:-.045em;line-height:1.05;display:flex;align-items:center;gap:0;transition:gap .5s var(--ease)}
.pc h3 .ar{display:inline-block;width:0;overflow:hidden;color:var(--orange);transition:width .5s var(--ease)}
.pc:hover h3 .ar{width:.9em}
.pc .im{clip-path:inset(12% 0 0 0 round var(--r));transition:clip-path 1.3s var(--ease)}
.pc.in .im{clip-path:inset(0 0 0 0 round var(--r))}
.index{display:none;border-top:1px solid rgba(18,18,18,.14)}
.work.list .grid{display:none}
.work.list .index{display:block}
.irow{display:grid;grid-template-columns:80px 1.4fr 1fr 80px;align-items:center;height:96px;border-bottom:1px solid rgba(18,18,18,.14);position:relative;transition:color .3s}
.irow b{font-weight:400;font-size:clamp(26px,2.8vw,40px);letter-spacing:-.045em;transition:transform .6s var(--ease)}
.irow .mono:last-child{text-align:right}
.irow::before{content:"";position:absolute;left:0;right:0;top:0;bottom:-1px;background:var(--ink);transform:scaleY(0);transform-origin:50% 100%;transition:transform .5s var(--ease);z-index:-1}
.irow:hover{color:var(--paper)}
.irow:hover::before{transform:none}
.irow:hover b{transform:translateX(14px)}
.index{position:relative;z-index:0}
.peek{position:fixed;left:0;top:0;width:300px;aspect-ratio:4/3;border-radius:16px;overflow:hidden;pointer-events:none;z-index:30;opacity:0;transform:scale(.7);transition:opacity .3s,transform .5s var(--ease)}
.peek.on{opacity:1;transform:scale(1)}
.peek img{position:absolute;inset:0;width:100%;height:100%;object-fit:cover}
.wfoot{display:flex;justify-content:center;margin-top:96px}

/* ---------- statement 2 ---------- */
.stmt2{position:relative;padding:20vh var(--g) 22vh}
.stmt2 .big{font-size:clamp(46px,8.3vw,120px)}
.stmt2 .cols{grid-template-columns:49fr 51fr;align-items:start}
.minicard{position:relative;width:min(100%,520px);aspect-ratio:4/3;border-radius:var(--r);overflow:hidden;transform:rotate(-4deg);margin-top:40px;box-shadow:0 40px 80px -40px rgba(18,18,18,.5)}
.minicard img{width:100%;height:100%;object-fit:cover}
.minicard .mono{position:absolute;left:14px;bottom:12px;color:#fff}

/* ---------- finale ---------- */
.fin{position:relative;height:480vh;background:#0E0E10;color:var(--paper)}
.fin .stick{position:sticky;top:0;height:100vh;overflow:hidden}
.fin canvas{position:absolute;inset:0;width:100%;height:100%}
.fin .kin{position:absolute;inset:0;display:grid;place-items:center;pointer-events:none}
.fin .kin .blk{text-align:center;font-weight:500;font-size:clamp(22px,2.6vw,38px);letter-spacing:-.02em;line-height:1.12;text-transform:uppercase}
.fin .kin .kw{display:inline-block;will-change:transform;white-space:pre}
.fin .cap{position:absolute;left:var(--g);bottom:36px;display:flex;gap:24px;color:rgba(247,245,240,.62)}
.fin .cap b{color:var(--orange);font-weight:500}
.fin .end{position:absolute;left:var(--g);right:var(--g);bottom:96px;display:flex;justify-content:space-between;align-items:flex-end;pointer-events:none;opacity:0}
.fin .end h3{font-weight:400;font-size:clamp(40px,5.4vw,80px);letter-spacing:-.05em;line-height:.98}
.fin .end h3 em{font-style:normal;color:var(--orange)}
.fin .flood{position:absolute;inset:0;background:var(--orange);clip-path:circle(0% at 50% 46%);pointer-events:none;z-index:5}
.fin .vig{position:absolute;inset:0;pointer-events:none;background:radial-gradient(120% 90% at 50% 45%,transparent 55%,rgba(0,0,0,.55))}
.fin .grain{position:absolute;inset:-50%;pointer-events:none;opacity:.07;background-image:url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='160' height='160'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='.9' numOctaves='2' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)'/%3E%3C/svg%3E");animation:gr 1s steps(4) infinite}
@keyframes gr{0%{transform:translate(0,0)}25%{transform:translate(-8%,4%)}50%{transform:translate(5%,-6%)}75%{transform:translate(-3%,7%)}100%{transform:translate(0,0)}}

/* ---------- footer ---------- */
.foot{position:relative;z-index:3;background:var(--orange);padding-top:0;margin-top:-60vh}
.fpanel{position:relative;background:var(--orange);color:var(--ink);padding:120px var(--g) 36px;overflow:hidden}
.fpanel .ask{display:flex;align-items:center;gap:12px}
.fpanel .ask i{width:8px;height:8px;border-radius:2px;background:var(--ink)}
.lets{display:block;margin-top:28px;font-weight:500;font-size:clamp(64px,14.8vw,214px);letter-spacing:-.065em;line-height:.9;white-space:nowrap}
.lets .ch{display:inline-block;overflow:hidden;vertical-align:top;height:.98em}
.lets .ch>span{display:block;transition:transform .7s var(--ease)}
.lets .ch>span::after{content:attr(data-c);display:block}
.lets:hover .ch>span{transform:translateY(-50%)}
.lets .ch.sp{width:.24em}
.fgrid{display:grid;grid-template-columns:1.2fr 1fr 1fr 1.4fr;gap:30px;margin-top:110px;padding-top:28px;border-top:1px solid rgba(18,18,18,.25)}
.fgrid h4{font-family:var(--mono);font-weight:500;font-size:11.5px;letter-spacing:.02em;text-transform:uppercase;margin-bottom:14px;opacity:.7}
.fgrid p,.fgrid a{display:block;font-size:17px;line-height:1.45;letter-spacing:-.01em}
.fgrid a{width:max-content;background:linear-gradient(currentColor,currentColor) 0 100%/0 1px no-repeat;transition:background-size .5s var(--ease)}
.fgrid a:hover{background-size:100% 1px}
.fgrid form{display:flex;align-items:center;height:52px;border-radius:52px;background:var(--ink);padding:0 6px 0 20px;margin-top:6px}
.fgrid input{flex:1;border:0;background:none;outline:0;color:var(--paper);font:inherit;font-size:14px;min-width:0}
.fgrid input::placeholder{color:#8a867e}
.fgrid form button{width:40px;height:40px;border-radius:50%;background:var(--orange);color:var(--ink);font-size:18px}
.fbase{display:flex;justify-content:space-between;margin-top:96px;gap:16px;flex-wrap:wrap}
.fbase .glyph i{background:var(--ink)}
.fbase .glyph i:nth-child(2){background:var(--paper)}

/* ---------- player ---------- */
#player{position:fixed;inset:0;z-index:80;background:rgba(14,14,16,.96);display:grid;place-items:center;opacity:0;visibility:hidden;transition:opacity .4s,visibility 0s .4s}
#player.on{opacity:1;visibility:visible;transition:opacity .4s,visibility 0s}
#player video{width:min(92vw,160vh);aspect-ratio:16/9;border-radius:16px;background:#000}
#player .x{position:absolute;right:var(--g);top:44px;height:44px;padding:0 20px;border-radius:44px;background:var(--paper);color:var(--ink);font-size:14px;font-weight:500}

/* ---------- no-webgl ---------- */
.nogl .win canvas,.nogl .fin canvas{display:none}
.nogl .fin .stick{background:#0E0E10 url(https://www.vividsites.app/media/flagship/blockhaus/finale-still.jpg) center/cover no-repeat}
.nogl .fin .end{opacity:1}
.nogl .win .hint{display:none}
.boot-fail .ln>span,.boot-fail .fade{transform:none;opacity:1}
.boot-fail .pc .im{clip-path:none}

/* ---------- responsive ---------- */
@media (max-width:1024px){
  .ticker{display:none}
  .grid{row-gap:80px}
  .grid .pc:nth-child(4n+2),.grid .pc:nth-child(4n+3){margin-top:90px}
}
@media (max-width:900px){
  .cols,.stmt2 .cols{grid-template-columns:1fr}
  .cols .txt{margin-top:0}
  .stmt-spacer{height:300px}
  .fgrid{grid-template-columns:1fr 1fr}
}
@media (max-width:760px){
  :root{--r:14px}
  .chrome{padding-top:20px;height:84px}
  .wm{font-size:24px}
  .talk{display:none}
  #menu{top:74px}
  .hero{padding-top:84px;min-height:560px;height:100svh}
  .win{height:calc(100% - 64px)}
  .tab{bottom:64px;padding:18px 18px 0 0}
  .tab h1{font-size:30px}
  .hrow{height:64px;grid-template-columns:1fr}
  .hrow>div:nth-child(2),.hrow>div:nth-child(3),.hrow>div:nth-child(4){display:none}
  .win .hint{display:none}
  .stmt{padding-top:16vh}
  .stmt .big .ln:nth-child(2){padding-left:0}
  .reel{height:220vh}
  .grid{grid-template-columns:1fr;row-gap:56px}
  .grid .pc:nth-child(n){grid-column:1/-1;margin-top:0}
  .grid .pc:nth-child(n) .im{aspect-ratio:4/3.4}
  .whead{flex-direction:column;align-items:flex-start;margin-bottom:44px}
  .whead .r{align-items:flex-start}
  .whead .blurb{text-align:left}
  .irow{grid-template-columns:44px 1fr 56px;height:76px}
  .irow .disc{display:none}
  .fin{height:400vh}
  .fin .end{flex-direction:column;align-items:flex-start;gap:12px;bottom:110px}
  .fin .cap{flex-direction:column;gap:6px}
  .fgrid{grid-template-columns:1fr;gap:28px;margin-top:72px}
  .fpanel{padding-top:80px}
  .gauge{right:12px;bottom:16px}
  .gauge .trk{height:44px}
  .minicard{transform:rotate(-3deg)}
  .reel .meta span:last-child{display:none}
}
@media (prefers-reduced-motion:reduce){
  .ln>span,.fade{transition:none!important;transform:none!important;opacity:1!important}
}
```

## Markup
`#grid` and `#index` are filled from the `WORK` data; `#kin` gets the finale's words; `#tick`, `#yr` and `#yr2` are rewritten from
today's date; `.lets` is split into rolling letters; the reel `<video>` gets its `src` from the script. The hero `<h1>` starts with
`in` so it reads behind the loader, and the entrance replays it. Copy every string exactly.

```html
<body class="locked">

<div id="loader" aria-hidden="true">
  <div class="stack"><i class="blk"></i><i class="blk"></i><i class="blk"></i><i class="blk"></i></div>
  <div class="lnote mono">Blockhaus <b>/</b> stacking the toybox</div>
  <div class="lcount"><span class="dg"><i>0</i></span><span class="dg"><i>0</i></span><span class="dg"><i>0</i></span></div>
  <div class="lwipe"></div>
</div>

<header class="chrome" id="chrome">
  <a href="#top" class="wm" aria-label="Blockhaus home"><span class="glyph"><i></i><i></i><i></i><i></i></span>blockhaus</a>
  <div class="ticker mono"><span class="sq"></span><span class="tw" id="tick"><span>Now booking Q1 ’27 · 3 seats left</span></span></div>
  <div class="cta">
    <a href="#contact" class="talk"><span class="dot"></span>Start a project <span class="ar">↗</span></a>
    <button class="mbtn" id="mbtn" aria-label="Menu" aria-expanded="false"><span class="g4"><i></i><i></i><i></i><i></i></span></button>
  </div>
</header>

<nav id="menu" aria-label="Main">
  <div class="tiles">
    <a class="tile on" href="#top"><span class="mono">01 / Home</span><b>Toybox</b></a>
    <a class="tile" href="#work"><span class="mono">02 / Work</span><b>Play</b></a>
    <a class="tile" href="#studio"><span class="mono">03 / Studio</span><b>People</b></a>
    <a class="tile" href="#contact"><span class="mono">04 / Contact</span><b>Say hi</b></a>
  </div>
  <div class="nl"><p>The Toybox<br><span class="mono" style="color:var(--mute)">one letter a season</span></p>
    <form onsubmit="return false"><input type="email" placeholder="you@example.com" aria-label="Email"><button aria-label="Subscribe">→</button></form></div>
  <a class="mrow" href="#lab"><span class="mono">Blockhaus Lab: experiments</span><span>↗</span></a>
</nav>

<canvas id="ribbon" aria-hidden="true"></canvas>
<div class="rider" id="rider"><img src="https://www.vividsites.app/media/flagship/blockhaus/work/p2-s.jpg" alt=""><span class="rl mono">Now playing: Shoal Atlas</span></div>
<div class="peek" id="peek"><img alt=""></div>

<div class="gauge mono" id="gauge"><span id="gnum">000</span><span class="trk"><i id="gbar"></i></span></div>

<main id="top">
  <section class="hero" id="hero">
    <div class="win" id="win">
      <img class="still" src="https://www.vividsites.app/media/flagship/blockhaus/hero-still.jpg" alt="A pile of glossy toy blocks, rings and capsules in orange, bone and graphite">
      <canvas id="heroCanvas"></canvas>
      <div class="corner mono">Fig. 00: the toybox</div>
      <div class="hint mono"><span><b></b>push</span><span>click to scatter</span><span>press to shove</span></div>
    </div>
    <div class="tab"><h1 class="in"><span class="ln"><span>Play-grade 3D</span></span><span class="ln"><span>for <em>curious</em> brands.</span></span></h1></div>
    <div class="hrow mono">
      <div><span class="bk o"></span>Studio: Lisbon / Hong Kong</div>
      <div><span class="bk"></span>Est. 2017</div>
      <div><span class="bk"></span>Web · 3D · Motion · Physics</div>
      <div class="scroll">Scroll <i></i></div>
    </div>
  </section>

  <section class="stmt" id="studio">
    <h2 class="big rv"><span class="ln"><span>Serious craft,</span></span><span class="ln"><span>built for play.</span></span></h2>
    <div class="cols">
      <div class="stmt-spacer"></div>
      <div class="txt rv">
        <p class="lead fade">Blockhaus is a small studio of designers, 3D artists and creative engineers. We make websites, launches and installations you can push, pull and poke, then fuss over the physics until it feels like a toy you already own.</p>
        <a href="#work" class="pill fade"><i></i>How we play</a>
      </div>
    </div>
  </section>

  <section class="reel" id="reel">
    <div class="stick">
      <div class="words k" id="wk"><span class="wd" data-w="l">Show</span><span class="wd" data-w="r">reel</span></div>
      <div class="card" id="rcard">
        <video id="rvid" muted loop playsinline preload="metadata" poster="https://www.vividsites.app/media/flagship/blockhaus/reel-poster.jpg"></video>
      </div>
      <div class="words w" id="ww"><span class="wd" data-w="l">Show</span><span class="wd" data-w="r">reel</span></div>
      <div class="playb mono" id="playb"><span><svg viewBox="0 0 24 24" fill="currentColor"><path d="M7 4.5v15l13-7.5z"/></svg>Play</span></div>
      <i class="tmark" data-m="0"></i><i class="tmark" data-m="1"></i><i class="tmark" data-m="2"></i><i class="tmark" data-m="3"></i>
      <div class="meta mono" id="rmeta"><span>Reel ’26: 00:26</span><span>Six worlds, half a minute</span></div>
    </div>
  </section>

  <section class="work" id="work">
    <div class="whead">
      <h2 class="rv"><span class="ln"><span>Selected play<sup>(08)</sup></span></span></h2>
      <div class="r">
        <p class="blurb mono fade">Eight recent launches, worlds and toys, for brands that would rather be touched than scrolled past.</p>
        <div class="tog" id="tog"><span class="kn" id="kn"></span><button class="on" data-v="grid">Grid</button><button data-v="list">Index</button></div>
      </div>
    </div>
    <div class="grid" id="grid"></div>
    <div class="index" id="index"></div>
    <div class="wfoot"><a href="#work" class="pill"><i></i>Every project, 2017–<span id="yr2">2026</span></a></div>
  </section>

  <section class="stmt2" id="lab">
    <h2 class="big rv"><span class="ln"><span>Things worth</span></span><span class="ln"><span>touching, made to</span></span><span class="ln"><span>outlast a scroll.</span></span></h2>
    <div class="cols">
      <div><div class="minicard fade"><img src="https://www.vividsites.app/media/flagship/blockhaus/work/p5-s.jpg" alt="A candy-coloured sneaker exploding into soft parts"><span class="mono">Lab note 14: soft-body laces</span></div></div>
      <div class="txt rv" style="padding-top:60px">
        <p class="lead fade">We don't chase trends or ship the same site twice. We pick one strange, tactile idea and sweat every frame of it: the weight of a click, the wobble of a ring, the half-second before a block lands.</p>
        <p class="lead fade">Strategy, art direction, 3D, sound and engineering sit at one table, so the idea never gets lost in a hand-off. Small team, short lines, long tails.</p>
        <a href="#contact" class="pill fade"><i></i>Inside the studio</a>
      </div>
    </div>
  </section>

  <section class="fin" id="fin">
    <div class="stick">
      <canvas id="finCanvas"></canvas>
      <div class="vig"></div>
      <div class="kin"><div class="blk" id="kin"></div></div>
      <div class="end" id="fend"><h3>Fifty-eight blocks.<br>Zero <em>glue.</em></h3><p class="mono" style="max-width:280px;line-height:1.6;color:rgba(247,245,240,.7)">Every piece you just watched land was drawn in your browser, live, as you scrolled.</p></div>
      <div class="cap mono"><span><b>■</b> Fig. 01: the haus</span><span id="fcount">00 / 58 blocks placed</span></div>
      <div class="grain"></div>
      <div class="flood" id="flood"></div>
    </div>
  </section>

  <footer class="foot" id="contact">
    <div class="fpanel">
      <div class="ask mono"><i></i>Got something that should be touched?</div>
      <a href="#contact" class="lets" id="lets" aria-label="Let's build it!">Let's build it!</a>
      <div class="fgrid">
        <div><h4>Studio</h4><p>Unit 4, Cobble Yard<br>18 Rua do Forno Velho<br>Lisbon, Portugal</p></div>
        <div><h4>Say hi</h4><a href="#contact">hello@blockhaus.play</a><a href="#contact">jobs@blockhaus.play</a></div>
        <div><h4>Follow</h4><a href="#contact">Journal</a><a href="#contact">Moodboards</a><a href="#contact">Showreel</a><a href="#contact">Community</a></div>
        <div><h4>The Toybox, one letter a season</h4><form onsubmit="return false"><input type="email" placeholder="Your email" aria-label="Email"><button aria-label="Subscribe">→</button></form></div>
      </div>
      <div class="fbase mono"><span class="wm" style="font-size:13px;line-height:1;gap:10px;letter-spacing:.02em"><span class="glyph"><i></i><i></i><i></i><i></i></span>© <span id="yr">2026</span> Blockhaus Play Studio</span><span>Made with too many blocks</span><a href="#top">Back to the toybox ↑</a></div>
    </div>
  </footer>
</main>

<div id="player" role="dialog" aria-label="Reel player"><button class="x" id="px">Close ×</button><video id="pvid" controls playsinline></video></div>
```

## Script prelude
One module. The three.js bindings are declared empty and filled by the boot's dynamic import, so a failed download only costs the
3D. `PHONE` is the phone tier (≤ 760 px, or a coarse pointer under 900 px). `C` is the 3D palette (the 3D bone `#E8E3D9` and
graphite `#5E5E63` are the CSS bone and mute shifted for the lights). `canGL()` probes a context once.

```js
<script type="module">
/* three.js is imported dynamically in the boot section, after the page's own UI is wired,
   so a failed download only costs the 3D, never the menu, the work grid or the loader */
let THREE, RoundedBoxGeometry, RoomEnvironment, EffectComposer, RenderPass, OutputPass, UnrealBloomPass, GTAOPass;

const $ = (s, r = document) => r.querySelector(s);
const $$ = (s, r = document) => [...r.querySelectorAll(s)];
const clamp = (v, a = 0, b = 1) => Math.min(b, Math.max(a, v));
const lerp = (a, b, t) => a + (b - a) * t;
const smooth = (a, b, v) => { const t = clamp((v - a) / (b - a)); return t * t * (3 - 2 * t); };
const eo = t => 1 - Math.pow(1 - t, 3);
const PHONE = matchMedia('(max-width:760px)').matches || matchMedia('(pointer:coarse)').matches && innerWidth < 900;
const RM = matchMedia('(prefers-reduced-motion:reduce)').matches;
let VW = innerWidth, VH = innerHeight;

const C = { orange: 0xFF5A1F, bone: 0xE8E3D9, graphite: 0x5E5E63, black: 0x0C0C0D, lilac: 0xB8A6FF, lime: 0xD4FF3A };

function canGL() { try { const c = document.createElement('canvas'); return !!(c.getContext('webgl2') || c.getContext('webgl')); } catch (e) { return false; } }
const GL = canGL();
if (!GL) document.documentElement.classList.add('nogl');
```

## The toy kit — five shapes, sphere colliders, five materials
Five shared geometries (rounded cube, brick, torus, capsule, squashed pebble). For physics each shape is a few spheres in its own
frame (`COL`: `[x, y, z, radius]`); `BR` is the broad-phase radius, `MASS` the mass. The five materials share one PMREM
environment: glossy orange, satin bone, matte graphite, piano black and a sheen lilac. The hero picks a material per body from
`MAT_MIX` (3 orange, 3 bone, 2 graphite, 3 black, 1 lilac of 12) and cycles shapes through `SHAPE_MIX`.

```js
/* ======================= shared toy kit ======================= */
const S = 1.0;
let GEO = null;
function makeGeo() { GEO = {
  cube: new RoundedBoxGeometry(1.15 * S, 1.15 * S, 1.15 * S, 6, 0.3 * S),
  brick: new RoundedBoxGeometry(2.3 * S, 1.15 * S, 1.15 * S, 6, 0.3 * S),
  ring: new THREE.TorusGeometry(0.62 * S, 0.3 * S, 28, 64),
  capsule: new THREE.CapsuleGeometry(0.44 * S, 1.15 * S, 12, 28),
  pebble: (() => { const g = new THREE.SphereGeometry(0.74 * S, 48, 32); g.scale(1, 0.64, 0.88); return g; })(),
}; }
const COL = {
  cube: [[0, 0, 0, .66]],
  brick: [[-.58, 0, 0, .6], [.58, 0, 0, .6]],
  ring: Array.from({ length: 8 }, (_, i) => { const a = i / 8 * Math.PI * 2; return [Math.cos(a) * .62, Math.sin(a) * .62, 0, .33]; }),
  capsule: [[0, -.58, 0, .46], [0, 0, 0, .46], [0, .58, 0, .46]],
  pebble: [[0, 0, 0, .6]],
};
const BR = { cube: 1.0, brick: 1.35, ring: .98, capsule: 1.08, pebble: .76 };
const MASS = { cube: 1.2, brick: 1.9, ring: .9, capsule: 1.05, pebble: .85 };

function makeMats(env) {
  const m = {
    orange: new THREE.MeshPhysicalMaterial({ color: C.orange, roughness: .38, clearcoat: 1, clearcoatRoughness: .06, envMap: env, envMapIntensity: .55 }),
    bone: new THREE.MeshPhysicalMaterial({ color: C.bone, roughness: .55, clearcoat: .4, clearcoatRoughness: .25, envMap: env, envMapIntensity: .6 }),
    graphite: new THREE.MeshPhysicalMaterial({ color: C.graphite, roughness: .82, envMap: env, envMapIntensity: .5 }),
    black: new THREE.MeshPhysicalMaterial({ color: C.black, roughness: .22, clearcoat: 1, clearcoatRoughness: .04, envMap: env, envMapIntensity: 1.2 }),
    lilac: new THREE.MeshPhysicalMaterial({ color: 0x9d88ff, roughness: .6, sheen: .8, sheenColor: new THREE.Color(0xd9ceff), sheenRoughness: .45, envMap: env, envMapIntensity: .5 }),
  };
  return m;
}
const MAT_MIX = ['orange', 'orange', 'orange', 'bone', 'bone', 'bone', 'graphite', 'graphite', 'black', 'black', 'black', 'lilac'];
const SHAPE_MIX = ['cube', 'cube', 'brick', 'ring', 'ring', 'capsule', 'capsule', 'pebble'];
```

## The hero — renderer, lights and the bodies
Neutral tone mapping at exposure .92, soft PCF shadows (off on phones), DPR ≤ 1.75 (1.5 on phones), a `#16161a` background with
`#131316` fog from 8.5 to 17, the room environment through PMREM at sigma .035, a 30° camera at z 9.4. A warm key `#fff3e6` 2.4
from (−6, 9, 10) with a 2048 shadow map over ±13 × ±10, a peach rim `#ffb48a` 1.1 from behind right, a lilac-over-brown hemisphere
at .22. Bodies come from a Lehmer generator (seed 7, × 16807 mod 2³¹ − 1), so the pile is the same on every load: spread over 10 ×
6 × 3 units, randomly turned and spun, then lifted 14–24 units so they all fall in when the page opens.

```js
/* ======================= HERO: physics toybox ======================= */
const hero = { ready: false };
function initHero() {
  const canvas = $('#heroCanvas'), win = $('#win');
  const renderer = new THREE.WebGLRenderer({ canvas, antialias: true, powerPreference: 'high-performance' });
  renderer.setPixelRatio(Math.min(devicePixelRatio, PHONE ? 1.5 : 1.75));
  renderer.outputColorSpace = THREE.SRGBColorSpace;
  renderer.toneMapping = THREE.NeutralToneMapping;
  renderer.toneMappingExposure = .92;
  renderer.shadowMap.enabled = !PHONE;
  renderer.shadowMap.type = THREE.PCFSoftShadowMap;
  const scene = new THREE.Scene();
  scene.background = new THREE.Color(0x16161a);
  scene.fog = new THREE.Fog(0x131316, 8.5, 17);
  const pmrem = new THREE.PMREMGenerator(renderer);
  const env = pmrem.fromScene(new RoomEnvironment(), 0.035).texture;
  const mats = makeMats(env);
  const cam = new THREE.PerspectiveCamera(30, 2, .1, 80);
  cam.position.set(0, 0, 9.4);

  const key = new THREE.DirectionalLight(0xfff3e6, 2.4);
  key.position.set(-6, 9, 10);
  key.castShadow = true;
  key.shadow.mapSize.set(2048, 2048);
  Object.assign(key.shadow.camera, { left: -13, right: 13, top: 10, bottom: -10, near: 1, far: 40 });
  key.shadow.bias = -0.0004; key.shadow.normalBias = 0.03; key.shadow.radius = 4;
  scene.add(key);
  const rim = new THREE.DirectionalLight(0xffb48a, 1.1); rim.position.set(8, -2, -6); scene.add(rim);
  scene.add(new THREE.HemisphereLight(0xdcd6ff, 0x1a1410, .22));

  const N = PHONE ? 34 : 62;
  const bodies = [];
  let seed = 7; const rnd = () => (seed = (seed * 16807) % 2147483647, (seed - 1) / 2147483646);
  for (let i = 0; i < N; i++) {
    const shape = SHAPE_MIX[i % SHAPE_MIX.length];
    const matName = MAT_MIX[Math.floor(rnd() * MAT_MIX.length)];
    const mesh = new THREE.Mesh(GEO[shape], mats[matName]);
    mesh.castShadow = mesh.receiveShadow = !PHONE;
    const b = {
      mesh, shape, mat: matName,
      p: new THREE.Vector3((rnd() - .5) * 10, (rnd() - .5) * 6, (rnd() - .5) * 3),
      v: new THREE.Vector3(), q: new THREE.Quaternion().setFromEuler(new THREE.Euler(rnd() * 6, rnd() * 6, rnd() * 6)),
      w: new THREE.Vector3((rnd() - .5), (rnd() - .5), (rnd() - .5)),
      im: 1 / MASS[shape], br: BR[shape], cols: COL[shape], wc: COL[shape].map(() => new THREE.Vector3()),
    };
    // loader entrance: start far above, fall in
    b.p.y += 14 + rnd() * 10;
    scene.add(mesh); bodies.push(b);
  }
```

## The cursor sphere and the burst
The pointer is raycast onto the plane z = .9 in front of the pile; that point is a kinematic sphere of radius 1 (1.3 while the
button is down) whose velocity is the frame-to-frame delta, clamped to 40 units/s. Leaving the window parks it at z 50. A press
that ends within 8 px and 400 ms is a click: `burst()` gives every body an outward impulse `13 · e^(−d/3.2) / mass` from the click
point (on z 0), a random z kick and up to ±4.5 rad/s of spin on each axis, and sets `flash`. Touch pointers release the sphere on
lift.

```js
  // cursor body
  const cur = { p: new THREE.Vector3(0, 0, 50), prev: new THREE.Vector3(0, 0, 50), v: new THREE.Vector3(), r: 1.0, on: false, down: false, dn: { x: 0, y: 0, t: 0 } };
  const ray = new THREE.Raycaster(), ndc = new THREE.Vector2(), plane = new THREE.Plane(new THREE.Vector3(0, 0, 1), -.9);
  const tmpV = new THREE.Vector3();
  function setCursor(e) {
    const r = canvas.getBoundingClientRect();
    ndc.set(((e.clientX - r.left) / r.width) * 2 - 1, -((e.clientY - r.top) / r.height) * 2 + 1);
    ray.setFromCamera(ndc, cam);
    ray.ray.intersectPlane(plane, tmpV);
    if (tmpV) cur.p.copy(tmpV);
  }
  win.addEventListener('pointermove', e => { setCursor(e); if (!cur.on) { cur.prev.copy(cur.p); cur.on = true; } });
  win.addEventListener('pointerleave', () => { cur.on = false; cur.p.set(0, 0, 50); cur.prev.copy(cur.p); });
  win.addEventListener('pointerdown', e => { setCursor(e); cur.down = true; cur.dn = { x: e.clientX, y: e.clientY, t: performance.now() }; if (!cur.on) { cur.prev.copy(cur.p); cur.on = e.pointerType === 'mouse'; } });
  win.addEventListener('pointerup', e => {
    cur.down = false;
    const d = Math.hypot(e.clientX - cur.dn.x, e.clientY - cur.dn.y);
    if (d < 8 && performance.now() - cur.dn.t < 400) burst(cur.p.clone());
    if (e.pointerType !== 'mouse') { cur.on = false; cur.p.set(0, 0, 50); cur.prev.copy(cur.p); }
  });

  // spark: orange pieces flash lime on click
  let flash = 0;
  function burst(at) {
    at.z = 0;
    for (const b of bodies) {
      tmpV.subVectors(b.p, at); const d = tmpV.length() + .001;
      const f = 13 * Math.exp(-d / 3.2) * b.im;
      b.v.addScaledVector(tmpV.normalize(), f); b.v.z += (Math.random() - .2) * f * .5;
      b.w.x += (Math.random() - .5) * 9; b.w.y += (Math.random() - .5) * 9; b.w.z += (Math.random() - .5) * 9;
    }
    flash = 1;
  }
  hero.burst = burst;
```

## The solver — one step
Per body: an anisotropic spring back to the origin (`kx = .9 / max(1, aspect × .95)`, `ky` 1.6, `kz` 3.2, all × 2.2 · dt), so the
pile stretches to fill a wide window and stays thin in depth; a slow churn (`−y · .06`, `x · .05`); exponential damping (linear
1.6/s, angular 1.2/s); position and quaternion integration; the colliders moved to world space. Pairs whose bounding spheres
touch are tested collider by collider: 55% of the penetration is corrected, split by inverse mass, then a contact impulse with
restitution .25 and Coulomb friction (.35 of the normal impulse, capped) is applied to both bodies, and its torque spins them at a
faked 1.6 × inverse mass. The cursor pushes at most one collider per body: 35% of the overlap out, a push `(max(0, v·n) · .35 + 1)
· .5` along the normal plus 2.5% of the cursor's velocity, and a spin.

```js
  const A = new THREE.Vector3(), B = new THREE.Vector3(), n = new THREE.Vector3(), ra = new THREE.Vector3(), rb = new THREE.Vector3(),
    va = new THREE.Vector3(), vb = new THREE.Vector3(), rel = new THREE.Vector3(), J = new THREE.Vector3(), t3 = new THREE.Vector3(), dq = new THREE.Quaternion();
  let aspect = 2;
  function step(dt) {
    const kx = .9 / Math.max(1, aspect * .95), ky = 1.6, kz = 3.2;
    for (const b of bodies) {
      // spring to the pile, anisotropic so the pile fills the window
      b.v.x -= b.p.x * kx * dt * 2.2; b.v.y -= b.p.y * ky * dt * 2.2; b.v.z -= b.p.z * kz * dt * 2.2;
      // slow churn keeps the pile alive
      b.v.x += -b.p.y * .06 * dt; b.v.y += b.p.x * .05 * dt;
      const damp = Math.exp(-1.6 * dt), wd = Math.exp(-1.2 * dt);
      b.v.multiplyScalar(damp); b.w.multiplyScalar(wd);
      b.p.addScaledVector(b.v, dt);
      dq.set(b.w.x * dt * .5, b.w.y * dt * .5, b.w.z * dt * .5, 0).multiply(b.q);
      b.q.x += dq.x; b.q.y += dq.y; b.q.z += dq.z; b.q.w += dq.w; b.q.normalize();
      for (let k = 0; k < b.cols.length; k++) { const c = b.cols[k]; b.wc[k].set(c[0], c[1], c[2]).applyQuaternion(b.q).add(b.p); }
    }
    // pairs
    for (let i = 0; i < bodies.length; i++) {
      const a = bodies[i];
      for (let j = i + 1; j < bodies.length; j++) {
        const b = bodies[j];
        const dx = b.p.x - a.p.x, dy = b.p.y - a.p.y, dz = b.p.z - a.p.z, rr = a.br + b.br;
        if (dx * dx + dy * dy + dz * dz > rr * rr) continue;
        for (let ka = 0; ka < a.cols.length; ka++) for (let kb = 0; kb < b.cols.length; kb++) {
          A.copy(a.wc[ka]); B.copy(b.wc[kb]);
          const R = a.cols[ka][3] + b.cols[kb][3];
          n.subVectors(B, A); const d = n.length();
          if (d >= R || d < 1e-5) continue;
          n.multiplyScalar(1 / d); const pen = R - d, sum = a.im + b.im;
          const corr = pen * .55 / sum;
          a.p.addScaledVector(n, -corr * a.im); b.p.addScaledVector(n, corr * b.im);
          for (const w of a.wc) w.addScaledVector(n, -corr * a.im); for (const w of b.wc) w.addScaledVector(n, corr * b.im);
          // contact impulse
          t3.copy(A).addScaledVector(n, a.cols[ka][3]);
          ra.subVectors(t3, a.p); rb.subVectors(t3, b.p);
          va.crossVectors(a.w, ra).add(a.v); vb.crossVectors(b.w, rb).add(b.v);
          rel.subVectors(vb, va); const vn = rel.dot(n);
          if (vn < 0) {
            const jn = -(1 + .25) * vn / sum;
            J.copy(n).multiplyScalar(jn);
            // friction
            rel.addScaledVector(n, -vn); const vt = rel.length();
            if (vt > 1e-4) J.addScaledVector(rel, -Math.min(.35 * jn, vt / sum) / vt);
            a.v.addScaledVector(J, -a.im); b.v.addScaledVector(J, b.im);
            t3.crossVectors(ra, J); a.w.addScaledVector(t3, -a.im * 1.6);
            t3.crossVectors(rb, J); b.w.addScaledVector(t3, b.im * 1.6);
          }
        }
      }
    }
    // cursor sphere (kinematic)
    if (cur.on) {
      for (const b of bodies) {
        for (let k = 0; k < b.cols.length; k++) {
          n.subVectors(b.wc[k], cur.p); const d = n.length(), R = cur.r * (cur.down ? 1.3 : 1) + b.cols[k][3];
          if (d >= R || d < 1e-5) continue;
          n.multiplyScalar(1 / d);
          b.p.addScaledVector(n, (R - d) * .35);
          const push = Math.max(0, cur.v.dot(n)) * .35 + 1.0;
          b.v.addScaledVector(n, push * .5);
          b.v.addScaledVector(cur.v, .025);
          ra.subVectors(b.wc[k], b.p); t3.crossVectors(ra, n); b.w.addScaledVector(t3, push * .5);
          break;
        }
      }
    }
  }
```

## The hero loop and GTAO
It renders only while the window is within 80 px of the viewport. `dt` is capped at 50 ms and split into three substeps. The flash
lerps the orange material toward lime by `sin(flash · π)` while `flash` drains at 1.4/s, so the colour peaks mid-way and returns.
The camera eases (.04 per frame) up to ±.45 / ±.3 toward the cursor and looks at the origin. Portrait windows widen the FOV to 50.
On desktop the frame goes through an EffectComposer on a half-float, 4× MSAA target: the scene, then GTAO (radius .55, distance
exponent 1.6, thickness .8, 24 samples, falloff .6; denoise luma 10, depth 2, normal 3, radius 8, 2 rings, 24 samples; blend .9)
for contact darkening, then the OutputPass. Phones render straight, with no shadows. `hero.warm` runs three steps and draws once,
so the loader can compile it.

```js
  let visible = true, last = performance.now(), acc = 0;
  new IntersectionObserver(es => { visible = es[0].isIntersecting; }, { rootMargin: '80px' }).observe(win);
  function resize() {
    const r = win.getBoundingClientRect();
    renderer.setSize(r.width, r.height, false);
    aspect = r.width / r.height; cam.aspect = aspect;
    cam.fov = aspect < 1 ? 50 : 30;
    cam.updateProjectionMatrix();
  }
  let comp = null, gtao = null;
  if (!PHONE) {
    try {
      const rt = new THREE.WebGLRenderTarget(2, 2, { samples: 4, type: THREE.HalfFloatType });
      comp = new EffectComposer(renderer, rt);
      comp.addPass(new RenderPass(scene, cam));
      gtao = new GTAOPass(scene, cam, 2, 2);
      gtao.updateGtaoMaterial({ radius: .55, distanceExponent: 1.6, thickness: .8, scale: 1, samples: 24, distanceFallOff: .6, screenSpaceRadius: false });
      gtao.updatePdMaterial({ lumaPhi: 10, depthPhi: 2, normalPhi: 3, radius: 8, rings: 2, samples: 24 });
      gtao.blendIntensity = .9;
      comp.addPass(gtao);
      comp.addPass(new OutputPass());
    } catch (e) { console.warn('gtao off', e); comp = null; }
  }
  function sizeComp() { if (!comp) return; const r = win.getBoundingClientRect(); comp.setPixelRatio(renderer.getPixelRatio()); comp.setSize(r.width, r.height); }
  sizeComp(); addEventListener('resize', sizeComp);
  resize(); addEventListener('resize', resize);
  const orange = mats.orange.color, oc = new THREE.Color(C.orange), lc = new THREE.Color(C.lime);
  hero.tick = (now) => {
    if (!visible) { last = now; return; }
    let dt = Math.min(.05, (now - last) / 1000); last = now;
    cur.v.subVectors(cur.p, cur.prev).multiplyScalar(1 / Math.max(dt, .001)); cur.v.clampLength(0, 40); cur.prev.copy(cur.p);
    const sub = 3; for (let i = 0; i < sub; i++) step(dt / sub);
    for (const b of bodies) { b.mesh.position.copy(b.p); b.mesh.quaternion.copy(b.q); }
    if (flash > 0) { flash = Math.max(0, flash - dt * 1.4); orange.copy(oc).lerp(lc, Math.sin(flash * Math.PI) ); }
    // gentle camera parallax with cursor
    const tx = cur.on ? clamp(cur.p.x / 6, -1, 1) * .45 : 0, ty = cur.on ? clamp(cur.p.y / 4, -1, 1) * .3 : 0;
    cam.position.x = lerp(cam.position.x, tx, .04); cam.position.y = lerp(cam.position.y, ty, .04); cam.lookAt(0, 0, 0);
    if (comp) comp.render(); else renderer.render(scene, cam);
  };
  hero.ready = true;
  hero.warm = () => { for (let i = 0; i < 3; i++) step(1 / 60); if (comp) comp.render(); else renderer.render(scene, cam); };
  hero.gtao = gtao; hero.renderer = renderer; hero.scene = scene; hero.cam = cam; hero.bodies = bodies; window.__hero = hero;
}
```

## The hero notch
The window is clipped by a CSS `path()` built from its size: rounded corners of 20 (14 under 760), and the bottom-left corner cut
away to the headline tab's size with an inverted radius at the inner corner. `border-radius` is dropped because the path carries
the corners. It runs on resize and again when the fonts are ready (the tab's size depends on the face).

```js
/* hero window notch: the bottom-left corner is cut away for the headline tab */
function notch() {
  const win = $('#win'), tab = $('.tab'); if (!win || !tab) return;
  const W = win.offsetWidth, H = win.offsetHeight, r = VW < 760 ? 14 : 20;
  const tw = Math.min(W - 80, tab.offsetWidth), th = Math.min(H - 80, tab.offsetHeight);
  const d = `M${r},0 H${W - r} A${r},${r} 0 0 1 ${W},${r} V${H - r} A${r},${r} 0 0 1 ${W - r},${H} H${tw + r} A${r},${r} 0 0 1 ${tw},${H - r} V${H - th + r} A${r},${r} 0 0 0 ${tw - r},${H - th} H${r} A${r},${r} 0 0 1 0,${H - th - r} V${r} A${r},${r} 0 0 1 ${r},0 Z`;
  win.style.clipPath = `path('${d}')`; win.style.borderRadius = '0';
}
addEventListener('resize', notch); document.fonts && document.fonts.ready.then(notch); notch();
```

## The ribbons — flat twisted paper bands in page space
A second renderer: transparent, DPR ≤ 2, neutral tone mapping, an orthographic camera in CSS pixels (x 0 → width, y 0 → −height,
z ±3000), the room environment at sigma .04, a white key 2.2, ambient .55. Each ribbon is a centripetal Catmull-Rom path in design
units (a 1440 board `d`, a 390 board `m` on phones; y down from its section's top, z in px) scaled by `VW / board`, 420 segments.
The band's width vector is turned about the tangent by `π × (smooth(f₁, f₁+.1, u) + smooth(f₂, f₂+.1, u)) + sin(u·13 + 1.7) × .32`:
a half turn at each flip point, a waver between (ribbon a's second flip, 2, lies past the end, so it flips once). Half width
`w × max(.62, min(1, s)) × .5` (× .62 on phones); the last 1.5% tapers 35%. Two meshes share the geometry: front face `cols[0]`,
back face `cols[1]`. `uShow` is the first sample left of x 560 and below y 480 (phone: 200 / 240), where the rider appears.

```js
/* ======================= RIBBONS (flat twisted band, page space) ======================= */
const rib = { list: [] };
function initRibbons() {
  const canvas = $('#ribbon');
  const renderer = new THREE.WebGLRenderer({ canvas, antialias: true, alpha: true });
  renderer.setPixelRatio(Math.min(devicePixelRatio, 2));
  renderer.outputColorSpace = THREE.SRGBColorSpace;
  renderer.toneMapping = THREE.NeutralToneMapping;
  const scene = new THREE.Scene();
  const cam = new THREE.OrthographicCamera(0, VW, 0, -VH, -3000, 3000);
  const pmrem = new THREE.PMREMGenerator(renderer);
  const env = pmrem.fromScene(new RoomEnvironment(), 0.04).texture;
  const l1 = new THREE.DirectionalLight(0xffffff, 2.2); l1.position.set(-.3, .7, 1); scene.add(l1);
  scene.add(new THREE.AmbientLight(0xffffff, .55));

  // paths in design units (1440 wide, y down from section top); z in px
  const PATHS = {
    a: { el: '#studio', w: 74, flips: [.8, 2], cols: [C.lilac, C.orange], rider: true,
      d: [[1640, 90, 0], [1380, 120, 60], [1130, 220, 120], [930, 380, 80], [700, 500, 20], [480, 560, -20], [330, 600, 0], [252, 640, 0]],
      m: [[460, 40, 0], [395, 80, 30], [360, 150, 40], [372, 215, 0], [330, 262, -20], [250, 280, 0], [195, 300, 0]] },
    b: { el: '#lab', w: 54, flips: [.36, .74], cols: [C.orange, C.lilac],
      d: [[1620, 30, 0], [1320, 70, 60], [1070, 180, 120], [1010, 400, 120], [1120, 590, 40], [1340, 560, -60], [1390, 330, -60], [1180, 220, 0], [930, 300, 60], [790, 470, 30], [960, 600, 0], [1260, 610, -30], [1640, 560, 0]],
      m: [[440, 60, 0], [330, 40, 30], [270, 120, 60], [300, 330, 30], [340, 520, 0], [200, 600, -30], [60, 520, 0], [-60, 480, 0]] },
  };
  const UP = new THREE.Vector3(0, 0, 1);
  function build(def) {
    const phone = VW < 760, base = phone ? 390 : 1440, s = VW / base;
    const pts = (phone ? def.m : def.d).map(([x, y, z]) => new THREE.Vector3(x * s, -y * s, z * s));
    const curve = new THREE.CatmullRomCurve3(pts, false, 'centripetal', .5);
    const SEG = 420, hw = def.w * Math.max(.62, Math.min(1, s)) * .5 * (phone ? .62 : 1);
    const pos = new Float32Array((SEG + 1) * 2 * 3), nor = new Float32Array((SEG + 1) * 2 * 3), idx = [];
    const T = new THREE.Vector3(), Bn = new THREE.Vector3(), Z = new THREE.Vector3(), Wd = new THREE.Vector3(), N = new THREE.Vector3(), P = new THREE.Vector3();
    const samples = [];
    for (let i = 0; i <= SEG; i++) {
      const u = i / SEG; curve.getPointAt(u, P); curve.getTangentAt(u, T);
      Bn.crossVectors(T, UP).normalize(); Z.crossVectors(Bn, T).normalize();
      const th = Math.PI * (smooth(def.flips[0], def.flips[0] + .1, u) + smooth(def.flips[1], def.flips[1] + .1, u)) + Math.sin(u * 13 + 1.7) * .32;
      Wd.copy(Bn).multiplyScalar(Math.cos(th)).addScaledVector(Z, Math.sin(th));
      N.crossVectors(T, Wd).normalize();
      // taper the very tip so the end reads as a folded paper end
      const taper = 1 - smooth(.985, 1, u) * .35;
      pos.set([P.x + Wd.x * hw * taper, P.y + Wd.y * hw * taper, P.z + Wd.z * hw * taper, P.x - Wd.x * hw * taper, P.y - Wd.y * hw * taper, P.z - Wd.z * hw * taper], i * 6);
      nor.set([N.x, N.y, N.z, N.x, N.y, N.z], i * 6);
      samples.push({ x: P.x, y: P.y, tx: T.x, ty: T.y, dx: P.x / s, dy: -P.y / s });
      if (i < SEG) { const a = i * 2; idx.push(a, a + 1, a + 2, a + 1, a + 3, a + 2); }
    }
    const g = new THREE.BufferGeometry();
    g.setAttribute('position', new THREE.BufferAttribute(pos, 3));
    g.setAttribute('normal', new THREE.BufferAttribute(nor, 3));
    g.setIndex(idx);
    let uShow = 1; for (let i = 0; i <= SEG; i++) { const q = samples[i]; if (phone ? (q.dy > 240 && q.dx < 200) : (q.dx < 560 && q.dy > 480)) { uShow = i / SEG; break; } }
    return { g, samples, SEG, uShow };
  }
```
Per frame: the draw progress runs from 85% of a viewport above the section's top over 95% of a viewport (80 / 80% on phones),
eased .2 per frame; the draw range grows with it, so the ribbon DRAWS itself, and the group moves with the page. The rider hangs 6
px under the drawing tip, fades and scales .6 → 1 over the .07 after `uShow`, and tilts at .18 of the tangent's angle, straightening
over the last 20%. The canvas renders only while a ribbon is on screen (plus one frame to clear).

```js
  for (const key of ['a', 'b']) {
    const def = PATHS[key];
    const front = new THREE.MeshStandardMaterial({ color: def.cols[0], roughness: .42, metalness: 0, side: THREE.FrontSide, envMap: env, envMapIntensity: .55 });
    const back = new THREE.MeshStandardMaterial({ color: def.cols[1], roughness: .5, metalness: 0, side: THREE.BackSide, envMap: env, envMapIntensity: .55 });
    const group = new THREE.Group(); scene.add(group);
    const r = { def, front, back, group, sec: $(def.el), p: 0 };
    r.rebuild = () => {
      group.clear(); if (r.geo) r.geo.g.dispose();
      r.geo = build(def);
      group.add(new THREE.Mesh(r.geo.g, front), new THREE.Mesh(r.geo.g, back));
    };
    r.rebuild(); rib.list.push(r);
  }
  const rider = $('#rider');
  function resize() {
    VW = innerWidth; VH = innerHeight;
    renderer.setSize(VW, VH, false);
    cam.left = 0; cam.right = VW; cam.top = 0; cam.bottom = -VH; cam.updateProjectionMatrix();
    for (const r of rib.list) r.rebuild();
  }
  resize(); addEventListener('resize', resize);
  let wasVisible = true;
  rib.tick = (sy) => {
    let any = false;
    for (const r of rib.list) {
      const top = r.sec.offsetTop; // section top in page px
      const phone = VW < 760;
      const start = top - VH * (phone ? .8 : .85), len = VH * (phone ? .8 : .95);
      const p = clamp((sy - start) / len);
      r.p = lerp(r.p, p, .2);
      if (Math.abs(r.p - p) < .0005) r.p = p;
      const onscreen = sy + VH > top - VH * .2 && sy < top + r.sec.offsetHeight;
      r.group.visible = onscreen && r.p > .002;
      r.group.position.y = -(top - sy);
      const cnt = Math.floor(r.geo.SEG * r.p) * 6;
      r.geo.g.setDrawRange(0, cnt);
      if (r.group.visible) any = true;
      if (r.def.rider) {
        const i = Math.max(0, Math.min(r.geo.SEG, Math.floor(r.geo.SEG * r.p)));
        const s = r.geo.samples[i];
        const x = s.x, y = -(s.y) + (top - sy); // screen px
        const ang = Math.atan2(-s.ty, s.tx);
        const cw = rider.offsetWidth;
        const show = smooth(r.geo.uShow, r.geo.uShow + .07, r.p) * (onscreen ? 1 : 0);
        const rot = (ang - Math.PI / 2) * .18 * (1 - smooth(.8, 1, r.p));
        rider.style.opacity = show;
        rider.style.transform = `translate3d(${x - cw / 2}px,${y - 6}px,0) rotate(${rot}rad) scale(${.6 + .4 * show})`;
        rider.style.transformOrigin = '50% 0';
      }
    }
    if (any || wasVisible) renderer.render(scene, cam);
    wasVisible = any;
  };
}
```

## The finale — the haus: scene and lights
A third renderer: ACES Filmic at exposure 1.05, soft shadows, DPR ≤ 1.6 (1.5 on phones), `#0e0e10` background and fog 22 → 48,
the room environment with every material's env intensity cut to 55%, a 34° camera (52° in portrait). A 40-unit floor disc
`#151517` (roughness .85) takes shadows; a warm spot `#fff1e2` (560, distance 60, angle .55, edge softness .6, decay 2) from (−8, 18,
10) onto (0, 1.5, 0) with a 2048 shadow map (1024 on phones); an orange point light 170 behind right, a lilac point light 120 behind
left, and a dim violet hemisphere .35.

```js
/* ======================= FINALE: the haus ======================= */
const fin = {};
function initFinale() {
  const canvas = $('#finCanvas'), sec = $('#fin');
  const renderer = new THREE.WebGLRenderer({ canvas, antialias: true, powerPreference: 'high-performance' });
  renderer.setPixelRatio(Math.min(devicePixelRatio, PHONE ? 1.5 : 1.6));
  renderer.outputColorSpace = THREE.SRGBColorSpace;
  renderer.toneMapping = THREE.ACESFilmicToneMapping; renderer.toneMappingExposure = 1.05;
  renderer.shadowMap.enabled = true; renderer.shadowMap.type = THREE.PCFSoftShadowMap;
  const scene = new THREE.Scene();
  scene.background = new THREE.Color(0x0e0e10);
  scene.fog = new THREE.Fog(0x0e0e10, 22, 48);
  const pmrem = new THREE.PMREMGenerator(renderer);
  const env = pmrem.fromScene(new RoomEnvironment(), 0.04).texture;
  const mats = makeMats(env);
  for (const k in mats) mats[k].envMapIntensity *= .55;
  const cam = new THREE.PerspectiveCamera(34, 1, .1, 120);

  const floor = new THREE.Mesh(new THREE.CircleGeometry(40, 64), new THREE.MeshStandardMaterial({ color: 0x151517, roughness: .85 }));
  floor.rotation.x = -Math.PI / 2; floor.receiveShadow = true; scene.add(floor);
  const spot = new THREE.SpotLight(0xfff1e2, 560, 60, .55, .6, 2);
  spot.position.set(-8, 18, 10); spot.target.position.set(0, 1.5, 0);
  spot.castShadow = true; spot.shadow.mapSize.set(PHONE ? 1024 : 2048, PHONE ? 1024 : 2048); spot.shadow.bias = -.0003; spot.shadow.normalBias = .03;
  scene.add(spot, spot.target);
  const rimL = new THREE.PointLight(C.orange, 170, 30, 2); rimL.position.set(6, 4, -7); scene.add(rimL);
  const fillL = new THREE.PointLight(C.lilac, 120, 30, 2); fillL.position.set(-9, 3, -4); scene.add(fillL);
  scene.add(new THREE.HemisphereLight(0x8c86b0, 0x0e0c0a, .35));
```

## The haus — 58 target poses and their order
On a 1.2-unit grid: three courses of walls, five blocks wide front and back plus the two side blocks, with a door gap (front centre,
lower two courses) and two orange ring windows (front, middle course); the wall colour is a little arithmetic pattern of bone,
graphite and black. The gable roof is two rows per slope of brick–cube–brick tilted to the slope, alternating orange and black;
two bone capsules lie along the ridge, a lilac capsule stands as the chimney and an orange ring stands on top as a weathervane;
eight pieces make a garden. That is 58, written into the count (`00 / 58 blocks placed`) and the end title through `numWord`
("Fifty-eight"). Each piece's start is random in a 26 × 18 area 16–30 units up, with a random turn; the fall order sorts the
targets by height plus up to 1.2 of noise (seed 11), and each piece's `delay` is its rank / 58.

```js
  // targets: a little toy house of blocks
  const U = 1.2, T = [];
  const put = (shape, mat, x, y, z, rx = 0, ry = 0, rz = 0) => T.push({ shape, mat, p: new THREE.Vector3(x * U, y * U + .58, z * U), r: new THREE.Euler(rx, ry, rz) });
  const wallMat = (x, y, z) => ((x + y + z) % 3 === 0 ? 'graphite' : (x * 7 + y * 3 + z) % 5 === 0 ? 'black' : 'bone');
  for (let y = 0; y < 3; y++) {
    for (let x = -2; x <= 2; x++) for (const z of [-1, 1]) {
      if (z === 1 && x === 0 && y < 2) continue; // door
      if (z === 1 && Math.abs(x) === 1 && y === 1) { put('ring', 'orange', x, y, z + .02); continue; } // round windows
      put('cube', wallMat(x + 2, y, z + 1), x, y, z);
    }
    for (const x of [-2, 2]) put('cube', wallMat(x + 2, y, 0), x, y, 0);
  }
  // gable roof: two tilted rows of bricks per slope, a capsule ridge, a chimney
  const putW = (shape, mat, x, y, z, rx = 0, ry = 0, rz = 0) => T.push({ shape, mat, p: new THREE.Vector3(x, y, z), r: new THREE.Euler(rx, ry, rz) });
  for (const sd of [-1, 1]) {
    const Ez = sd * 1.95, Ey = 3 * U + .1, Rz = sd * .12, Ry = 3 * U + 1.75;
    const nz = sd * (Ry - Ey), ny = Math.abs(Ez - Rz), nl = Math.hypot(nz, ny);
    const ang = sd * Math.atan2(Math.abs(nz), ny);
    for (const [f, row] of [[.24, 0], [.74, 1]]) {
      const cz = lerp(Ez, Rz, f) + nz / nl * .5, cy = lerp(Ey, Ry, f) + ny / nl * .5;
      const m1 = (row + (sd > 0 ? 1 : 0)) % 2 ? 'black' : 'orange', m2 = m1 === 'orange' ? 'black' : 'orange';
      putW('brick', m1, -1.5 * U + (row ? .3 : 0), cy, cz, ang); putW('cube', m2, (row ? .3 : 0) + (row ? .6 : 0) * 0, cy, cz, ang); putW('brick', m1, 1.5 * U + (row ? .3 : 0), cy, cz, ang);
    }
  }
  putW('capsule', 'bone', -1.3, 3 * U + 2.12, 0, 0, 0, Math.PI / 2); putW('capsule', 'bone', 1.3, 3 * U + 2.12, 0, 0, 0, Math.PI / 2);
  putW('capsule', 'lilac', 1.75, 3 * U + 2.15, -1.05); // chimney
  putW('ring', 'orange', 0, 3 * U + 3.05, 0, 0, Math.PI / 2, 0); // weathervane ring
  // the garden
  const garden = [['pebble', 'lilac', -4.2, -.05, 2.2], ['pebble', 'bone', -3.4, -.05, 3.1], ['ring', 'lilac', 3.8, -.25, 2.4, Math.PI / 2], ['pebble', 'graphite', 4.4, -.05, .2], ['capsule', 'orange', -3.8, -.1, -1.8, 0, 0, Math.PI / 2], ['ring', 'bone', 3.2, -.25, -2.6, Math.PI / 2], ['pebble', 'orange', 2.4, -.05, 3.6], ['cube', 'lilac', -2.7, 0, 3.4, 0, .5, 0]];
  for (const g of garden) put(g[0], g[1], g[2], g[3], g[4], g[5] || 0, g[6] || 0, g[7] || 0);
  const NB = T.length;
  $('#fcount').textContent = `00 / ${NB} blocks placed`;
  $('#fend h3').innerHTML = `${numWord(NB)} blocks.<br>Zero <em>glue.</em>`;
  let seed = 11; const rnd = () => (seed = (seed * 16807) % 2147483647, (seed - 1) / 2147483646);
  const order = T.map((t, i) => ({ i, k: t.p.y + rnd() * 1.2 })).sort((a, b) => a.k - b.k);
  const pieces = T.map((t, i) => {
    const m = new THREE.Mesh(GEO[t.shape], mats[t.mat]); m.castShadow = m.receiveShadow = true; scene.add(m);
    const qT = new THREE.Quaternion().setFromEuler(t.r);
    const q0 = new THREE.Quaternion().setFromEuler(new THREE.Euler(rnd() * 7, rnd() * 7, rnd() * 7));
    const p0 = new THREE.Vector3((rnd() - .5) * 26, 16 + rnd() * 14, (rnd() - .5) * 18);
    return { m, t, qT, q0, p0 };
  });
  order.forEach((o, n) => { pieces[o.i].delay = n / NB; });
```

## The storm, the halo, bloom
420 small toys (150 on phones) in three InstancedMeshes (cube, ring, capsule) sharing one white clearcoat material, each instance
coloured from an orange-heavy palette; radius 6.5–16, height around 3, an angular speed `.9 / √r`, a size .18–.48 and its own
spin. The halo is two tori facing the camera at y 3.2: orange (8.2, tube .075, colour × 2.2) and lilac (7.4, tube .035, × 1.6),
`toneMapped: false` so they blow out into the bloom. Desktop adds an UnrealBloomPass (strength .28, radius .5, threshold .9) before
the OutputPass; phones render straight.

```js
  // the storm: hundreds of small toys orbiting the haus
  const NS = PHONE ? 150 : 420;
  const pal = [C.orange, C.orange, C.bone, C.bone, C.black, C.graphite, C.lilac].map(c => new THREE.Color(c));
  const smat = new THREE.MeshPhysicalMaterial({ color: 0xffffff, roughness: .35, clearcoat: .8, clearcoatRoughness: .1, envMap: env, envMapIntensity: .5 });
  const sGeo = [GEO.cube, GEO.ring, GEO.capsule];
  const storm = sGeo.map(g => { const im = new THREE.InstancedMesh(g, smat, Math.ceil(NS / 3)); im.castShadow = false; scene.add(im); return im; });
  const sp = [];
  for (let i = 0; i < NS; i++) {
    const r = 6.5 + Math.pow(rnd(), .9) * 9.5;
    sp.push({ m: i % 3, k: Math.floor(i / 3), r, a: rnd() * Math.PI * 2, y: 3 + (rnd() - .5) * (2 + r * .5), w: .9 / Math.sqrt(r) * (rnd() > .5 ? 1 : 1), s: .18 + rnd() * .3, rx: rnd() * 6, ry: rnd() * 6, rs: (rnd() - .5) * 3, d: rnd() });
    storm[i % 3].setColorAt(Math.floor(i / 3), pal[Math.floor(rnd() * pal.length)]);
  }
  storm.forEach(im => { im.instanceColor.needsUpdate = true; });
  const dm = new THREE.Object3D();
  // the halo: two neon rings that open behind the haus
  const halo = new THREE.Group(); halo.position.set(0, 3.2, 0); scene.add(halo);
  const h1 = new THREE.Mesh(new THREE.TorusGeometry(8.2, .075, 16, 200), new THREE.MeshBasicMaterial({ color: new THREE.Color(C.orange).multiplyScalar(2.2), toneMapped: false }));
  const h2 = new THREE.Mesh(new THREE.TorusGeometry(7.4, .035, 12, 200), new THREE.MeshBasicMaterial({ color: new THREE.Color(C.lilac).multiplyScalar(1.6), toneMapped: false }));
  halo.add(h1, h2);
  const flood = $('#flood');

  let comp = null;
  if (!PHONE) {
    comp = new EffectComposer(renderer);
    comp.addPass(new RenderPass(scene, cam));
    comp.addPass(new UnrealBloomPass(new THREE.Vector2(256, 256), .28, .5, .9));
    comp.addPass(new OutputPass());
  }
  function resize() {
    const w = innerWidth, h = innerHeight;
    renderer.setSize(w, h, false); if (comp) comp.setSize(w, h);
    cam.aspect = w / h; cam.fov = w / h < 1 ? 52 : 34; cam.updateProjectionMatrix();
  }
  resize(); addEventListener('resize', resize);
```

## The kinetic words
Three lines become one `span.kw` per word; each word's offset from the block's centre is measured (again on resize and when the
fonts are ready) so the scroll can push it outward from where it sits.

```js
  // kinetic words
  const kin = $('#kin');
  const lines = ['Every block', 'is a decision.', 'Stack them with care'];
  kin.innerHTML = lines.map(l => l.split(' ').map(w => `<span class="kw">${w}</span>`).join(' ')).join('<br>');
  const kws = $$('.kw', kin);
  let kwPos = [];
  function measure() {
    const kr = kin.getBoundingClientRect(); const cx = kr.left + kr.width / 2, cy = kr.top + kr.height / 2;
    kwPos = kws.map(w => { w.style.transform = ''; const r = w.getBoundingClientRect(); return { dx: r.left + r.width / 2 - cx, dy: r.top + r.height / 2 - cy }; });
  }
  measure(); addEventListener('resize', measure); document.fonts && document.fonts.ready.then(measure);
```

## The finale tick — all scrubbed by scroll
`p` is the stage's scroll progress. Words: with `q = smooth(0, .3, p)` each moves out along its own offset (× 3.2q, then × 1.15
across and × .9 down), scales `1 + 1.9q` and fades over p .22–.34. Assembly: `a = smooth(.06, .58, p)`; each piece's `t =
clamp((a − delay × .78) / .22)`; x and z ease out, y follows `t²` so it FALLS, a small bounce over the last 22%, the rotation
slerps home slightly ahead. The end title shows over .6–.66, leaves over .73–.77. The storm grows in over .05–.42, spins `p × 5.5`
plus a slow clock, and RUSHES over .72–.86 (radii −35%, faster, sizes +60%). The halo scales .42 → 1 over .1–.62 and brightens. The
flood is `clip-path: circle(0 → 120% at 50% 46%)` over .765–.83. The camera orbits −.95 → .62 rad, radius 21 → 17 (× 1.5 in
portrait, −25% in the rush), height 11 → 5.2, aim y 3.4 → 2.4 (1.6 lower in portrait). It renders only within 100 px of view.

```js
  const fcount = $('#fcount'), fend = $('#fend');
  const tq = new THREE.Quaternion();
  let visible = false;
  new IntersectionObserver(es => { visible = es[0].isIntersecting; }, { rootMargin: '100px' }).observe(sec);
  let lastPlaced = -1;
  fin.tick = (sy, now) => {
    if (!visible) return;
    const top = sec.offsetTop, h = sec.offsetHeight - VH;
    const p = clamp((sy - top) / h);
    // words: spread outward & scale, then go
    const q = smooth(0, .3, p);
    kws.forEach((w, i) => {
      const k = kwPos[i] || { dx: 0, dy: 0 };
      const sp = 1 + q * 3.2;
      w.style.transform = `translate(${k.dx * (sp - 1) * 1.15}px,${k.dy * (sp - 1) * .9}px) scale(${1 + q * 1.9})`;
      w.style.opacity = String(1 - smooth(.22, .34, p));
    });
    // assembly
    const a = smooth(.06, .58, p) * 1.0;
    let placed = 0;
    for (const pc of pieces) {
      const t = clamp((a - pc.delay * .78) / .22);
      const e = t;
      const yE = t < 1 ? (t * t) : 1; // gravity-ish fall
      const bounce = t > .78 ? Math.sin((t - .78) / .22 * Math.PI) * .35 * (1 - t) * 4 : 0;
      pc.m.position.set(lerp(pc.p0.x, pc.t.p.x, eo(e)), lerp(pc.p0.y, pc.t.p.y, yE) + bounce, lerp(pc.p0.z, pc.t.p.z, eo(e)));
      tq.copy(pc.q0).slerp(pc.qT, eo(Math.min(1, t * 1.15)));
      pc.m.quaternion.copy(tq);
      pc.m.visible = t > 0;
      if (t >= 1) placed++;
    }
    if (placed !== lastPlaced) { fcount.textContent = `${String(placed).padStart(2, '0')} / ${NB} blocks placed`; lastPlaced = placed; }
    fend.style.opacity = smooth(.6, .66, p) * (1 - smooth(.73, .77, p));
    fend.style.transform = `translateY(${(1 - smooth(.62, .72, p)) * 30}px)`;
    // storm
    const sIn = lerp(.22, 1, smooth(.05, .42, p)), spin = p * 5.5 + now * .00008, rush = smooth(.72, .86, p);
    for (const q of sp) {
      const sc = q.s * smooth(q.d * .5, q.d * .5 + .5, sIn) * (1 + rush * .6);
      const ang = q.a + spin * q.w * 2.2 + rush * q.w * 6;
      const rr = q.r * (1 - rush * .35);
      dm.position.set(Math.cos(ang) * rr, q.y + Math.sin(ang * 2 + q.d * 6) * .4, Math.sin(ang) * rr);
      dm.rotation.set(q.rx + now * .0004 * q.rs, q.ry + spin * q.rs, 0);
      dm.scale.setScalar(Math.max(.0001, sc));
      dm.updateMatrix(); storm[q.m].setMatrixAt(q.k, dm.matrix);
    }
    storm.forEach(im => { im.instanceMatrix.needsUpdate = true; });
    // halo opens with the storm, faces the camera
    const hs = lerp(.42, 1, eo(smooth(.1, .62, p))) * (1 + rush * .25);
    halo.scale.setScalar(hs); halo.visible = true;
    h1.material.color.setRGB(2.2, .78, .3).multiplyScalar(lerp(.35, 1, smooth(.1, .4, p)));
    h2.material.color.setRGB(1.2, 1.0, 2.0).multiplyScalar(lerp(.25, 1, smooth(.15, .5, p)));
    halo.quaternion.copy(cam.quaternion); h2.rotation.z = now * .0002;
    // flood: the halo opens into the footer's orange
    const fl = smooth(.765, .83, p);
    flood.style.clipPath = `circle(${fl * 120}% at 50% 46%)`;
    // camera orbit
    const ang = lerp(-.95, .62, eo(p)) + Math.sin(now * .0002) * .03;
    const rad = lerp(21, 17, p) * (cam.aspect < 1 ? 1.5 : 1);
    const hgt = lerp(11, 5.2, smooth(0, 1, p));
    cam.position.set(Math.sin(ang) * rad * (1 - rush * .25), hgt, Math.cos(ang) * rad * (1 - rush * .25));
    cam.lookAt(0, lerp(3.4, 2.4, p) - (cam.aspect < 1 ? 1.6 : 0), 0);
    if (comp) comp.render(); else renderer.render(scene, cam);
  };
  fin.warm = () => { renderer.compile(scene, cam); };
  window.__fin = { renderer, scene, cam, pieces, get vis() { return visible; } };
}
function numWord(n) {
  const ones = ['Zero', 'One', 'Two', 'Three', 'Four', 'Five', 'Six', 'Seven', 'Eight', 'Nine', 'Ten', 'Eleven', 'Twelve', 'Thirteen', 'Fourteen', 'Fifteen', 'Sixteen', 'Seventeen', 'Eighteen', 'Nineteen'];
  const tens = ['', '', 'Twenty', 'Thirty', 'Forty', 'Fifty', 'Sixty', 'Seventy', 'Eighty', 'Ninety'];
  if (n < 20) return ones[n];
  const t = Math.floor(n / 10), o = n % 10;
  return tens[t] + (o ? '-' + ones[o].toLowerCase() : '');
}
```

## Work — the grid, the index and the peek
Eight projects: `[name, disciplines, year, id]`. The grid card's key art is `${WORK_BASE}${id}.jpg` and the index peek is
`${WORK_BASE}${id}-s.jpg` — the base URL constant is added here because the build loaded both from a relative folder; it resolves
to `p1.jpg`…`p8.jpg` and `p1-s.jpg`…`p8-s.jpg` on the hosted folder. Cards 1, 4, 5, 8 are `wide` (16:11) in 7 columns; cards 2, 3,
6, 7 span 5 columns, drop 96 px and stand 5:5.6. The toggle's knob slides to the active button (.55 s); switching to Index also
marks every card revealed. The peek follows the pointer at (+24, −110) px with a .16 lerp and swaps its image on entering a row.

```js
/* ======================= WORK ======================= */
const WORK_BASE = 'https://www.vividsites.app/media/flagship/blockhaus/work/';   // added: the hosted folder the key art and peeks are built from
const WORK = [
  ['Mosswick', 'Brand world · WebGL · Physics', '2026', 'p1'],
  ['Shoal Atlas', 'Data story · Real-time 3D · Sound', '2026', 'p2'],
  ['Kilnfest ’26', 'Festival identity · Motion · Web', '2025', 'p3'],
  ['Owlhour FM', 'App launch · Interactive 3D', '2025', 'p4'],
  ['Pip & Stride', 'Product launch · Exploded 3D', '2025', 'p5'],
  ['Foldfare', 'Fintech · Illustration · Web', '2024', 'p6'],
  ['Coin-Op Nocturne', 'Game launch · Interactive', '2024', 'p7'],
  ['Saltlight', 'Fragrance · CGI film', '2024', 'p8'],
];
function initWork() {
  const grid = $('#grid'), index = $('#index');
  grid.innerHTML = WORK.map((w, i) => `<a class="pc${i % 4 === 0 || i % 4 === 3 ? ' wide' : ''}" href="#work"><div class="im"><img loading="lazy" src="${WORK_BASE}${w[3]}.jpg" alt="${w[0]} key art"><span class="idx mono">${String(i + 1).padStart(2, '0')} / 08</span><span class="chip">↗</span></div><div class="tags mono"><span>${w[1]}</span><span>${w[2]}</span></div><h3><span class="ar">→</span>${w[0]}</h3></a>`).join('');
  index.innerHTML = WORK.map((w, i) => `<a class="irow" href="#work" data-i="${i}"><span class="mono">${String(i + 1).padStart(2, '0')}</span><b>${w[0]}</b><span class="mono disc">${w[1]}</span><span class="mono">${w[2]}</span></a>`).join('');
  const tog = $('#tog'), kn = $('#kn'), sec = $('#work');
  const place = () => { const on = $('button.on', tog); kn.style.width = on.offsetWidth + 'px'; kn.style.transform = `translateX(${on.offsetLeft - 4}px)`; };
  $$('button', tog).forEach(b => b.addEventListener('click', () => {
    $$('button', tog).forEach(x => x.classList.toggle('on', x === b)); place();
    sec.classList.toggle('list', b.dataset.v === 'list');
    $$('.pc', grid).forEach(p => p.classList.add('in'));
  }));
  place(); document.fonts && document.fonts.ready.then(place);
  // index peek
  const peek = $('#peek'), pimg = $('img', peek); let px = 0, py = 0, tx = 0, ty = 0, on = false;
  $$('.irow', index).forEach(r => {
    r.addEventListener('pointerenter', () => { pimg.src = `${WORK_BASE}${WORK[r.dataset.i][3]}-s.jpg`; peek.classList.add('on'); on = true; });
    r.addEventListener('pointerleave', () => { peek.classList.remove('on'); on = false; });
  });
  addEventListener('pointermove', e => { tx = e.clientX + 24; ty = e.clientY - 110; });
  (function lp() { px = lerp(px, tx, .16); py = lerp(py, ty, .16); if (on || peek.classList.contains('on')) peek.style.transform = `translate(${px}px,${py}px)`; requestAnimationFrame(lp); })();
}
```

## The reel — the growing card and the riding words
`p = (scroll − top + .35 VH) / (stage − VH + .35 VH)`, so it moves before the pin. The card grows on `e = easeOutCubic(smooth(0,
.62, p))` from `min(24vw, 360)` × .62 (phone 42vw × 1.25) to `VW − 2g` × `VH − 192` (phone 72vh), drops 12 px, radius 26 → 20
(18 → 14). The words exist twice: ink under the card, white over it, clipped by `inset(... round r)` to the card's own rectangle,
so each turns white exactly at the card edge. They flank the card 26 px out at scale .78 (phone: above and below it), then on `k =
easeOutCubic(smooth(.08, .62, p))` ride to its top-left and bottom-right corners, 40 px in (18), scaling to 1. Ticks fade in over
.5–.7, the meta over .55–.75; the play disc lerps (.16) to the cursor or the centre and shows once `e > .5` or on hover. The video
(hosted URL, constant added) plays muted only in view; a click opens the player unmuted from 0; Lenis stops while it is open.

```js
/* ======================= REEL ======================= */
const REEL_URL = 'https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/flagship/blockhaus/reel.mp4';   // added: the hosted reel
const reel = {};
function initReel() {
  const sec = $('#reel'), card = $('#rcard'), vid = $('#rvid'), wk = $('#wk'), ww = $('#ww'), playb = $('#playb');
  const marks = $$('.tmark', sec);
  vid.src = REEL_URL;
  let playing = false;
  new IntersectionObserver(es => { const v = es[0].isIntersecting; if (v && !playing) { vid.play().catch(() => {}); playing = true; } else if (!v && playing) { vid.pause(); playing = false; } }).observe(sec);
  const L = [$('[data-w=l]', wk), $('[data-w=l]', ww)], R = [$('[data-w=r]', wk), $('[data-w=r]', ww)];
  // play button follows cursor inside the card
  let bx = 0, by = 0, tx = 0, ty = 0, over = false;
  card.addEventListener('pointermove', e => { tx = e.clientX; ty = e.clientY; if (!over) { bx = tx; by = ty; } over = true; playb.classList.add('on'); });
  card.addEventListener('pointerleave', () => { over = false; });
  card.addEventListener('click', openPlayer);
  reel.tick = (sy) => {
    const top = sec.offsetTop, h = sec.offsetHeight - VH;
    const p = clamp((sy - top + VH * .35) / (h + VH * .35));
    const g = parseFloat(getComputedStyle(document.documentElement).getPropertyValue('--g')) || 72;
    const phone = VW < 760;
    const e = eo(smooth(.0, .62, p));
    const w0 = phone ? VW * .42 : Math.min(VW * .24, 360), h0 = w0 * (phone ? 1.25 : .62);
    const w1 = VW - g * 2, h1 = phone ? VH * .72 : VH - 120 - 72;
    const cw = lerp(w0, w1, e), ch = lerp(h0, h1, e);
    const cy = lerp(0, phone ? 0 : 12, e);
    card.style.width = cw + 'px'; card.style.height = ch + 'px';
    card.style.transform = `translate(-50%,calc(-50% + ${cy}px))`;
    card.style.borderRadius = lerp(phone ? 18 : 26, phone ? 14 : 20, e) + 'px';
    // words flank the small card, then ride its edges into opposite corners
    const fs = L[0].offsetHeight || 150;
    const lw = L[0].offsetWidth, rw = R[0].offsetWidth;
    const x0c = (VW - cw) / 2, pad = phone ? 18 : 40;
    const gap = phone ? 0 : 26;
    const lxA = phone ? VW / 2 - lw / 2 : x0c - gap - lw, lyA = phone ? -ch / 2 - fs * .5 : 0;
    const rxA = phone ? VW / 2 - rw / 2 : x0c + cw + gap, ryA = phone ? ch / 2 + fs * .5 : 0;
    const lxB = x0c + pad, lyB = -ch / 2 + fs * .5 + pad * .4;
    const rxB = x0c + cw - pad - rw, ryB = ch / 2 - fs * .5 - pad * .5;
    const k = eo(smooth(.08, .62, p));
    const sc = phone ? 1 : lerp(.78, 1, k);
    for (const el of L) { el.style.transformOrigin = '100% 50%'; el.style.transform = `translate(${lerp(lxA, lxB, k)}px, calc(-52% + ${cy + lerp(lyA, lyB, k)}px)) scale(${sc})`; }
    for (const el of R) { el.style.transformOrigin = '0 50%'; el.style.transform = `translate(${lerp(rxA, rxB, k)}px, calc(-52% + ${cy + lerp(ryA, ryB, k)}px)) scale(${sc})`; }
    // white copy only inside the card
    const x0 = (VW - cw) / 2, y0 = (VH - ch) / 2 + cy;
    ww.style.clipPath = `inset(${y0}px ${VW - x0 - cw}px ${VH - y0 - ch}px ${x0}px round ${parseFloat(card.style.borderRadius)}px)`;
    marks.forEach((m, i) => { const mx = i % 2 ? x0 + cw + 10 : x0 - 21, my = i < 2 ? y0 - 21 : y0 + ch + 10; m.style.transform = `translate(${mx}px,${my}px)`; m.style.opacity = smooth(.5, .7, p); });
    $('#rmeta').style.opacity = smooth(.55, .75, p);
    const hx = over ? tx : VW / 2, hy = over ? ty : (VH / 2 + cy);
    bx = lerp(bx || hx, hx, .16); by = lerp(by || hy, hy, .16); playb.style.left = bx + 'px'; playb.style.top = by + 'px';
    playb.classList.toggle('on', e > .5 || over);
  };
  const player = $('#player'), pv = $('#pvid');
  function openPlayer() { pv.src = REEL_URL; player.classList.add('on'); pv.currentTime = 0; pv.muted = false; pv.play().catch(() => {}); lenis && lenis.stop(); }
  function close() { player.classList.remove('on'); pv.pause(); lenis && lenis.start(); }
  $('#px').addEventListener('click', close);
  addEventListener('keydown', e => { if (e.key === 'Escape') { close(); setMenu(false); } });
}
```

## Chrome — menu, anchors, ticker, reveals, the letter roll, the header and gauge
The menu button toggles `body.menu-open` (outside click, a menu link or Escape closes it). Every `#` anchor scrolls with Lenis over
1.6 s. The booking line is the quarter after this one with its year (`Q4` → `Q1 ’27`); the Lisbon time comes from `Intl` with
`timeZone: 'Europe/Lisbon'`; every 3.2 s the next message slides up from 110% as the old leaves to −110%. One observer (bottom
margin −12%) adds `.in` once to `.rv`, `.fade` and `.pc`. The footer line becomes one masked `span.ch` per letter carrying its own
copy (`::after`), 18 ms apart, so hover rolls it up by half. `chromeTick` hides the header after 60 px of downward scroll past .6 of
a viewport and returns it after 40 px up (never with the menu open), runs the gauge, and turns header and gauge dark over the finale.

```js
/* ======================= chrome, menu, ticker, gauge, reveals ======================= */
let lenis = null;
function setMenu(open) { document.body.classList.toggle('menu-open', open); $('#mbtn').setAttribute('aria-expanded', open); }
function initChrome() {
  $('#mbtn').addEventListener('click', e => { e.stopPropagation(); setMenu(!document.body.classList.contains('menu-open')); });
  document.addEventListener('click', e => { if (!e.target.closest('#menu')) setMenu(false); });
  $$('#menu a').forEach(a => a.addEventListener('click', () => setMenu(false)));
  // anchor links via lenis
  $$('a[href^="#"]').forEach(a => a.addEventListener('click', e => {
    const id = a.getAttribute('href'); const t = id === '#top' ? 0 : $(id); if (t === null) return;
    e.preventDefault(); lenis ? lenis.scrollTo(t, { duration: 1.6 }) : (t === 0 ? scrollTo(0, 0) : t.scrollIntoView());
  }));
  // ticker
  const tw = $('#tick');
  // booking line and years follow today's date: the quarter after this one, the current year
  const now = new Date(), q = Math.floor(now.getMonth() / 3) + 2, qy = now.getFullYear() + (q > 4 ? 1 : 0);
  const booking = `Now booking Q${q > 4 ? 1 : q} ’${String(qy).slice(2)} · 3 seats left`;
  $('span', tw).textContent = booking;
  $('#yr').textContent = $('#yr2').textContent = now.getFullYear();
  const fmt = () => new Intl.DateTimeFormat('en-GB', { hour: '2-digit', minute: '2-digit', timeZone: 'Europe/Lisbon' }).format(new Date());
  const msgs = [() => booking, () => `Studio time ${fmt()} Lisbon`, () => 'Recently: Shoal Atlas is live', () => 'Toys built this year: 214'];
  let mi = 0;
  setInterval(() => {
    const old = $('span', tw); mi = (mi + 1) % msgs.length;
    const nw = document.createElement('span'); nw.textContent = msgs[mi](); nw.style.transform = 'translateY(110%)'; tw.appendChild(nw);
    requestAnimationFrame(() => requestAnimationFrame(() => { old.style.transform = 'translateY(-110%)'; nw.style.transform = 'none'; }));
    setTimeout(() => old.remove(), 900);
  }, 3200);
  // reveals
  const io = new IntersectionObserver(es => es.forEach(e => { if (e.isIntersecting) { e.target.classList.add('in'); io.unobserve(e.target); } }), { rootMargin: '0px 0px -12% 0px' });
  $$('.rv,.fade,.pc').forEach(el => io.observe(el));
  // letter roll for footer
  const lets = $('#lets'); const txt = lets.textContent;
  lets.innerHTML = [...txt].map((c, i) => c === ' ' ? '<span class="ch sp"></span>' : `<span class="ch"><span data-c="${c}" style="transition-delay:${i * 18}ms">${c}</span></span>`).join('');
}
let lastSy = 0, dirAcc = 0;
function chromeTick(sy) {
  const ch = $('#chrome'), gauge = $('#gauge');
  // hide on the way down, return on the way up (never while the menu is open)
  const dy = sy - lastSy; lastSy = sy;
  if (Math.sign(dy) !== Math.sign(dirAcc)) dirAcc = 0;
  dirAcc += dy;
  if (sy < VH * .6 || document.body.classList.contains('menu-open') || dirAcc < -40) ch.classList.remove('hid');
  else if (dirAcc > 60) ch.classList.add('hid');
  const max = document.documentElement.scrollHeight - VH;
  const p = clamp(sy / max);
  $('#gnum').textContent = String(Math.round(p * 100)).padStart(3, '0');
  $('#gbar').style.transform = `scaleY(${p})`;
  gauge.style.opacity = smooth(VH * .3, VH * .7, sy);
  const fin = $('#fin'), ft = $('#contact');
  const ftop = fin.offsetTop - sy, fbot = ftop + fin.offsetHeight;
  const darkTop = ftop < 60 && fbot > 60;
  ch.classList.toggle('dark', darkTop);
  const gy = VH - 60;
  const fpanelTop = ft.offsetTop - sy;
  gauge.classList.toggle('dark', ftop < gy && fbot > gy && !(fpanelTop < gy));
}
```

## Loader
The shown value follows a target that the boot raises at real milestones, capped by elapsed time / 26 ms (so 100 takes at least
2.6 s) and closing 12% of the gap per frame; the digits redraw at most every 110 ms, each changed digit snapping to 100% below
and transitioning up (.32 s). Block n drops when the count passes 4, 29, 54, 79: 720 ms, falling in on an ease-in, overshooting
up 14 px with a slight stretch, squashing to .94 and settling. At 100: a 260 ms hold, the orange wipe scales up from the bottom
(520 ms), and 560 ms later the counter and blocks vanish, `onDone()` runs and the loader's own `clip-path` closes from the bottom
to the top over 780 ms, pulling the orange off the page; then it is removed.

```js
/* ======================= loader ======================= */
function runLoader(onDone) {
  const blks = $$('#loader .blk'), dg = $$('#loader .dg i'), wipe = $('#loader .lwipe'), L = $('#loader');
  let shown = 0, target = 0, t0 = performance.now(), done = false;
  const setDigits = v => { const s = String(v).padStart(3, '0'); dg.forEach((d, i) => { if (d.textContent !== s[i]) { d.style.transition = 'none'; d.style.transform = 'translateY(100%)'; d.textContent = s[i]; d.offsetWidth; d.style.transition = ''; d.style.transform = 'none'; } }); };
  const dropBlock = i => blks[i].animate([
    { transform: 'translateY(-60vh)', opacity: 1 }, { transform: 'translateY(0)', opacity: 1, offset: .62 },
    { transform: 'translateY(-14px) scaleY(1.04)', offset: .78 }, { transform: 'translateY(0) scaleY(.94) scaleX(1.05)', offset: .9 }, { transform: 'none', opacity: 1 }
  ], { duration: 720, easing: 'cubic-bezier(.5,0,.75,0)', fill: 'forwards' });
  let dropped = 0;
  window.__loadTarget = v => { target = Math.max(target, v); };
  (function lp() {
    const el = performance.now() - t0;
    const cap = Math.min(target, el / 26); // min ~2.6s
    if (cap > shown) shown = Math.min(Math.floor(cap), shown + Math.max(1, Math.round((cap - shown) * .12)));
    if (el - (window.__lastDig || 0) > 110 || shown >= 100) { window.__lastDig = el; setDigits(shown); }
    while (dropped < 4 && shown >= dropped * 25 + 4) { dropBlock(dropped); dropped++; }
    if (shown >= 100 && !done) {
      done = true;
      setTimeout(() => {
        wipe.animate([{ transform: 'scaleY(0)' }, { transform: 'scaleY(1)' }], { duration: 520, easing: 'cubic-bezier(.7,0,.2,1)', fill: 'forwards' });
        setTimeout(() => {
          $$('#loader > :not(.lwipe)').forEach(e => e.style.opacity = 0);
          onDone();
          wipe.style.transformOrigin = '50% 0';
          L.animate([{ clipPath: 'inset(0 0 0 0)' }, { clipPath: 'inset(0 0 100% 0)' }], { duration: 780, easing: 'cubic-bezier(.7,0,.2,1)', fill: 'forwards' }).onfinish = () => { L.style.display = 'none'; };
        }, 560);
      }, 260);
      return;
    }
    requestAnimationFrame(lp);
  })();
}
```

## Boot, the entrance and the one loop
The work grid, chrome and reel are wired first (no three.js needed); Lenis (`lerp: .1`) unless reduced motion; then the eight
modules are imported in parallel and the toy geometry built; any failure sets `nogl`. `__booted` tells the watchdog the module is
alive; each GL system boots in its own `try`. Loader targets: 20 at once, 45 after the fonts (or 2.5 s), 70 after the hero warm-up,
88 after the finale compiles, 100 when the first two grid images decode (or 1.5 s); patience forces 100 at 8 s. The entrance fades
the still out (.6 s), scales the window in from .94 over 1.4 s and replays the headline. One rAF loop steps Lenis, the hero, the
ribbons, the reel, the finale and the chrome, reading `window.scrollY` once.

```js
/* ======================= boot ======================= */
initWork(); initChrome(); initReel();
try { if (window.Lenis && !RM) { lenis = new Lenis({ lerp: .1, wheelMultiplier: 1 }); window.__lenis = lenis; } } catch (e) { }
scrollTo(0, 0);
let glOK = GL;
if (glOK) {
  try {
    const m = await Promise.all([
      import('three'),
      import('three/addons/geometries/RoundedBoxGeometry.js'),
      import('three/addons/environments/RoomEnvironment.js'),
      import('three/addons/postprocessing/EffectComposer.js'),
      import('three/addons/postprocessing/RenderPass.js'),
      import('three/addons/postprocessing/OutputPass.js'),
      import('three/addons/postprocessing/UnrealBloomPass.js'),
      import('three/addons/postprocessing/GTAOPass.js'),
    ]);
    THREE = m[0];
    ({ RoundedBoxGeometry } = m[1]); ({ RoomEnvironment } = m[2]); ({ EffectComposer } = m[3]); ({ RenderPass } = m[4]);
    ({ OutputPass } = m[5]); ({ UnrealBloomPass } = m[6]); ({ GTAOPass } = m[7]);
    makeGeo();
  } catch (e) { console.warn('three.js failed to load', e); glOK = false; document.documentElement.classList.add('nogl'); }
}
window.__booted = true;
// the watchdog already lifted the curtain onto the stills: stay on them
if (window.__lifted) glOK = false;
try { if (glOK) { initHero(); } } catch (e) { console.warn('hero gl failed', e); glOK = false; document.documentElement.classList.add('nogl'); }
try { if (glOK) initRibbons(); } catch (e) { console.warn('ribbon gl failed', e); }
try { if (glOK) initFinale(); } catch (e) { console.warn('finale gl failed', e); }
window.__loadTarget = window.__loadTarget || (() => {});
if (!window.__lifted) runLoader(() => {
  window.__lifted = 'loader'; window.__booted = true;
  document.body.classList.remove('locked');
  if (hero.ready) $('#win').classList.add('live');
  $('#win').animate([{ transform: 'scale(.94)', borderRadius: '40px' }, { transform: 'none' }], { duration: 1400, easing: 'cubic-bezier(.16,1,.3,1)' });
  $('.tab h1').classList.remove('in'); requestAnimationFrame(() => $('.tab h1').classList.add('in'));
});
// progress: fonts + hero warm + finale compile + first images
setTimeout(() => window.__loadTarget(100), 8000); // patience: never hold the curtain past ~8 s
(async () => {
  window.__loadTarget(20);
  try { await Promise.race([document.fonts.ready, new Promise(r => setTimeout(r, 2500))]); } catch (e) { }
  window.__loadTarget(45);
  try { if (hero.warm) hero.warm(); } catch (e) { }
  window.__loadTarget(70);
  await new Promise(r => setTimeout(r, 60));
  try { if (fin.warm) fin.warm(); } catch (e) { }
  window.__loadTarget(88);
  await Promise.race([Promise.all($$('#grid img').slice(0, 2).map(i => i.decode().catch(() => {}))), new Promise(r => setTimeout(r, 1500))]);
  window.__loadTarget(100);
})();

function frame(now) {
  if (lenis) lenis.raf(now);
  const sy = window.scrollY;
  if (hero.tick) hero.tick(now);
  if (rib.tick) rib.tick(sy);
  if (reel.tick) reel.tick(sy);
  if (fin.tick) fin.tick(sy, now);
  chromeTick(sy);
  requestAnimationFrame(frame);
}
requestAnimationFrame(frame);
addEventListener('resize', () => { VW = innerWidth; VH = innerHeight; });
</script>
</body>
</html>
```

## Copy
Every static string is in the markup above; set them exactly, including the title `Blockhaus: play-grade 3D studio`, the meta
description and the aria labels. Dynamic strings: the eight projects and their lines — `Mosswick` (Brand world · WebGL · Physics,
2026), `Shoal Atlas` (Data story · Real-time 3D · Sound, 2026), `Kilnfest ’26` (Festival identity · Motion · Web, 2025), `Owlhour
FM` (App launch · Interactive 3D, 2025), `Pip & Stride` (Product launch · Exploded 3D, 2025), `Foldfare` (Fintech · Illustration ·
Web, 2024), `Coin-Op Nocturne` (Game launch · Interactive, 2024), `Saltlight` (Fragrance · CGI film, 2024) — with `01 / 08`…`08 /
08` chips and `<name> key art` alt text; the ticker's four messages (`Now booking Q<n> ’<yy> · 3 seats left`, `Studio time HH:MM
Lisbon`, `Recently: Shoal Atlas is live`, `Toys built this year: 214`); the finale words `Every block` / `is a decision.` / `Stack
them with care` (set in caps by CSS), the count `NN / 58 blocks placed` and the title `Fifty-eight blocks.` / `Zero glue.`; the
current year in `© 2026 Blockhaus Play Studio` and `Every project, 2017–2026`. Blockhaus, its projects, the address `Unit 4, Cobble
Yard, 18 Rua do Forno Velho` and the `.play` emails are fictional; Lisbon and Hong Kong are real cities used as places.

## Phone (390px) and tablet
- ≤ 1024 px: the ticker hides; the grid's row gaps tighten (80 / 90).
- ≤ 900 px: both statements go to one column (the ribbon's empty left column becomes a 300 px spacer above the lead); the footer
  grid is two columns.
- ≤ 760 px (and the JS `PHONE` tier): radius 14; the chrome sits 20 px down in an 84 px bar, wordmark 24 px, `Start a project`
  hidden, the menu at 74 px and as wide as the screen less the gutters. The hero is `100svh` (min 560) with an 84 px top, the
  headline 30 px in its notch, the meta row only `Studio: Lisbon / Hong Kong`, no hint chips; the toybox has 34 bodies, no shadows,
  no GTAO, DPR ≤ 1.5, and FOV 50 in the portrait window. The statement indent drops; the ribbons follow their 390-board paths at
  62% width. The reel is 220vh: the card grows from 42vw × 1.25 to 72vh tall, the words start above and below it and ride to the
  corners 18 px in, the second meta line hides. The grid is one column at 4:3.4, the head stacks left; index rows are 76 px with
  the discipline hidden. The finale is 400vh with 150 storm toys, no bloom, 1024 shadows, FOV 52, the orbit 1.5× wider and the aim
  1.6 lower; its end title and caption stack. The footer is one column; the gauge shrinks to a 44 px bar at 12 / 16 px.
- Touch: a tap on the hero is a burst; a finger drag pushes the pile until the browser takes the vertical pan (`touch-action:
  pan-y` on the canvas); the play disc shows once the card is half grown and a tap opens the player.

## Failure, and the motion floor
- **No WebGL** (probed in the head and again in the module): `nogl` hides the hero canvas and its hint chips, leaving the designed
  hero still in the window, and gives the finale its still behind a visible end title (the caption still reads `00 / 58 blocks
  placed` and the kinetic words are never written); the ribbons never draw. The loader runs on its other milestones.
- **three.js fails to download**: the dynamic imports are caught, `nogl` is set, and the menu, ticker, reel, work grid, reveals and
  loader all keep working because they were wired before the import.
- **The watchdog**: a classic script in the head waits 10 s; if the module has not set `__booted` (the import hung, or the module
  never ran) and the loader has not lifted, it adds `nogl boot-fail`, fades the loader out, unlocks the scroll and marks itself, so
  the module, if it arrives late, stays on the stills. `.boot-fail` shows every line and fade that would have waited for a reveal.
- **The loader never waits forever**: the patience timer forces 100 eight seconds after the three.js imports settle. Each canvas
  renders only in view (hero within 80 px, finale within 100 px, ribbons while one is on screen).
- **Reduced motion**: Lenis is off and the line and fade reveals are shown at once with no transition. Everything else still runs
  — the loader, the falling pile and its physics, the ribbons and the scrubbed reel and finale (they follow the scroll, not a
  clock), the ticker, the pulsing dot, the scroll arrow and the finale grain.
- **No JavaScript**: nothing hides the loader, so it stays over the page.

## Assets (hosted, public, CORS-open — load them by these URLs)
Twenty files, none sampled by WebGL (every 3D surface is procedural), so none needs `crossOrigin` (the hosts send
`access-control-allow-origin: *` all the same); the finale still is a CSS background, the reel a plain `<video>`, the rest `<img>`.

- `https://www.vividsites.app/media/flagship/blockhaus/hero-still.jpg` — 1820 × 1010 JPEG (150 KB): the designed hero still, rendered from the
  toybox scene: a close crop of the glossy pile (orange bricks and capsules, bone rings, black cubes and rings, lilac blocks) on
  black, notch corner bottom-left. The window's `.still` and the no-WebGL hero; preloaded; fades out (.6 s) when the canvas is live.
- `https://www.vividsites.app/media/flagship/blockhaus/finale-still.jpg` — 2000 × 1250 JPEG (251 KB): the finished toy house amid the orbiting
  storm inside the orange and lilac halo on a dark floor. The `.nogl` background of the finale stage.
- `https://www.vividsites.app/media/flagship/blockhaus/reel-poster.jpg` — 1280 × 720 JPEG (58 KB): three clay arcade cabinets (orange, coral,
  lilac) with glowing screens, neon tubes and floating coins on a wet purple floor. The reel `<video>`'s `poster`.
- `https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/flagship/blockhaus/reel.mp4` — 1280 × 720 H.264
  (yuv420p, faststart), 30 fps, 26.0 s, no audio track (3.5 MB): six toy worlds in turn (the arcade cabinets, a floating sneaker,
  jellyfish over coral, glazed pots tumbling in a sunlit room, paper planes among clay clouds, a moss terrarium under a glass dome).
  The reel card's `src` (muted, looped, in view only) and the player's; with no audio track, the "unmuted" player is silent.
- The eight project key arts, two cuts each, built from `WORK_BASE` (`https://www.vividsites.app/media/flagship/blockhaus/work/`):
  `${WORK_BASE}${id}.jpg` is 1600 × 1194 (the grid card, lazy, `object-fit: cover` at scale 1.08) and `${WORK_BASE}${id}-s.jpg` is
  800 × 597 (the index peek; p2-s is also the ribbon rider and p5-s the tilted lab card):
  - Mosswick: `https://www.vividsites.app/media/flagship/blockhaus/work/p1.jpg` (86 KB),
    `https://www.vividsites.app/media/flagship/blockhaus/work/p1-s.jpg` (25 KB): a moss hill with a stone arch and orange mushrooms under a glass dome.
  - Shoal Atlas: `https://www.vividsites.app/media/flagship/blockhaus/work/p2.jpg` (117 KB),
    `https://www.vividsites.app/media/flagship/blockhaus/work/p2-s.jpg` (41 KB): glowing jellyfish over blue coral in an underwater diorama.
  - Kilnfest ’26: `https://www.vividsites.app/media/flagship/blockhaus/work/p3.jpg` (151 KB),
    `https://www.vividsites.app/media/flagship/blockhaus/work/p3-s.jpg` (51 KB): glazed jugs and vases in orange, cream and cobalt floating in a sunlit room.
  - Owlhour FM: `https://www.vividsites.app/media/flagship/blockhaus/work/p4.jpg` (81 KB),
    `https://www.vividsites.app/media/flagship/blockhaus/work/p4-s.jpg` (27 KB): a chrome crescent moon over a black turntable platter among glowing orbs.
  - Pip & Stride: `https://www.vividsites.app/media/flagship/blockhaus/work/p5.jpg` (82 KB),
    `https://www.vividsites.app/media/flagship/blockhaus/work/p5-s.jpg` (28 KB): a chunky orange, lilac and cream sneaker floating among soft blobs.
  - Foldfare: `https://www.vividsites.app/media/flagship/blockhaus/work/p6.jpg` (92 KB),
    `https://www.vividsites.app/media/flagship/blockhaus/work/p6-s.jpg` (34 KB): paper planes and boats among soft clay clouds in a pastel sky.
  - Coin-Op Nocturne: `https://www.vividsites.app/media/flagship/blockhaus/work/p7.jpg` (132 KB),
    `https://www.vividsites.app/media/flagship/blockhaus/work/p7-s.jpg` (48 KB): three clay arcade cabinets with neon tubes and coins.
  - Saltlight: `https://www.vividsites.app/media/flagship/blockhaus/work/p8.jpg` (136 KB),
    `https://www.vividsites.app/media/flagship/blockhaus/work/p8-s.jpg` (44 KB): a faceted glass perfume bottle with an orange cap on white sand by a stone ring.

Everything else (the toys, the physics, the ribbons, the house, the storm, the halo, the loader glyph, the notch, the grain and
every icon) is written in the file. The only other requests are General Sans from api.fontshare.com, JetBrains Mono from
fonts.googleapis.com, and Lenis and three.js from cdn.jsdelivr.net.

## Verify
- The loader counts 000 → 100 in rolling digits (never under 2.6 s, forced by 8 s after the imports) while four blocks drop and
  squash into the glyph at 4 / 29 / 54 / 79; the orange wipe rises and the curtain pulls up.
- The toys fall into the window as it scales in from .94; the pile overflows the frame, glossy next to matte, with soft shadows and
  contact darkening, and churns slowly. The cursor shoves and spins pieces and leans the camera; a drag ploughs a wider path; a
  click bursts the pile and the orange pieces flash lime and return; the pile always settles back.
- The notch is cut round the headline with smooth inverted corners at 1440 and 390. The header hides scrolling down and returns
  scrolling up; the ticker rolls every 3.2 s with the Lisbon time and next quarter; the menu closes on outside click or Escape.
- The first ribbon draws itself in as you scroll (un-draws scrolling back), flips once and carries the `Now playing: Shoal Atlas`
  card on its tip; the second loops through the lab statement.
- The reel card grows to the full window; "Show" and "reel" ride to opposite corners and are white exactly over the card; the play
  disc follows the cursor; the player opens on click and closes on Escape.
- The cards wipe up; hover zooms the art, shows the ↗ chip and slides the arrow; Index rows fill with ink and the peek shows each
  project's `-s` image from the base URL.
- The finale: the caps burst and fade; the pieces stack into the house as the counter climbs to 58 / 58 (scrolling back un-builds
  it); the storm orbits, the halo blooms, the title shows, the storm rushes and the orange flood fills the screen with no empty gap
  before the footer rises over it; the footer letters roll on hover.
- At 390 × 844: 34 bodies, no horizontal overflow, reel words above and below the card; no console errors at 1440 × 900 or 390 ×
  844. With WebGL disabled or three.js blocked the stills stand in; with the module blocked the watchdog lifts the loader at 10 s.
