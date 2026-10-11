Build a full-viewport, single-screen mindfulness landing hero for an inner-growth brand called ASCEND. The whole page is one 100vh hero: a real nav across the top and a centered editorial block below, composed over a large black-and-white halftone illustration of two hands reaching toward each other. No scrolling, no additional sections. It must render perfectly at 1280x800 (it will be screen-recorded at that size). Ship it as ONE self-contained HTML file: inline <style>, inline <script> only if needed, Google Fonts via <link> in the head, and one local image. No build step, no framework, no external JS/CSS beyond Google Fonts and that image.

BRAND + VOICE:

ASCEND is a mindfulness and inner-growth space — a calm daily practice for a steadier mind. The tone is quiet, aspirational, and premium; the type is crisp modern sans, never curly or "bookish". Copy is minimal and specific — a calm value-prop voice, not poetry. The feeling is off-white paper, dark ink, and a lot of negative space: still, spacious, expensive.

THEME — LIGHT MINIMAL:

This is a LIGHT design. Base is off-white #f4f3ef fading toward #eceae3 at the bottom; all primary text is dark ink #191b1e. There is NO video and NO dark scrim — light sites never get a heavy black overlay. Depth comes from a soft layered backdrop only:
- A fixed backdrop div (z-index 0): the off-white vertical gradient plus two faint radials — a barely-there slate bloom in the center, radial-gradient(120% 90% at 50% 40%, rgba(92,107,120,.09), transparent 52%), and a faint ink shadow along the bottom edge.
- A fixed grain div (z-index 1, opacity ~.35): a 4px radial-dot pattern at rgba(25,27,30,.05), masked with a centered radial so it only reads as faint paper texture, never a visible grid.
All hero content sits in a relative shell at z-index 10.

THE IMAGE (large centerpiece behind the headline):

Reference https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/ascend.png — a black-and-white halftone illustration of two hands reaching toward each other, one entering from the left edge and one from the right, fingertips reaching toward the centered text (a calm, Creation-of-Adam-style gesture). Place it fixed and centered, width ~min(1180px, 96vw), translate(-50%,-50%) at left:50% top:52%, at z-index 2 — BEHIND the text, spanning the full width so the hands enter from both edges. Apply mix-blend-mode: multiply and opacity ~.92 so the white of the halftone drops out and the illustration sits directly on the off-white paper (no white box). The empty gap between the fingertips is where the headline lives.

LEGIBILITY BLOOM (keeps centered text crisp):

Add a fixed .art-glow div at z-index 3 (above the art, below the shell), centered, width ~min(760px, 80vw), aspect-ratio ~1.5, filled with radial-gradient(ellipse at center, rgba(244,243,239,.92) 0%, rgba(244,243,239,.62) 34%, transparent 66%). It lifts the headline off the halftone at the very center without any dark overlay.

SLOW MOTION ON THE ART (this is the signature — keep it gentle):

The <img> runs a single slow ken-burns @keyframes kenburns from scale(1) to scale(1.04) over ~22s, infinite, alternate, transform-origin ~50% 48% — so a card preview of the page is always subtly moving. Layer a one-time softIn fade (opacity 0 to .92 over ~1.6s) on top via a comma-separated animation. Add will-change: transform. Keep it slow and calm; nothing snappy.

COLOR:

Off-white base #f4f3ef / #eceae3. Ink #191b1e for the headline and the button fills. Muted body text rgba(25,27,30,.62); dim rgba(25,27,30,.42); hairline borders rgba(25,27,30,.12). The single accent is a calm slate #5c6b78 — use it only for the mono kicker + its rules, the wordmark mark, and the backdrop glow. Everything else is ink-on-paper.

FONTS (Google Fonts, modern sans only — no serif, no italic, ever):

Manrope (400/500/600/700/800) for the wordmark, H1, nav CTA, and button. Inter (400/500/600) for nav links, the sub-line, and body. IBM Plex Mono (400/500) for the kicker and the corner captions. Import all three via one <link>. Never use a serif display face (no Fraunces / Playfair / Instrument Serif / DM Serif) and never italicize an accent word — emphasis comes from weight, color, and the mono kicker.

