Build ORRERY — a landing page for an amateur observatory and astronomical society, with ninety thousand bodies on real Kepler orbits rendered in WebGL2 behind the whole document. ONE self-contained HTML file: inline <style>, inline <script>, fonts by <link>. Raw WebGL2, no three.js, no library. No image, video or mesh anywhere on the page.

═══ ⛔ THE SEVEN SILENT FAILURES ═══
1. A CONSTANT ANGULAR RATE. The single most obvious tell in an orbital scene: the outer band sweeps round with the inner one and nothing reads as gravity. Kepler's third law is one line — mean motion n = k / a^1.5 — and it is the difference between a system and a spinning disc.
2. SOLVING KEPLER'S EQUATION WITH TOO FEW ITERATIONS. Three Newton steps is visibly wrong above e ≈ 0.4: the body stutters through periapsis. Four is enough, and the STARTING GUESS matters more than the count — use E = M + e·sin(M).
3. THE ROTATION ORDER. Argument of periapsis, THEN inclination, THEN longitude of the ascending node. Any other order tilts the inclined band about the wrong axis and the whole system reads as a bowl.
4. A UNIFORM DISC. A belt with no gaps is a smear. Five bands with clear space between them is what makes it read as a system with a history.
5. A FLAT RANDOM INCLINATION. A real belt is bunched to the plane with thin wings. Use the sum of two uniforms, not one.
6. NO NEAR/FAR CUE. A face-on ring rendered with uniform alpha is a flat annulus. Fade the far half very slightly — smoothstep on the rotated z — and it becomes a disc.
7. A CSS FILTER ON THE CANVAS for the vignette. It forces a readback every frame. The vignette is a fixed radial-gradient layer over the top.

═══ THE SIMULATION ═══
There is no simulation state and no feedback buffer. Position is a PURE FUNCTION of (elements, time), so scrubbing time backwards is exact, the system can never drift, and the whole thing costs one draw call and one static buffer.
  N = 90 000 desktop · 45 000 tablet · 22 000 mobile · 14 000 reduced-motion
  aOrb1 = vec4(a, e, inc, node)   aOrb2 = vec4(peri, M0, n, seed)
  M = M0 + n·t
  E = M + e·sin(M);  four Newton steps of E −= (E − e·sin(E) − M) / max(0.15, 1 − e·cos(E))
  x = a·(cos E − e) ;  y = a·√(1 − e²)·sin E
  rotate by peri (in plane) → inclination about x → node about z
Five bands, weighted 0.16 / 0.24 / 0.30 / 0.14 / 0.16:
  a 0.9–1.35  e≤0.05 i≤0.030 · 1.7–2.35 e≤0.09 i≤0.055 · 2.9–3.9 e≤0.14 i≤0.090
  4.6–5.4 e≤0.10 i≤0.320 (the inclined one) · 6.3–8.6 e≤0.26 i≤0.240
  e = |u1 + u2 − 1| · band.e ;  inc = (u1 + u2 − 1) · band.i ;  n = 0.42 / a^1.5
Index 0 carries a negative seed and is the PRIMARY: pinned to the origin, twenty-six times the point size, near-white.

═══ THE DRAW ═══
gl.POINTS, additive (SRC_ALPHA, ONE), no depth test.
  gl_PointSize = uPx · (star ? 26 : 1 + big·3.4) · (26 / max(2, cp.w))     uPx = 0.62·DPR
  vA  = (0.20 + 0.55·fract(seed·13.7)) · (1 + big·2.2) · (0.62 + 0.38·smoothstep(−1.6, 1.6, −w.z))
  dust is cold blue-white shading to warm; roughly 1.5% of bodies are "big" and warm; the primary is the only white thing
  fragment: a tight core exp(−d·6.5) plus a wide halo exp(−d·1.7)·0.3, discard outside the disc

