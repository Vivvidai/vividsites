Build a full-viewport, single-screen cinematic hero for a home-solar / clean-energy brand called HELIO. It is a LIGHT, warm, editorial hero — bright, confident, and premium, built around ONE clean motif: a full-bleed aerial video gliding over rooftop solar panels at golden hour, with the headline set lower-left over a soft light scrim. Deliver it as ONE self-contained HTML file — inline <style>, inline <script>, Google Fonts via <link> in the head, no build step and no external assets except the fonts and the video. The whole page is a single 100vh hero — no scrolling. It must render perfectly at 1280x800 (it will be screen-recorded at that size).

THEME AND COLOR:

Light, warm theme. There is NO card and NO dark overlay — the golden-hour footage carries the whole frame and stays visible. Warm near-black ink #1d150c for text, muted ink at ~70% opacity for the sub-line, and a single warm accent, amber #f5a623, used for the primary CTA, the kicker rule, and small marks. The scrim color is a warm cream #fbf5ec. Keep it bright and airy — this is a light page, never a dark one.

FONTS (Google Fonts) — MODERN SANS ONLY, no serif, no italic anywhere:

Display / wordmark / H1: Manrope — weights 500/600/700/800. Use 800 for the headline and wordmark.
Body / sub-line / nav links: Inter — weights 400/500/600.
Small mono kicker and stat: JetBrains Mono — weights 500/600.
Do NOT use any serif or italic type. Emphasis comes from weight, color, and the mono kicker — never from an italic accent word.

BACKGROUND VIDEO (full-bleed):

A single <video src="https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/helio.mp4" autoplay muted loop playsinline> fixed to the viewport, width/height 100%, object-fit: cover, z-index 0, behind everything. It must autoplay, be muted, and loop seamlessly. Content is an aerial glide over rows of rooftop solar panels at golden hour.

LEGIBILITY — LIGHT SCRIM, NO DARKENING:

Three fixed, pointer-events-none, z-index 1 layers sit over the video (never a dark overlay):
  1. scrim-bottom: a warm cream gradient rising from the bottom — linear-gradient(to top, rgba(251,245,236,.97) 0%, rgba(251,245,236,.82) 16%, rgba(251,245,236,.30) 38%, rgba(251,245,236,0) 56%). This is the light base the lower-left text sits on.
  2. blur-bottom: a backdrop-filter: blur(10px) layer (with -webkit- prefix) masked so the blur only appears at the very bottom — mask-image: linear-gradient(to top, #000 0%, #000 10%, transparent 40%) (and -webkit-mask-image). It lifts the text area subtly without adding any color.
  3. scrim-top: a faint cream wash under the nav — linear-gradient(to bottom, rgba(251,245,236,.60), transparent 20%) — just enough to keep the nav legible over the bright sky.

LAYOUT:

A relative z-index-10 page shell at 100vh, flex column, padding ~24px top / clamp 28–60px sides / ~38–58px bottom.

Top — a clean navbar (flex, space-between, light chrome, no border):
  - Left: wordmark "HELIO" in Manrope 800, ~22px, ink, preceded by a small ~15px amber "sun" dot — a circle with a radial highlight (radial-gradient(circle at 38% 34%, #ffd27a, #f5a623 70%)) and a soft 3px amber halo ring.
  - Center/right: three plain links — "Panels", "Savings", "Install" — Inter 500, 14px, ink at ~70%, hover to full ink.
  - Far right: ONE light-glass pill CTA "Get a quote" — translucent white background rgba(255,255,255,.55), 1px white-ish border, backdrop-blur(10px), ink text, inset white highlight + soft shadow, subtle lift on hover.

Below the nav — the hero fills the remaining height as a flex column, justify-content flex-end, align-items flex-start, so all content stacks at the LOWER LEFT:
  - Mono kicker "HOME SOLAR" — JetBrains Mono 500, 12px, uppercase, letter-spacing 0.30em, ink, preceded by a 26px amber rounded rule. ~22px bottom margin.
  - H1 "Power from the sun." — Manrope 800, huge clamp(60px → 124px), line-height 0.92, letter-spacing -0.035em, ink, max-width ~14ch. No italic, no serif, no highlighted word. ~24px bottom margin.
  - Sub-line "Cut your bill to zero with rooftop solar." — Inter 400, ~18–21px, muted ink, max-width ~38ch. ~34px bottom margin.
  - Actions row: primary amber pill "See your savings" (background #f5a623, ink text #1d150c, Manrope 700, ~15/28px padding, rounded 999px, amber glow shadow + inset white highlight, with a right-arrow SVG that nudges right and a -2px lift on hover) + a secondary text link "How it works" with a thin ink underline that darkens on hover. ~30px bottom margin.
  - Stat row (the tasteful extra): JetBrains Mono 500, ~13px, muted ink — "25-yr warranty" · "$0 down" — with the numbers ("25-yr", "$0") in bolder ink and a small amber dot as the separator.

MOTION — staggered blur-rise entrance:

Define @keyframes blurRise: from { opacity:0; filter:blur(18px); transform:translateY(34px) } to { opacity:1; filter:blur(0); transform:translateY(0) }, applied ~1s with easeOutExpo (cubic-bezier(0.16,1,0.3,1)) and forwards fill, initial opacity 0. Give each element an incrementing animation-delay so they cascade in:
  wordmark 0ms, nav links 70/120/170ms, nav CTA 230ms, kicker 340ms, H1 440ms, sub 560ms, actions 680ms, stat 800ms.
Wrap everything in @media (prefers-reduced-motion: reduce) that disables the animations and shows all content at rest.

Add a tiny inline <script> that calls video.play() on 'canplay' and on window 'load' (catching rejections) so the loop starts even if autoplay is deferred.

RESPONSIVE:

Target 1280x800 desktop. Under ~720px, hide the center nav links, let the H1 shrink with clamp (down to ~46px), and let the actions row wrap. The lower-left composition and full-bleed video hold at every size.

VOICE:

Real, on-brand home-solar copy — confident, plain, and specific (value-prop voice, not poetry). Keep all copy above verbatim: kicker "HOME SOLAR", H1 "Power from the sun.", sub "Cut your bill to zero with rooftop solar.", primary CTA "See your savings", nav CTA "Get a quote", stat "25-yr warranty · $0 down". The overall feeling: a modern, trustworthy solar company's homepage — bright, warm, and premium, with golden-hour footage doing the selling.
