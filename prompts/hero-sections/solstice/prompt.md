Build SOLSTICE — a one-screen hero for a light-therapy lamp, with real arctic halo optics in raw WebGL2 behind a light poster. ONE self-contained HTML file: inline <style>, inline <script>, font by <link> (Albert Sans 300/400/600). No scroll. No three.js, no library, no image anywhere on the page.

═══ ⛔ THE SIX SILENT FAILURES ═══
1. A SEAM DOWN THE SUN LINE. Shading the snow with sign(uv.x − sunX) prints a hard vertical crease through the whole field the moment the sun moves. The direction factor must be SMOOTH: clamp((sunX − uv.x) · 4.0, −1.0, 1.0).
2. THE CLASSIC SCRIPT RACING THE SHADER TAG. If the main script runs before the fragment-shader <script type="x-shader"> is parsed, getElementById returns null and the page dies with "reading textContent of null". Load the main script as type="module" — modules are deferred by definition.
3. HALO AS LENS FLARE. A 22° halo is WEATHER, not optics-kitsch: its inner edge is faintly red (ice dispersion), its brightness peaks at the two horizontal sun-dog positions and at the upper tangent arc, and it must dim when the sun drops. A uniform white ring reads as a camera artefact.
4. BACKGROUND ON BOTH html AND body. Paint both and body stops propagating to the viewport, which buries a negative-z canvas completely. The clear colour goes on <html> alone.
5. AN UNCLAMPED DPR. Clamp by tier AND by area: dpr = min(devicePixelRatio, 1.6, sqrt(2.4e6 / (w·h))). A 5K display at 2x is not a place a background may spend 47 million fragments.
6. EASING TUNED AT 60 HZ ONLY. Every eased value uses k = 1 − pow(1 − base, dt·60), or the whole design is twice as stiff on a 120 Hz panel.

═══ THE SCENE — raw WebGL2, one full-screen triangle ═══
An arctic snowfield at polar dawn. Ice sky #eef2f6 → dawn gradient (#ffb45c → #e86a3a) pooled around the sun. Ink for type: #1d2530.
· Snow plane in perspective: z = k / (horizon − uv.y), carved by anisotropic fbm sastrugi (stretch x ~3:1), shaded by sun azimuth with the SMOOTH direction factor from failure 1.
· Hash-glint sparkle firing on its own clock — step(0.997, h21(cell + floor(t·2))) — snow answers light.
· Above the horizon: sun disc + gaussian glow; a 22° halo ring whose brightness = base + sunDog(azimuth ± 22°) + tangentArc(top); inner edge tinted #d96a4a; a vertical light pillar under the sun; two drifting ice-fog bands (1D fbm, screen-parallel).
· THE CURSOR IS THE SUN'S HAND: azimuth follows pointer x, elevation leans on pointer y, eased at base 0.06. The entire optics stack — dogs, arc, pillar, shading, sparkle — recomputes from the one sun vector. Nothing else listens to the pointer; one hand, one consequence.

═══ THE PRODUCT — CSS only ═══
A ring lamp floating centre: conic-gradient brushed aluminium rim, radial 10,000-lux core with three layered glows, a dial ON the rim edge (a real notch, not a floating dot), a short stand, an elliptical snow shadow that scales with the bob.
Composition law: the lamp sits ON the sun's screen position, so the sun dogs peek out either side of the product — the tagline made literal. It rises from below the fold on reveal (translateY, 900 ms, cubic-bezier(.16,1,.3,1)), bobs on a slow sine, tilts ≤ 3° toward the pointer.

═══ THE POSTER ═══
Header: dot logo + wordmark, frosted nav pill (Light / Science / Mornings / Order), "Order the lamp" button. Display headline top-left, two lines: "Winter, / optional." — 300 weight, then 400. Description column left (~28 words). Three feature lines right, bolded value first: "10,000 lux · zero UV / Sunrise ramp · 30 min / One dial · no app". CTAs bottom-left: dawn-gradient primary "Order — $189", ghost "The science". Outro display bottom-right: "The sun, / on your desk." A hairline divider EXACTLY on the scene's horizon line, with a mono chip under it: "10,000 LX · MEASURED AT 30 CM". ~85 words on the whole page.

═══ THE PRELOADER ═══
A lux meter: counts 0 → 10,000 LX against a dawn-gradient bar, mono digits, captioned "warming up". It counts something TRUE — gate the count on font load + first rendered frame, failsafe at 4 s. Exit: upward clip wipe, 700 ms.

═══ THE FLOOR ═══
prefers-reduced-motion: settled frame (sun frozen at its resting azimuth, lamp already risen, no bob, no count — the poster simply IS). No WebGL2 → the flat sky colour, never a black rectangle. Coarse pointers get the resting sun (no pointer listener at all). 0 px horizontal overflow at 390 px. Set window.__sceneReady = true when the preloader lifts.

═══ FIXED PARAMETERS ═══
sun rest azimuth 0.62 · halo radius 0.30 of min-axis · dog gain 2.2 · pillar width 0.012 · snow anisotropy 3:1 · sparkle rate step(0.997) · pointer ease 0.06 · lamp bob ±6 px @ 0.11 Hz · tilt max 3° · preloader count 1700 ms + 340 ms hold · reveal stagger 90 ms · dpr cap 1.6 / 2.4 MFrag · fps cap 60 desktop, 30 coarse.
