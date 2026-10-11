Build a full-viewport, single-screen editorial hero for TERRA — a wellness brand of living terrariums ("living goods"). One self-contained HTML file: inline <style>, inline <script> if needed, Google Fonts via <link> in the head, and one background video. No build step, no external JS/CSS/images beyond Google Fonts and the video. The whole page is a single 100vh hero — no scrolling, no additional sections. It must render perfectly at 1280x800 (it will be screen-recorded at that size). Theme is DARK. The archetype is HUGE modern-sans editorial — an oversized sans headline dominates the screen, floating over the video.

BACKGROUND VIDEO:

A single full-screen background video plays on loop, muted, autoplaying, playsinline, covering the entire viewport with object-fit:cover, fixed-positioned behind everything at z-index 0. The footage is a single glass terrarium filled with moss and tiny plants — soft, slow, meditative. Use src="https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/terra.mp4".

VIGNETTE + SCRIM (no heavy black overlay):

Over the video sits a fixed, full-screen, pointer-events-none vignette div at z-index 1. It combines a radial vignette that darkens the outer edges (radial-gradient(120% 100% at 50% 42%, transparent 40%, rgba(6,9,7,0.55) 100%)) with a vertical gradient that darkens only the very top and bottom for nav/caption legibility (transparent through the middle 22%-58%). Add a second, separate pointer-events-none "scrim" div centered behind the headline only: a soft blurred radial pool (radial-gradient(60% 55% at 50% 50%, rgba(6,9,7,0.55) 0%, transparent 72%)) with filter:blur(8px), sized ~min(1100px,92vw) by min(560px,72vh). Never a flat black overlay — the terrarium must stay visible everywhere.

FONTS:

Import Manrope (weights 300, 400, 500, 600, 700) for the modern-sans display, Inter (300, 400, 500) for body/nav, and IBM Plex Mono (400) for the tiny mono captions. Set font-family:'Inter',sans-serif on the body.

COLOR PALETTE:

Background base #0a0d0b (near-black green-charcoal). Ink text #f3f1ea (warm off-white). Muted text rgba(243,241,234,0.62). Hairline borders rgba(243,241,234,0.18). One accent only: #57c785 (soft living green), used for the accent word in the headline, the eyebrow, the glow dot, and hover states.

LAYOUT SHELL:

A relative z-index:5 flex column, height 100vh: nav at top, hero centered and flex:1, a caption row pinned at the bottom.

NAV (top):

Horizontal, space-between, padding ~26px clamp(24px,5vw,64px). Left: the wordmark "TERRA" in Manrope 600, ~24px, letter-spacing 0.14em. Center: three plain links "Science", "Products", "Journal" in Inter 14px, muted color, 38px gap, hover transitions to full ink. Right: one text CTA "Shop ->" in Inter 500, 14px, hover turns accent green. Hide the center links below 720px.

HERO (centered, dominant):

Vertically and horizontally centered, text-align center, nudged up ~2vh so it optically centers above the caption.

- Eyebrow: a mono label "LIVING WELLNESS" in IBM Plex Mono, 11px, letter-spacing 0.32em, uppercase, accent green, preceded by a small 5px accent dot with a soft green glow (box-shadow 0 0 12px accent). Margin-bottom ~30px.
- H1: "Grow quietly." in Manrope, weight 500, font-size clamp(72px,15vw,188px), line-height 0.9, letter-spacing -0.02em, ink color. The word "quietly." is wrapped in <em> — no italic, weight 700, colored accent green. This headline is the hero of the page; let it be enormous.
- Sub: "Living wellness, cultivated slowly." in Inter 300, clamp(15px,1.6vw,18px), muted color, margin-top ~30px.
- CTA: an outline pill "Explore Terra ->", padding 15px 34px, border-radius 100px, 1px hairline border, ink text, Inter 400 15px. On hover: border becomes accent green, background rgba(87,199,133,0.08), text pure white, and the arrow nudges right ~4px via a transform transition. Margin-top ~40px.

BOTTOM CAPTION:

A space-between row pinned at the bottom, padding 0 clamp(24px,5vw,64px) 30px, IBM Plex Mono 11px, letter-spacing 0.24em, uppercase, muted. Left: "TERRA · Living Goods". Right (dimmer, hidden below 720px): "Cultivated in glass — No. 001".

ENTRANCE MOTION (staggered fade/blur-rise):

Define @keyframes blurFadeUp: from { opacity:0; filter:blur(18px); transform:translateY(34px) } to { opacity:1; filter:blur(0); transform:translateY(0) }. Apply via a .rise class: opacity:0 then animation:blurFadeUp 1.1s cubic-bezier(.2,.7,.2,1) forwards. Give each element a staggered inline animation-delay: wordmark 0ms, nav links 80/140/200ms, Shop 260ms, eyebrow 340ms, H1 420ms, sub 600ms, CTA 720ms, bottom caption 900ms. The result is a calm, cascading settle. Wrap it all in @media (prefers-reduced-motion:reduce) to disable the animation (opacity:1, no blur/transform).

VOICE:

Confident, minimal, botanical-luxury — not poetry. Real product-brand copy for slow living / wellness terrariums. Keep everything on one screen, uncluttered, with the giant modern-sans headline and the living terrarium doing all the work.