═══ THE FRAME ═══
DPR clamped twice: \`max(1, min(coarse?1.5:2, devicePixelRatio, sqrt(2_600_000/(w·h))))\`. Resize only when the size CHANGED.
ONE rAF loop, per-subscriber dt clamped to 0.05s.
SCROLLING RUNS THE CLOCK FASTER — dt × (0.85 + p·5.5) — rather than moving a camera down a page. The subject is time, and a reader going further down the almanac is a reader looking further ahead.
DRAG ROTATES THE SYSTEM, with inertia: yaw and pitch velocities decayed by pow(0.0016, dt), pitch clamped to [0.16, π−0.16], and the pitch easing back toward its scroll-driven rest when the pointer is up.
Hold the preloader open until the first frame is drawn, with a 5.2s patience.

═══ LAYOUT ═══
A CENTRED ALMANAC. The canvas is fixed at z-index 0, a vignette at 1, the page at 2 in a single 46rem column with NO panels anywhere — an observatory's printed matter is a column of dates and it should read like one. This is the deliberate opposite of a left-aligned WebGL landing page with bordered cards.
Bands: centred hero · a four-cell ephemeris rule · public nights (four dated entries) · instruments (three) · membership · footer.

═══ THE EPHEMERIS ═══
Computed, not written. Greenwich mean sidereal time from the visitor's clock:
  jd = Date.now()/86400000 + 2440587.5 ; T = (jd − 2451545)/36525
  gmst = 280.46061837 + 360.98564736629·(jd − 2451545) + 0.000387933·T², wrapped to 360, shown as hh:mm:ss
Moon phase from age = ((jd − 2451550.1) mod 29.530588853), named in eight steps and shown with the age in days. Seeing walks between about 1.0 and 2.1 arcseconds and updates every three seconds. An observatory page whose ephemeris is a static string is the one thing this audience notices first.

═══ TYPE ═══
Display: Amulya 400/500/700 — the hero at clamp(1.9rem, 4.3vw, 3.5rem) with line-height 1.24 and \`text-wrap: balance\`. It is five short lines, not two long ones.
Body: Supreme 400/500. Chrome and every read-out: JetBrains Mono 400/500.
  https://api.fontshare.com/v2/css?f[]=amulya@400,500,700&f[]=supreme@400,500&display=swap
  https://fonts.googleapis.com/css2?family=JetBrains+Mono:wght@400;500&display=swap

═══ COLOUR ═══
  void #05060b · paper #e8e6df · AMBER #ffcf7a · torch #e0563c · soft #7c7a86
The torch red is the colour of an observing lamp — the only light anybody is allowed to carry on that hill — and it appears on the eyebrow dot and the dates and nowhere else.

═══ COPY (verbatim) ═══
Nav: Public nights · Instruments — ORRERY — Join
Eyebrow  Founded 1841 · 220 m above sea level
H1  We have watched | the same sky | from the same hill | for a hundred | and eighty-five years
Sub An amateur observatory with two working refractors, one of them older than the building. Public nights every clear Friday, no charge, no booking, no telescope required.
CTA  Next clear Friday   Hint  Drag the sky
Ephemeris  Bodies tracked {N} · Sidereal {live} · Seeing {live} · Moon {live}
H2  If you can see | three stars, we | are open
    The dome opens at dusk and closes when the last person leaves, which in December is about nine and in June is about two in the morning. There is a kettle and there are no chairs.
  Fri 22 Aug 21:10 Saturn at opposition — Rings open to twenty-six degrees, the best they will be this decade. The 8-inch refractor will be on it all night.
  Fri 29 Aug 21:00 Double stars for beginners — Albireo, Mizar, and the one everybody argues about. Bring nothing; we will show you how to find them again from your garden.
  Fri 05 Sep 20:45 The Perseid tail — Past the peak and therefore worth watching, because there is nobody else on the hill.
  Fri 12 Sep 19:30 Lecture: parallax — How the first person to measure the distance to a star did it with a brass instrument and eleven months of patience.
H2  Two refractors | and a great | deal of brass
  I   The Cooke — An 8-inch Cooke refractor of 1888, on its original clock drive. It is the reason the society exists and it is still the best instrument on the hill. 203 mm · 2 900 mm · 1888
  II  The Grubb — A 5-inch Grubb from 1902, mounted on the south pier. Easier to point, easier to share, and the one every visitor actually looks through. 127 mm · 1 520 mm · 1902
  III The transit — A meridian transit instrument that has not been used in earnest since 1961 and is kept working out of stubbornness. 76 mm · 910 mm · 1874
H2  Eighteen pounds | a year, and a | key to the gate
    Members get the gate code, the observing log, and the right to be on the hill at three in the morning without explaining themselves to anybody.
Footer  dome@orrery.org · Beacon Hill, past the reservoir · Open when it is clear · Founded 1841 · Bortle 4

═══ ASSETS ═══
None.

═══ VERIFY BEFORE YOU CALL IT DONE ═══
1. Freeze time and read the angular position of one inner and one outer body a second apart: the inner must have moved further. If they move together, the third law is missing.
2. Drag: the system must keep turning after the pointer is released and settle, not stop dead.
3. Compare the sidereal read-out against any online GMST calculator — it must agree to within a few seconds.
4. Console clean · the preloader lifts on the first frame · no horizontal overflow at 390px · 60fps.
