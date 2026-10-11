Build a full-viewport, single-screen brand hero for HAVEN, an AI journaling / calm-mind app. Build it as one self-contained HTML file — inline <style>, inline <script>, Google Fonts via <link> in the head, no build step and no external JS/CSS. The only external assets are the Google Fonts and one full-bleed background video. The whole page is a single 100vh hero with NO scrolling, designed to render perfectly at 1280x800 (it will be screen-recorded at that size).

ARCHETYPE — MINIMAL CALM HERO OVER FULL-BLEED VIDEO:
A serene, centered/lower-aligned hero floating over a cinematic full-bleed background video of a misty dawn lake. Generous whitespace, soft light text over the calm scene, one quiet accent. Nothing busy, nothing sci-fi — this should feel like a breath: still, confident, premium.

THEME + COLOR:
- The video IS the background — a misty dawn-lake scene, calm water and soft light. Text sits light over it.
- Light text on the scene: near-white #f4f8fb, with softer tints rgba(244,248,251,.72) and .60 for secondary text and captions.
- Single accent, a soft blue #7fb0d9 — used sparingly (the primary CTA, the kicker tick lines, a faint bloom of light).
- Page fallback background #0e1620 (deep calm blue-black) behind the video before it loads.

FONTS (Google Fonts) — modern sans only, NO serif, NO italic anywhere:
- Display: Manrope (weights ~400-700) — wordmark and H1.
- Body / UI: Inter (400/500) — sub-line, links, buttons text.
- Tiny mono kicker/caption: JetBrains Mono (400/500).

BACKGROUND VIDEO (the motif — a cinematic misty dawn lake):
- <video src="https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/haven.mp4" autoplay muted loop playsinline>, position fixed, inset 0, width/height 100%, object-fit:cover, z-index 0 behind everything.
- Add a tiny JS fallback that calls video.play() on canplay and on window load (catch and ignore rejections) so the loop always starts.

LEGIBILITY — soft light scrim, never a heavy black overlay:
- A fixed pointer-events-none scrim (z-index 1) over the video: a gentle vertical gradient that is slightly darker at the very top (~.30 of #0e1620 for nav legibility), nearly clear through the middle (~.04-.05), and softly deeper at the bottom (~.46) where the CTA and caption sit, plus a soft radial darkening low-center. Keep the calm scene bright — this is a whisper, not a mask.
- Add a faint accent light bloom: a fixed radial-gradient of the soft blue #7fb0d9 at ~.14 opacity around the upper-center, mix-blend-mode:screen, to warm the mist.

NAV (light text on the scene, z-index 2):
- Left: wordmark "HAVEN" in Manrope 700, wide letter-spacing (~.22em), a soft text-shadow for legibility.
- Center/right: three plain links — App / Science / Pricing — in soft light, hover to full white.
- Far right: ONE soft pill CTA "Start free" — a near-white frosted pill (rgba(244,248,251,.94)) with dark blue-ink text (#12222f), Manrope 600, soft shadow and inner top highlight; lifts 1px on hover.

HERO — centered, aligned to the LOWER portion of the screen (justify-end, text-center), generous whitespace:
- Mono kicker (uppercase JetBrains Mono, letter-spacing ~.34em, soft light) reading "DAILY REFLECTION", flanked by short soft-blue tick lines on both sides.
- H1 in Manrope semibold (~600), large (clamp ~52-104px), line-height ~1.0, tight tracking (~-.035em), near-white with a soft shadow: "A calmer mind, daily." — upright, modern sans, NOT italic, NOT serif.
- Sub-line in soft light (~17-20px), max-width ~520px, centered: "A few quiet minutes with an AI that listens and helps you reflect."
- CTA row (centered, gap ~26px): a soft-blue pill button "Start free" (#7fb0d9 bg, dark blue-ink text, arrow icon that slides right on hover, soft blue glow shadow) followed by a quiet text link "How it works" with a small arrow (soft light, hover to white).

THE ONE TASTEFUL EXTRA — a tiny caption:
- Pinned near the very bottom, centered: mono, uppercase, letter-spacing ~.28em, dim light: "HAVEN · 3 MIN A DAY".

MOTION — staggered blur-rise entrance:
- @keyframes blurRise: from { opacity:0; filter:blur(16px); transform:translateY(28px) } to { opacity:1; filter:blur(0); transform:translateY(0) }, ~1.05s, cubic-bezier(.2,.7,.2,1), forwards, initial opacity 0.
- Stagger: wordmark 0ms, links 70/120/170ms, nav CTA 220ms, then kicker 320ms, H1 420ms, sub 540ms, actions 660ms, caption 800ms. The slow, drawn-out cadence should feel calm, not snappy.
- Respect prefers-reduced-motion: reduce — disable all entrance animation and show everything at rest.

LAYOUT + RESPONSIVE:
- .page is a relative flex column (z-index 2), height 100vh, padding ~28px clamp(28-56px) 34px, overflow hidden on body.
- The hero flexes to fill, aligning its content to the bottom with padding-bottom ~clamp(20px,7vh,64px); the caption pins to the very bottom via a small footer row.
- Below ~720px, hide the center nav links and stack the CTA row — but keep it a single non-scrolling screen at 1280x800.

VOICE:
Calm, confident, minimal, specific — not poetry. Every element on brand: a still misty scene, light text, one soft-blue accent, clean modern sans, one clear promise (a calmer mind in a few minutes a day) and one clear CTA.
