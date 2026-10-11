Build a full-viewport, single-screen editorial hero for STILLWATER, a calm platform for deep, focused work. Build it as one self-contained HTML file — inline <style>, inline <script>, Google Fonts via <link> in the head, no build step and no external JS/CSS. The only external assets are the Google Fonts and one background video. The whole page is a single 100vh hero with NO scrolling, designed to render perfectly at 1280x800 (it will be screen-recorded at that size).

ARCHETYPE — BRIGHT, AIRY EDITORIAL HERO OVER A NATURE FILM:
A serene product landing page. A full-bleed cinematic video of a lush green valley with a winding river plays behind everything; all UI sits on top in dark ink, centered. Think a high-end calm-productivity brand (Linear / Vercel restraint) laid over a painterly, sunlit landscape — spacious, quiet, one clear idea. Not busy, not sci-fi, not dark. The scene stays visible and bright; the type reads as ink over paper-light mist.

THEME + COLOR (dark ink over a bright green scene):
- Paper fallback behind the video: #f6f8f4 (only shows before the video paints).
- Text ink: deep forest-ink #16231b; soft rgba(22,35,27,.72); dim rgba(22,35,27,.52).
- Hairlines / borders: rgba(22,35,27,.16).
- Single accent, deep green #2f5d43 — used for the wordmark dot, the mono kicker text, and the solid dark CTA pill. Everything else is ink or paper.

FONTS (Google Fonts) — modern sans only, NO serif, NO italic anywhere:
- Display / headings / wordmark: Manrope (weights 400-800) — the H1, wordmark, CTA labels.
- Body / UI: Inter (400/500/600) — nav links, sub-line, ghost link.
- Tiny mono tag: JetBrains Mono for the kicker pill and the footer tag.

BACKGROUND VIDEO (the motif — a painterly green valley, a river winding through, soft daylight drifting):
- <video class="bg-video" src="https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/stillwater.mp4" autoplay muted loop playsinline>, position fixed, inset 0, width/height 100%, object-fit:cover, z-index 0.
- Add a tiny JS fallback that calls video.play() on canplay and on window load (catch and ignore rejections) so the loop always starts.

LEGIBILITY — a soft LIGHT scrim, never a heavy dark box (two fixed layers over the video):
1. .scrim (z-index 1, pointer-events none): a vertical PAPER-tinted gradient (all tints rgba(246,248,244,...)) that is soft-light at the very top (~.66 at 0%) for the nav, clears through the middle (~.06 at 34-66%), and returns soft-light at the bottom (~.58 at 100%) for the footer — plus a gentle center radial glow (rgba(246,248,244,.52) at center fading to 0 by ~72%) so the centered ink headline stays crisp over the bright valley. The point is to lift the scene toward paper-white exactly where text sits, never to darken it.
2. .blur-mask (z-index 2, pointer-events none): a light backdrop-blur(6px) masked to only the very bottom — mask-image: linear-gradient(to top, #000 0%, transparent 22%) with the -webkit- prefix — so the mono footer tag reads cleanly.

SHELL:
- .shell: position relative, z-index 10, height 100vh, flex column. Three rows: nav (top), hero (flex:1, centered), footer (bottom).

NAV (ink text on the bright scene):
- Left: wordmark "STILLWATER" in Manrope 800, letter-spacing ~.24em, preceded by a small 11px green dot with a soft ring halo (box-shadow 0 0 0 4px rgba(47,93,67,.16)).
- Center (absolutely centered, hidden below ~960px): four plain links — Product / Studio / About / Journal — soft ink, hover to full ink.
- Right: a plain "Sign in" text link (soft ink, hover full ink) + ONE solid dark-green pill "Begin" — rounded-full, forest-green #2f5d43 fill, cream text (#f2f6ef), soft green drop shadow + inset top highlight; lifts 1px and brightens to #356a4c on hover.

HERO — centered, vertically and horizontally, calm editorial rhythm:
- Mono kicker pill: JetBrains Mono, uppercase, letter-spacing ~.34em, green text, reading "A CALM HOME FOR FOCUSED WORK", with a small solid green dot before it. The pill has a faint green border (rgba(47,93,67,.26)) and a translucent paper fill with a light backdrop-blur.
- H1 in Manrope 700, very large (clamp ~56-108px), line-height ~.96, tight tracking (-0.045em), ink: "Built for deep work." — one line, upright, NOT italic, NOT serif, at most 7 words. Give it a soft paper text-shadow (0 2px 40px rgba(246,248,244,.55)) so it floats cleanly.
- Sub-line, Inter 400, ~17-20px, soft ink, max-width ~530px, centered: "A quiet place to think, make, and finish — one uninterrupted surface for the work that deserves your full attention."
- CTA row (centered, gap ~20px, wrap):
  - Primary solid dark pill "Begin" — Manrope 600, forest-green #2f5d43 fill, cream text, soft green glow shadow + inset top highlight, with a small arrow icon; lifts 2px and brightens on hover.
  - A secondary ghost text link "See how it works" with a small arrow that nudges right on hover — soft ink to full ink, no box.

FOOTER — the one tasteful extra:
- Centered at the very bottom: a tiny JetBrains Mono tag, uppercase, letter-spacing ~.30em, dim ink, reading "STILLWATER — DEEP WORK, UNDISTURBED", flanked left and right by a short 26px hairline rule.

MOTION — staggered blur-rise entrance (blurFadeUp):
- @keyframes blurFadeUp: from { opacity:0; filter:blur(20px); transform:translateY(36px) } to { opacity:1; filter:blur(0); transform:translateY(0) }, 1s, cubic-bezier(.2,.7,.2,1), forwards, initial opacity 0 via a .rise class.
- Stagger: wordmark 0ms; nav links 90/140/190/240ms; Sign in 290ms; Begin pill 340ms; kicker 440ms; H1 540ms; sub 680ms; primary CTA 800ms; ghost link 900ms; footer tag 1020ms.
- Respect prefers-reduced-motion: reduce — disable all entrance animation, show everything at rest (opacity 1, no blur/transform).

LAYOUT + RESPONSIVE:
- nav padding ~28px 48px; hero padding 0 32px 44px; footer padding 0 48px 30px.
- Below ~960px: hide the center nav links, tighten nav/hero/footer padding — but keep it a single non-scrolling screen at 1280x800.

VOICE:
Calm, confident, specific — a quiet home for focused makers. One clear promise (built for deep work), one clear action (begin), a restful premium tone over a living green valley. Everything on brand: deep-green accent, clean modern sans, dark ink floating over bright paper-lifted mist. No poetry, no fluff — just stillness with intent.
