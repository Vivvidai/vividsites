Build a full-viewport ambient hero section using React, Tailwind CSS, and Lucide React icons. Use the Fraunces font (display serif) and Inter Tight (UI) from Google Fonts. The entire page is a single full-height hero — no scrolling. This is KNEAD, an artisan bakehouse: warm dough, crackling crust, morning light. (This template is FREE.)

BACKGROUND VIDEO:

A full-screen background video plays on loop, muted, autoplaying, playsInline, object-cover, fixed behind everything at z-index 0.

Seamless footage — hands folding dough, a slow crust bake, flour catching light — that loops without a hard cut.

Add keyframe "warmDrift" scaling 1 to 1.05 over 22s ease-in-out infinite so the frame breathes like a warm oven.

Video URL: your provided bakehouse footage (bundled asset: https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/knead.mp4)

BOTTOM BLUR OVERLAY (no dark gradient):

A fixed full-screen overlay, backdrop-blur-xl, masked bottom-only:

mask-image: linear-gradient(to top, black 0%, transparent 47%) — with the -webkit- prefix.

pointer-events-none, z-index 1. Blur only, so the warm tones stay rich.

CRUMB SCRIM (accent warmth):

A second fixed overlay z-index 1 pointer-events-none, mix-blend-mode: screen:

radial-gradient(120% 100% at 50% 88%, rgba(217,160,102,0.24), transparent 62%)

a soft crust-brown glow rising from the base.

FONT:

Import Fraunces (weights 400, 500 + italic, opsz) and Inter Tight (weights 300-500).

Body font-family: 'Inter Tight', sans-serif.

Headline uses 'Fraunces', serif with font-optical-sizing: auto and a soft italic accent word.

LIQUID GLASS EFFECT (used on buttons/pills):

Create a reusable .liquid-glass CSS class with these exact properties:

background: rgba(255, 255, 255, 0.01) with background-blend-mode: luminosity
backdrop-filter: blur(4px) (with -webkit- prefix)
border: none
box-shadow: inset 0 1px 1px rgba(255, 255, 255, 0.1)
position: relative; overflow: hidden

A ::before pseudo-element:
position: absolute; inset: 0; border-radius: inherit; padding: 1.4px
background: linear-gradient(180deg, rgba(255,255,255,0.45) 0%, rgba(255,255,255,0.15) 20%, rgba(255,255,255,0) 40%, rgba(255,255,255,0) 60%, rgba(255,255,255,0.15) 80%, rgba(255,255,255,0.45) 100%)
-webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0); -webkit-mask-composite: xor; mask-composite: exclude
pointer-events: none

GRADIENT TEXT (accent word):

.crust-text { background: linear-gradient(180deg, #fbe6cf, #e7bd90 55%, #d9a066); -webkit-background-clip: text; background-clip: text; color: transparent; }

Applied to the italic accent word in the headline.

FREE BADGE:

A small pill in the metadata row: .liquid-glass rounded-full px-3 py-1, Inter Tight text-[10px] tracking-[0.25em] uppercase, content "FREE TEMPLATE", with a Lucide Gift icon (size 12) tinted #d9a066. blur-fade-up 260ms.

BLUR-FADE-UP ANIMATION (staggered):

@keyframes blurFadeUp —
From: opacity 0; filter blur(20px); transform translateY(40px)
To: opacity 1; filter blur(0); transform translateY(0)

.animate-blur-fade-up applies animation: blurFadeUp 1.1s ease-out forwards, initial opacity 0, inline animationDelay per element.

Add @keyframes floatSlow — translateY 0 to -8px and back over 6s ease-in-out infinite — on the metadata row so it drifts gently.

NAVBAR (z-index 50, relative):

justify-between, px-4 sm:px-6 md:px-12 py-4 md:py-6.

Left: wordmark "Knead" in Fraunces italic text-xl md:text-2xl tracking-tight, blur-fade-up 0ms.

Center (hidden below lg): links, text-sm text-white/70 hover:text-white, staggered:
"Bakes" — 100ms
"Our Starter" — 150ms
"Find Us" — 200ms
"Order" — 250ms

Right: "Order Ahead" liquid-glass pill rounded-full px-5 md:px-6 py-2 text-sm with Lucide ShoppingBag icon (size 16), blur-fade-up 300ms.

Below lg: w-10 h-10 rounded-full liquid-glass hamburger (Menu/X crossfade rotate-180 scale-50 duration-500) at 300ms.

HERO CONTENT (bottom-anchored, warm editorial):

Container flex-1 flex flex-col justify-end, padding px-4 sm:px-6 md:px-12 pb-8 md:pb-16, z-index 10. Inner flex-col md:flex-row items-end gap-8.

Left (flex-1):

Metadata row — flex flex-wrap items-center gap-4 mb-6 text-xs sm:text-sm, blur-fade-up 300ms, floatSlow:
the FREE badge · Lucide Clock (16) + "Baked at 5am" · Lucide Wheat (16, tinted crust) + "Wild Yeast".

Headline — Fraunces text-4xl sm:text-6xl md:text-7xl font-medium leading-[1.03] tracking-[-0.02em], mb-5, blur-fade-up 420ms.
Text: "Slow Dough. Honest Crust." with "Honest" in italic + .crust-text.

Sub-line — Inter Tight text-base sm:text-lg text-white/60 max-w-xl mb-8, blur-fade-up 540ms.
Text: "A neighborhood bakehouse folding real sourdough by hand, one warm batch a morning."

CTA row — flex flex-wrap gap-3:
"Order Ahead" — solid bg-white text-black rounded-full font-medium px-7 py-3 with Lucide ArrowRight (size 18), hover:bg-white/90, blur-fade-up 640ms.
"See Today's Bakes" — liquid-glass rounded-full px-7 py-3, blur-fade-up 740ms.

Right (batch chip, md:w-auto):

A liquid-glass rounded-2xl px-6 py-5 max-w-xs text-right, blur-fade-up 820ms:
small serif italic "Today's Batch" title, then Inter Tight text-sm text-white/60 "Country loaf · Rye · Seeded" and a line "Fresh from 7am · while it lasts".

COLOR PALETTE:

Background: warm near-black bg-[#0d0a07] beneath the video.
Text: white, white/60 sub-copy.
Accent: #d9a066 (warm crust) — .crust-text, crumb scrim, icon tints, FREE badge gift icon.
Solid element: the white "Order Ahead" button. Everything else uses .liquid-glass.

STAGGER TIMING SUMMARY:

Logo: 0ms
Nav links: 100ms, 150ms, 200ms, 250ms
Order Ahead pill / hamburger: 300ms
FREE badge: 260ms
Metadata row: 300ms
Headline: 420ms
Sub-line: 540ms
Order Ahead: 640ms
See Today's Bakes: 740ms
Batch chip: 820ms

RESPONSIVE BREAKPOINTS:

Below sm (< 640px): headline text-4xl, metadata wraps, CTAs stack full-width, the batch chip drops below the copy left-aligned.
Below lg (< 1024px): center nav hidden, hamburger shown; mobile dropdown top-[72px] z-40 bg-[#0d0a07]/95 backdrop-blur-lg, 4 links stacked py-3 with staggered translate-x slide-ins.
md and up: side-by-side copy + batch chip, headline text-7xl.
Respect prefers-reduced-motion: freeze warmDrift and floatSlow, keep blurFadeUp once.
