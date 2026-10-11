Build DEEPFIELD — a one-screen studio site over a flooded stone chamber, where the type stays at the EDGES and the entire middle of the frame is left alone. No scroll. Nothing below. ONE self-contained HTML file: inline <style>, inline <script>, fonts by <link>. Real footage, no WebGL, no library.

═══ ⛔ THE SIX SILENT FAILURES ═══
1. FILLING THE MIDDLE. Every instinct will be to put something in the biggest, best-lit part of the shot. Do not. The light shaft, the fish and the sand ARE the content; the copy is a caption in the empty left third and an index in the bottom-right corner. A studio one-screener that fills its own frame reads as a splash page, and a splash page is what this shape is usually mistaken for.
2. A SCROLLING PAGE. `html, body { height:100%; overflow:hidden }`. There is no second section and there must not be one — the moment a scrollbar exists the promise is broken and the visitor spends the whole visit looking for what is below.
3. NO INDEX. Four named projects with disciplines and hairlines is the single detail that separates a studio site from a splash. It costs twenty lines and it is the difference. `Marisco Atlantic — Identity`, `Hydra Systems — Motion`, `Casa do Sal — Site`, `Nordkapp — Film`, under a `Selected / 2026` header row.
4. THE INDEX SITS ON THE CAUSTICS. The sand at the bottom-right is the brightest thing in the loop and it gets brighter as the loop plays — measured peak under that box is 0.153 at t=6.0s, not at t=0. Fix it in the SCRIM LADDER, with a fourth gradient — `radial-gradient(ellipse 52% 46% at 88% 97%, rgb(0 6 9/.86), transparent 82%)` — not with a box behind the text and not with a text-shadow. A shadow strong enough to fix a real contrast failure is visible as a shadow.
5. A DEFERRED MODULE THAT ONLY LISTENS FOR `loadeddata`. On a cached file it has already fired, and the page holds its poster forever at `readyState 4`. Check `readyState >= 2` too, plus a 2.6 s fallback. `play()` also rejects on iOS in Low Power Mode even when muted, and rejects rather than throws.
6. A POINTER PARALLAX THAT SNAPS. This page has no scroll, so the pointer is the only parallax it gets, and at `lerp 0.2` it reads as a mouse-follow gimmick. `0.045`, capped at 14px x and 11px y, with `scale(1.06)` on the video for headroom. Under `pointer: coarse` it does not exist at all.

═══ THE STACK ═══
```
z0  <video> position:fixed inset:0, object-fit:cover, scale(1.06), will-change:transform
z1  grade    #06283a, mix-blend-mode:soft-light, .60
z2  scrims   a six-stop EASED gradient from the LEFT (the copy's side, and only
             that side), a short top gradient for the nav, the corner radial from
             failure 4, then a vignette centred at 56% 50% — off-centre, because
             the subject is
z3  grain    inline SVG feTurbulence, .05, overlay. Dark navy water is where
             8-bit H.264 bands worst; this is the only fix that works
z4  chrome
```
No frame inset on this one — it is a window, and it goes to the edges.

═══ TYPE — sentence case, and deliberately not loud ═══
Switzer 400/500/600, one family, one `<link>`. The headline is `clamp(1.9rem, 4.1vw, 3.5rem)` at weight 500 with −.033em tracking, and it is *quiet* — this site earns its screen with the plate, not the type size. Nav links are 13.5px SENTENCE CASE, right-aligned as a group, with the mark on the far left and a status chip beyond them behind a 1px divider. Micro is 11px / .13em / uppercase and only the coordinates, the status and the index keys use it.

═══ PALETTE — out of the plate ═══
--ink #000405 · --paper #dceff2 · --accent #5cc6e0 · --mute paper 56% · --faint paper 34% · --line paper 13%.
The accent appears exactly four times: the mark's 9px square, the status dot, an index row's discipline on hover, and the focus ring. A fifth use makes it a brand colour instead of a light source.

═══ THE LAYOUT ═══
Nav 64px: `■ Deepfield` left · Work / Studio / Journal / Contact pushed right with `margin-left:auto` · `● Two slots — Q3` beyond a divider.
Left third, top at `clamp(120px, 21svh, 220px)`, max-width `min(34rem, 54vw)`:
  H1  Deep work for brands<br>that only get one look.
  Sub Deepfield is a four-person studio in Lisbon working in identity, motion, and the places the two meet. We take three projects a year.
  A solid paper pill, `See the work`, with a 13px arrow glyph. Solid, not ghost — a ghost button over moving footage is illegible for half the loop.
Bottom-right, `min(22rem, 44vw)`: the index. Rows shift `padding-left:9px` on hover over 220ms and the discipline goes accent. That is the only hover on the page.
Bottom-left: `38.7223° N · 9.1393° W`, tabular numerals.
Entrance once — 14px lift, 850ms, staggered nav .05 / h1 .20 / sub .30 / btn .38 / index .50 / place .56 — and then nothing on this page ever animates again.

═══ ASSETS ═══
https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/vb/deepfield/hero.mp4      1080p, 8.04s, locked-off
https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/vb/deepfield/hero-sm.mp4   720p for ≤900px
https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/vb/deepfield/poster.webp   frame 0 of hero.mp4

═══ SMALL SCREENS ═══
The 16:9 plate cropped to 390px loses two thirds of its width — `object-position:64% 46%` keeps the shaft. The whole scrim flips from left-directional to a bottom-up gradient, because the copy moves to the bottom. Nav links, status chip and coordinates all go; the index keeps three rows.

═══ VERIFY BEFORE YOU CALL IT DONE ═══
1. There must be no scrollbar and no scroll, at any viewport, ever.
2. Move the pointer fast to a corner and stop: the plate must still be easing when your hand has stopped.
3. Hide the index and sample the mean luma of its box at twelve points across the loop. Peak below 0.30. It will peak near t=6s, not at t=0.
4. Console clean · 0px horizontal overflow at 390px · the page still finishes with the mp4 blocked entirely.
