Build a full-viewport, single-screen AI-product hero for ROVE, a friendly AI trip planner. Build it as one self-contained HTML file — inline <style>, inline <script>, Google Fonts via <link> in the head, no build step and no external JS/CSS. The only external assets are the Google Fonts and one background illustration image. The whole page is a single 100vh hero with NO scrolling, designed to render perfectly at 1280x800 (it will be screen-recorded at that size).

ARCHETYPE — CENTERED AI-INPUT HERO:
A modern AI-product landing hero, everything centered on a warm cream page: real nav, big headline, sub-line, and a prominent glassy input-box card that is the star of the screen. Below the content, a full-bleed hand-drawn adventure-landscape illustration band sits along the bottom of the viewport, slowly drifting (ken-burns) so the whole card preview is quietly alive. Calm, warm, premium — like a well-made modern AI product, not busy or sci-fi. Lots of whitespace.

THEME + COLOR (warm LIGHT):
- Cream paper background: #f4ede1 (with a slightly deeper #efe5d5 for surfaces).
- Dark ink text: #2b241d, with a softer ink #6f6357 for secondary text.
- Single accent, a warm terracotta: #b5763f — used sparingly (the accent word "you?" in the headline, the kicker ticks, the compass-mark in the wordmark, the caret, chip dots).
- Hairline dividers/borders at rgba(43,36,29,.12).
- A faint warm ambient wash on the paper: two low-opacity terracotta radial gradients (top-center ~10%, top-right ~6%), fixed, pointer-events none, behind content.

FONTS (Google Fonts) — MODERN SANS ONLY, no serif, no italic anywhere:
- Display / headings / wordmark: Space Grotesk (weights ~400-700) — the H1 and the ROVE wordmark.
- Body / UI: Inter (400/500/600) — sub-line, nav links, buttons, chips, the typed placeholder.
- Tiny mono kicker: JetBrains Mono for the "AI TRIP PLANNER" label only.

BACKGROUND IMAGE (the motif — a warm hand-drawn adventure landscape):
- <img src="https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/rove.png"> inside a fixed .backdrop band pinned to the bottom of the viewport: left/right/bottom 0, height ~55vh, overflow hidden, pointer-events none, z-index 0.
- The image fills the band with object-fit:cover, object-position center 42%, transform-origin center 68%.
- SLOW KEN-BURNS: @keyframes scaling the image from scale(1.0) to scale(1.05) over ~22s ease-in-out infinite alternate (will-change:transform). This subtle drift is what keeps the card preview in motion.
- Melt the illustration up into the paper with a ::after cream gradient over the band: from solid #f4ede1 at top, ~.88 at 16%, ~.38 at 36%, fully transparent by ~60%, a faint ~.12 at the very bottom — so the top edge of the artwork dissolves into the page and the base stays legible.
- The page content sits above the band at z-index 2-3.