NAV (top, z-index 10):

Flex row, justify-between, padding ~30px 56px.
Left: wordmark ASCEND in Manrope 800 ~20px, letter-spacing .05em, preceded by a small ~17px slate ascending-chevrons SVG mark (two stacked upward chevrons, stroke currentColor), ~11px gap.
Center: four plain links in Inter 500 ~14.5px, muted ink, hover to full ink with a .25s color transition — "Home", "Practice", "Explore", "Help".
Far right: ONE CTA — a rounded-full SOLID dark pill "Begin" in Manrope 600 ~14.5px: off-white text on ink #191b1e fill, soft shadow 0 10px 26px -12px rgba(25,27,30,.5). On hover lift 1px and deepen the shadow.

HERO (centered, vertically centered, fills remaining space):

A flex column, align-items center, justify-content center, text-align center, padding ~0 24px 30px.
- Kicker: IBM Plex Mono ~12px, weight 500, letter-spacing .4em, uppercase, slate #5c6b78 — text "INNER GROWTH". Flank it with two short 28px slate hairline rules (::before and ::after), ~14px gaps. ~30px bottom margin.
- H1: Manrope, clamp(46px, 6.4vw, 88px), line-height 1.0, letter-spacing -0.04em, ink. TWO lines as block spans: line 1 in weight 400 at rgba(25,27,30,.82) — "Reach toward something higher,"; line 2 in weight 800 full ink — "and grow into what's next." (write your own original aspirational copy in this spirit; plain modern sans, no italic, no serif.) ~30px bottom margin.
- Sub: Inter 400, clamp(16px, 1.35vw, 19px), muted ink, max-width ~480px, line-height 1.55 — text "A daily practice for a steadier mind — breathe, reflect, and return to center, one quiet moment at a time." ~40px bottom margin.
- Primary CTA "Enter the space" — a rounded-full SOLID ink button: Manrope 600 ~15.5px, off-white text, background #191b1e, soft shadow 0 14px 34px -12px rgba(25,27,30,.45), with a small right-arrow SVG icon. On hover lift 2px and deepen the shadow.

CORNER CAPTIONS (fixed, z-index 11, bottom ~30px):

Two small IBM Plex Mono labels ~11.5px, letter-spacing .12em, uppercase, dim ink rgba(25,27,30,.42).
- Bottom-left (left:56px): "Stillness starts within."
- Bottom-right (right:56px): "Scroll to discover" followed by a small down-arrow SVG (~13px, opacity .7).

ENTRANCE MOTION (staggered blur-rise):

Define @keyframes blurFadeUp — from { opacity:0; filter:blur(20px); transform:translateY(38px) } to { opacity:1; filter:blur(0); transform:translateY(0) }. A .rise class applies animation: blurFadeUp 1s cubic-bezier(.2,.7,.2,1) forwards with initial opacity:0; each element gets a staggered animation-delay via inline style. Suggested cascade: wordmark 0ms; nav links 90/140/190/240ms; Begin pill 320ms; kicker 480ms; H1 600ms; sub 760ms; Enter-the-space CTA 880ms; both corner captions 1040ms. Everything blurs up into place once; then the art keeps its slow ken-burns forever.

REDUCED MOTION:

Wrap all motion in a @media (prefers-reduced-motion: reduce) guard that disables the blurFadeUp entrance AND the ken-burns loop (elements start at opacity:1, the art holds still at opacity .92).

RESPONSIVE:

Below ~960px, hide the center nav links (keep wordmark + Begin pill) and the corner captions, widen the art to ~150vw so the hands still frame the text, and tighten nav padding. The design is tuned for 1280x800 desktop first — that's the framing that must look perfect.

OVERALL FEEL:

Off-white editorial paper with generous negative space, a big calm two-weight modern-sans headline centered in the gap between two reaching halftone hands, one slate mono kicker, a dark pill nav CTA and a solid ink button — and the illustration drifts on a slow ken-burns so the whole card is always quietly alive. Still, aspirational, expensive; nothing decorative that isn't earning its place.
