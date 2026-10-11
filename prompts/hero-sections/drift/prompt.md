Build a full-viewport, single-screen landing hero for a boutique travel brand called DRIFT — hand-picked stays in quiet, out-of-the-way places. The whole page is one 100vh hero: a real nav at the top and the hero content anchored to the lower-left. No scrolling, no additional sections. It must render perfectly at 1280x800 (it will be screen-recorded at that size). Ship it as ONE self-contained HTML file: inline <style>, inline <script> only if needed, Google Fonts via <link> in the head, and one background video. No build step, no framework, no external JS/CSS/images beyond Google Fonts and the video.

BRAND + VOICE:

DRIFT is a boutique travel / stays company. The tone is calm, confident, and understated — an editorial travel brand, not a booking-engine deal site. Copy is minimal and specific: value-prop voice, not poetry. It should feel like a warm dusk at the end of a long flight — expensive, unhurried, a little cinematic.

BACKGROUND VIDEO:

A full-bleed background video sits fixed behind everything at z-index 0, object-fit:cover, width/height 100%. Source: https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/drift.mp4 with attributes autoplay muted loop playsinline. It must autoplay and loop seamlessly. The footage is a slow aerial glide over a coastline at golden hour — warm, dusky light, water and headland drifting past below the camera. Let it play at full opacity so the warmth carries the whole frame.

LEGIBILITY / SCRIM (no heavy black box):

Layer two fixed, pointer-events-none overlays above the video:
1. A scrim div (z-index 1) that keeps the sky clear but warms and darkens the lower-left corner where the text sits. Combine a corner radial — radial-gradient(130% 110% at 18% 96%, rgba(20,14,10,.86) 0%, rgba(20,14,10,.42) 34%, rgba(20,14,10,0) 62%) — with a gentle vertical gradient that darkens the very top and bottom bands: linear-gradient(to bottom, rgba(20,14,10,.42) 0%, transparent 24%, transparent 58%, rgba(20,14,10,.55) 100%). Everything uses the same warm near-black rgba(20,14,10) so the tint reads as dusk, never as a gray box.
2. A cinematic bottom blur mask (z-index 2): a full-screen div with backdrop-filter: blur(9px) (with -webkit- prefix) and a CSS mask so the blur only appears at the very bottom and fades out by ~45% up the screen — mask-image: linear-gradient(to top, #000 0%, transparent 45%) with the -webkit- prefix too. Blur only, no dark gradient inside this layer.

All hero content lives in a relative shell at z-index 10.

COLOR:

Warm near-black base #1a1410. Primary ink is a soft warm white #fbf7f0; muted text rgba(251,247,240,.72); dim caption rgba(251,247,240,.55); hairline borders rgba(251,247,240,.22). The single accent is a coastal teal #2aa9b8 — use it only for the mono kicker label and its short rule. Keep everything else warm-white on dusk.

FONTS (Google Fonts, modern sans only — no serif, no italic):

Manrope (400/500/600/700/800) for the wordmark, headline, nav CTA, and primary button. Inter (400/500/600) for nav links, the sub-line, and body. JetBrains Mono (400/500) for the kicker label and the tiny caption. Import all three via one <link>. Never use a serif display face and never italicize an accent word — emphasis comes from weight, color, and the mono kicker.

NAV (top, z-index 10):

Flex row, justify-between, padding ~28px 48px.
Left: wordmark DRIFT in Manrope 800, ~20px, letter-spacing .30em, full caps.
Center: three plain links in Inter 500 ~14px, muted warm-white, hover to full ink with a .25s color transition — "Stays", "Destinations", "Journal".
Far right: ONE CTA — a rounded-full outline pill "Plan a trip" in Manrope 600 ~14px: 1px hairline border rgba(251,247,240,.22) over a barely-there rgba(251,247,240,.04) fill with a 6px backdrop-blur. On hover, brighten the border to ~.5 and lift the fill to ~.09. Outline, not solid — it should feel quiet next to the wordmark.

HERO (anchored lower-left, fills remaining space):

The hero column grows to fill the space and pins its content to the bottom-left: align-items flex-start, justify-content flex-end, padding ~0 48px 58px.
- Kicker: JetBrains Mono ~12.5px, weight 500, letter-spacing .40em, uppercase, color teal #2aa9b8 — text "QUIET ESCAPES". Precede it with a short 34px teal rule (a ::before hairline) sitting on the baseline, ~14px gap. ~24px bottom margin.
- H1: Manrope 700, clamp(58px, 9vw, 118px), line-height ~.94, letter-spacing -0.045em, warm-white, max-width ~12ch, a soft text-shadow (0 2px 40px rgba(0,0,0,.35)) so it holds over the brighter water — text "Go somewhere quiet." (plain modern sans, no italic, no serif). ~26px bottom margin.
- Sub: Inter 400, clamp(17px, 1.5vw, 20px), muted warm-white, max-width ~440px, line-height 1.5 — text "Hand-picked stays in places worth the flight." ~36px bottom margin.
- Actions row (align items center, gap ~22px, wrap):
  (a) Primary CTA "Explore stays" — a rounded-full SOLID warm-white button: Manrope 600 ~15px, color #12100d, background #fbf7f0, soft drop shadow 0 12px 34px -10px rgba(0,0,0,.5), with a small right-arrow SVG icon. On hover lift 2px and deepen the shadow.
  (b) A tiny caption alongside it in JetBrains Mono ~12px, dim warm-white, letter-spacing .14em, uppercase — text "DRIFT · 40 DESTINATIONS". It's a quiet trust mark, not a button.

ENTRANCE MOTION (staggered blur-rise):

Define @keyframes blurFadeUp — from { opacity:0; filter:blur(20px); transform:translateY(40px) } to { opacity:1; filter:blur(0); transform:translateY(0) }. A .rise class applies animation: blurFadeUp 1s cubic-bezier(.2,.7,.2,1) forwards with initial opacity:0; each element gets a staggered animation-delay via inline style. Suggested cascade: wordmark 0ms; nav links 90/140/190ms; Plan-a-trip pill 280ms; kicker 400ms; H1 500ms; sub 640ms; primary CTA 760ms; caption 880ms. Everything blurs up into place once, then rests.

REDUCED MOTION:

Wrap all motion in a @media (prefers-reduced-motion: reduce) guard that disables the blurFadeUp animation (elements start at opacity:1).

RESPONSIVE:

Below ~860px, hide the center nav links (keep wordmark + Plan-a-trip pill) and tighten nav and hero padding. The design is tuned for 1280x800 desktop first — that's the framing that must look perfect.

OVERALL FEEL:

A slow golden-hour coastline drifting past, one big calm modern-sans headline pinned low-left, a single teal kicker, an outline nav CTA and a solid warm-white button. Warm dusk with one coastal-teal accent. Understated, editorial, expensive — nothing decorative that isn't earning its place.