NAV (dark text on cream, z-index 3):
- Left: wordmark "ROVE" in Space Grotesk 700, letter-spacing ~.06em, preceded by a small terracotta compass/route mark (a stroked circle with an inner compass-needle diamond).
- Center/right: three plain links — Discover / Pricing / FAQs — soft ink, hover to full ink.
- Far right: a plain "Login" text link (ink, medium weight, hover fades), then ONE dark pill CTA "Plan my trip" (background #2b241d, cream text, small arrow icon) that lifts 1px on hover.

HERO (centered, flex column, vertically centered, text-align center, slight padding-bottom so it floats above the illustration):
- Mono kicker "AI TRIP PLANNER" (uppercase, letter-spacing ~.26em, soft ink) with a short terracotta tick line on BOTH sides.
- H1 in Space Grotesk semibold (~600), very large (clamp ~50-92px), line-height ~1.0, tight tracking -.035em: "Where should we" on line one, then "take you?" on line two with "you?" in solid terracotta #b5763f (upright, NOT italic, NOT serif).
- Sub-line in soft ink, ~18.5px, max-width ~560px: "Tell Rove where you're headed and what you love — get a trip built just for you."

THE INPUT-BOX CARD (the centerpiece — a glassy rounded search/prompt bar):
- Width min(700px,92vw), a flex row: [typed field] [upload icon button] [dark Plan-my-trip button], gap ~14px, padding 14px 14px 14px 22px, border-radius ~22px.
- Glassy warm surface: background rgba(255,251,244,.62), backdrop-filter blur(18px) saturate(1.2) (with -webkit- prefix), a 1px near-white top/inset highlight and a large soft drop shadow (0 24px 60px -28px rgba(43,36,29,.42)) so it reads as a floating frosted card on the cream paper.
- Field (flex:1, left-aligned, text truncates): a <span> that the JS types into, followed by a blinking terracotta caret (2px wide, ~19px tall, steps blink 1s). Placeholder-colored soft ink when empty, full ink while typing.
- Upload: a 42x42 square icon button, transparent with a hairline border, a paperclip/attach icon in soft ink; on hover a faint ink wash + darker border.
- Plan-my-trip button: a dark rounded button (#2b241d bg, cream text, ~14px radius) with an arrow icon that slides right on hover; lifts 1px on hover, soft shadow.

THE TYPEWRITER (the continuous motion of the card):
- A JS loop types and cycles three example prompts into the field, character by character, then deletes and moves to the next, forever:
  1. "A 5-day food tour of Tokyo, no crowds…"
  2. "A quiet week in the Dolomites, great hikes…"
  3. "Two weeks island-hopping Greece on a budget…"
- Typing ~42ms/char (add a little random jitter), hold ~1.9s at full phrase, delete ~22ms/char, ~0.3s pause between phrases, ~0.7s initial delay. Toggle the empty/placeholder color class when the string is empty. Use the "…" ellipsis character, not three dots.

THE ONE TASTEFUL EXTRA — suggestion chips:
- A centered row of three small frosted pill chips under the box (margin-top ~20px), each a terracotta dot + label: "Weekend escapes", "Food & wine trails", "Off the map". Frosted translucent cream, hairline border, soft ink text brightening on hover.

MOTION — staggered fade/blur-rise entrance:
- @keyframes fadeRise: from { opacity:0; filter:blur(12px); transform:translateY(26px) } to { opacity:1; filter:blur(0); transform:translateY(0) }, ~0.95s, cubic-bezier(.2,.7,.2,1), forwards, initial opacity 0.
- Stagger: wordmark 0ms, nav links 60/110/160ms, Login 200ms, CTA 250ms, then kicker 260ms, H1 340ms, sub 440ms, input box 540ms, chips 640ms.
- The ken-burns image drift and the typewriter run continuously after entrance.
- Respect prefers-reduced-motion: reduce — disable all entrance animation (show at rest), freeze the image at a static scale(1.03), stop the caret blink, and show the first full phrase in the field statically (no typing).

LAYOUT + RESPONSIVE:
- .page is a flex column, height 100vh, padding ~26px clamp(28-54px) 0, overflow hidden, z-index 2.
- .hero is flex-column centered (align + justify center), text-align center, padding-bottom ~8vh so the card floats clearly above the illustration band.
- Below ~1120px, reduce the H1 clamp and tighten nav gaps — but keep it a single non-scrolling screen at 1280x800.

THE BACKGROUND ILLUSTRATION (media/rove.png):
- A warm, hand-drawn adventure-landscape illustration: rolling hills, distant mountains, a winding trail/road, a couple of trees, soft sun — friendly and inviting, in the same cream/terracotta/sage palette. Painterly, gentle, no text, no hard horizon line at the very top (it dissolves into the cream). Composed so the interesting detail sits in the lower two-thirds where the band is fully opaque.

VOICE:
Confident, minimal, specific — a friendly AI trip planner. Warm cream paper, one terracotta accent, clean modern sans, one clear action (describe your trip → plan it). The living illustration and the typing prompt do all the talking; no poetry, no clutter.
