Build a full-viewport, single-screen hero for a creative motion and brand studio called FLUX. It is a LIGHT, minimal, centered hero — bright, airy, confident, high-end, with a lot of whitespace. One clean motif: a soft flowing pastel liquid gradient video washed almost to white behind perfectly centered type. Deliver it as ONE self-contained HTML file — inline <style>, inline <script> if needed, Google Fonts via <link> in the head, no build step, no external assets except the fonts and the video. The whole page is a single 100vh hero — no scrolling. It must render perfectly at 1280x800 (it will be screen-recorded at that size).

THEME AND COLOR:

Light theme, bright and minimal. Background is pure white #ffffff. Primary text ("ink") is near-black #17151f. Muted body text around #6a6577, with a fainter meta gray #9a94a6. One accent color, a soft violet #7c6cff, used sparingly — the wordmark mark, the period in the headline, the kicker rules, and a faint bloom behind the H1. No dark overlays and no heavy scrims — this is a bright, clean page where the pastel video only bleeds in softly at the edges.

FONTS (Google Fonts) — MODERN SANS ONLY, no serif, no italic anywhere:

Display / headings / wordmark: Plus Jakarta Sans — a clean modern grotesk. Weights 400/500/600/700/800. Use it for the FLUX wordmark (800), the H1 (700), and all buttons (600).
Body / UI: Inter — weights 400/500/600, for the sub-line and nav links.
Mono label: IBM Plex Mono — weights 400/500, for the small kicker and the footer meta row.
Do NOT use any serif or italic type. Emphasis comes from color, weight, and the mono kicker only.

BACKGROUND VIDEO — SOFT AMBIENT WASH:

A single <video src="https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/flux.mp4" autoplay muted loop playsinline> fixed behind everything at z-index 0, object-fit: cover, filling the viewport. This is soft flowing pastel liquid gradient motion on white. Keep it soft and bright: apply filter: blur(2px) saturate(1.06) and transform: scale(1.06) so it reads as an ambient accent rather than a busy backdrop. It must autoplay, be muted, and loop seamlessly.

Over the video sits a fixed, pointer-events-none scrim div at z-index 1 that keeps the center bright and clean and only lets the pastel liquid bleed in at the edges:
  - A radial white wash centered around 50% 44%: rgba(255,255,255,0.94) at 0%, 0.80 at 30%, 0.46 at 58%, 0.20 at 100%.
  - Plus a vertical linear-gradient for nav/footer legibility: rgba(255,255,255,0.85) at top, transparent through the middle (18% to 82%), rgba(255,255,255,0.90) at the bottom.
  - A ::after on the scrim: a faint accent bloom behind the headline — a ~640px radial-gradient(circle, rgba(124,108,255,0.10), transparent 62%), centered around 50% 46%, softly blurred. This is the only brand color in the field.

LAYOUT — CENTERED MINIMAL:

The page content sits at z-index 2 in a full-height flex column with generous padding (about 26px top, clamp(28px,4vw,60px) sides, 28px bottom): nav at the top, the hero centered in the remaining space, and a small meta row pinned at the bottom.

Top — a clean navbar (flex, space-between, no border):
  - Left: wordmark "FLUX" in Plus Jakarta Sans 800, ~21px, letter-spacing -0.01em, ink. Precede it with a small 15px rounded-square "mark" filled with a violet gradient (linear-gradient(150deg,#a99bff,#7c6cff)) and a soft violet drop shadow.
  - Center/right: three plain text links — "Work", "Studio", "Contact" — Inter 500, 14px, muted ink, hover to full ink.
  - Far right: ONE dark pill CTA "Start a project" — ink background #17151f, white text, Plus Jakarta Sans 600, ~11px x 20px padding, fully rounded (999px), subtle lift on hover.

Middle — the hero, a flex column centered both horizontally and vertically, text-align center:
  - Mono kicker "MOTION & BRAND" — IBM Plex Mono 500, 12px, uppercase, letter-spacing 0.30em, muted ink, flanked left and right by short 26px violet rule lines (::before and ::after). ~30px bottom margin.
  - H1 "Make it move." — Plus Jakarta Sans 700, huge (clamp ~64px to 136px), line-height 0.92, letter-spacing -0.045em, ink. Render only the final period in the violet accent color (a <span class="dot">). No italic, no serif.
  - Sub-line "A studio for brands that refuse to sit still." — Inter 400, clamp ~17px to 20px, muted ink, max-width ~440px, ~40px bottom margin.
  - CTA row (flex, centered, ~26px gap): a dark pill button "See our work" (ink bg, white text, Plus Jakarta Sans 600, 15px x 30px padding, rounded 999px, expensive soft shadow, hover lift with the arrow sliding right) followed by a plain text link "Get in touch" in ink with a small violet arrow-chevron drawn via ::after that nudges on hover and turns the text violet.

Bottom — a small centered meta row (the tasteful extra): three labels in IBM Plex Mono, 11.5px, uppercase, letter-spacing 0.16em, faint gray — "Brand identity", "Motion design", "Film & CGI" — separated by tiny 4px violet dots. This grounds the composition and hints at the studio's disciplines without adding clutter.

MOTION — staggered blur-rise entrance:

Define a @keyframes blurRise: from { opacity:0; filter:blur(16px); transform:translateY(30px) } to { opacity:1; filter:blur(0); transform:translateY(0) }, applied over ~1s with cubic-bezier(0.2,0.7,0.2,1) and forwards fill. Give a .rise class opacity:0 and this animation, then cascade the elements with incrementing animation-delay:
  wordmark 0ms, nav links 70/120/170ms, nav CTA 220ms, kicker 300ms, H1 380ms, sub 490ms, CTA row 600ms, footer meta 720ms.
Wrap everything in @media (prefers-reduced-motion: reduce) that disables the animations, shows all elements at rest, and drops the video blur to just saturate.

Keep the loop alive with a tiny inline script: select the background video and call play() on its 'canplay' event and on window load (catch and ignore rejections), so it autoplays even if the browser defers it.

RESPONSIVE:

The design targets 1280x800 desktop. Under ~720px, hide the center nav links, stack the CTA row vertically, and scale the H1 down with clamp. The centered composition otherwise holds at any width.

VOICE:

Real, on-brand studio copy — confident, minimal, specific, not poetic. Keep everything already specified above verbatim. The overall feeling: a boutique motion-and-brand studio's homepage — bright, precise, quietly premium, with soft pastel motion breathing behind clean modern-sans type that does the talking.
