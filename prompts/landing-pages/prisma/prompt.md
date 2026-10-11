Build a premium cinematic website for PRISMA — "For the curious". Build it as ONE self-contained HTML file: inline <style>, inline <script>, Google Fonts via <link> in the head. No build step, no framework, no external JS/CSS. The only external assets are the Google Fonts and one background video.

STRUCTURE — a 100vh cinematic hero, then a short scrollable body:
Screen 1 is a full-viewport hero with the film behind everything. Below it, three calm sections scroll in: a three-card "what it is" grid, a full-width pull-quote, and a closing CTA + footer. The whole page must feel like one continuous piece, not a template.

ARCHETYPE:
A surreal, warm creative-collective hero. A full-bleed film of a small grassy cliff-island floating in a sea of golden sunset clouds — a lone figure with a glowing laptop, a tiny wooden hut, a leaning telephone pole — plays behind everything. The layout is deliberately asymmetric: an enormous wordmark anchors the bottom-left, a short paragraph and CTA sit bottom-right.

BACKGROUND VIDEO (fetch it from the cloud — do NOT ask the user to download anything):
<video class="bg-video" src="https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/prisma.mp4" autoplay muted loop playsinline></video>
position:fixed; inset:0; width:100%; height:100%; object-fit:cover; z-index:0.
Add a tiny JS fallback that calls video.play() on 'canplay' and on window load (catch and ignore rejections) so the loop always starts.

LEGIBILITY — two fixed layers over the film, never a flat dark box:
1. .scrim (z-index 1, pointer-events:none): a vertical gradient that is strongest at the very top (for the nav) and at the very bottom (for the footer strip), and nearly clear through the middle, PLUS a soft radial that darkens the outer edges so centered type stays crisp.
2. .vignette (z-index 2, pointer-events:none): inset box-shadow, roughly "inset 0 0 220px 70px" in the darkest base colour.

THEME + COLOR:
- Dark base: #0d0b09 (only shows before the video paints).
- Text: warm cream #f3efe6; soft rgba(243,239,230,.7); dim rgba(243,239,230,.46).
- Hairlines: rgba(243,239,230,.16).
- No coloured accent at all — the golden clouds in the film are the only colour. Keep every UI element cream or dark.

FONTS — modern sans only, NO serif, NO italic anywhere:
- Display / wordmark / headings: Inter Tight (500/600) — modern geometric sans, tight tracking. NO serif anywhere.
- Body / UI: Inter (400/500).
- Tiny mono: JetBrains Mono for the eyebrow labels and step numbers.

NAV:
A single centered row at the top: Our story / Collective / Workshops / Programs / Inquiries. No logo in the nav — the giant wordmark below IS the logo.

HERO:
- H1: Prisma*  — set ENORMOUS (clamp 72px to 196px), Inter Tight 500, line-height .86, letter-spacing -.045em, anchored to the bottom-left. The asterisk is a small superscript.
- Sub-line: "Prisma is a worldwide network of visual artists, filmmakers and storytellers — bound not by place or scene, but by a shared belief in the power of an unusual perspective."
- One CTA pill "Join the lab": translucent glass fill, 1px hairline border, backdrop-blur, with a small circular icon button on its right containing an arrow. On hover the pill lifts 2px and the circle rotates 45deg.
- Bottom strip: none — the hero is just the wordmark and the side column.

BELOW THE FOLD (three sections, same palette):
1. A section with a tiny mono eyebrow, a large heading, one lead line, then a 3-column card grid. Cards: 20px radius, 1px hairline border, faint translucent fill, a mono step number, a heading and two lines of copy:
  01 The residency — Six weeks, one idea, a room of people who will tell you the truth about it.
  02 The workshops — Small, hands-on, taught by people still doing the work, not talking about it.
  03 The archive — Every project, process file and dead end, open to the whole collective.
2. A full-width pull-quote band with a hairline top and bottom border, centered, large display type: “I came for the workshop. I stayed for the people who kept asking better questions.”
3. A centered closing section: heading "Come be curious." and the same CTA pill, then a footer row with the wordmark, a copyright line and three quiet links.

MOTION:
- Entrance: @keyframes blurFadeUp — from opacity 0, filter blur(18px), translateY(30px) to opacity 1, blur(0), translateY(0). 1s, cubic-bezier(.2,.7,.2,1), forwards. Apply via a .rise class with staggered animation-delay: nav items 0-290ms, H1 400ms, sub 560ms, CTA 700ms, bottom strip 860ms.
- Scroll reveals: below-the-fold blocks start at opacity 0 / translateY(26px) and transition in over .85s when an IntersectionObserver (threshold .14, rootMargin '0px 0px -8% 0px') fires. Unobserve after revealing.
- Respect prefers-reduced-motion: reduce — disable all entrance + reveal animation, show everything at rest, and remove hover transforms.

RESPONSIVE:
- Below 900px: hide the nav link row, collapse the card grid to one column, and stack the hero column.
- The hero must stay a single non-scrolling screen at 1280x800 (it will be screen-recorded at that size).

VOICE:
Calm, confident, specific. One clear promise, one clear action. No brochure copy, no paragraph soup — the film carries the emotion and the type stays quiet and deliberate.
