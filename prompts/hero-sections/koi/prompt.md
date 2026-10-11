Build a single full-viewport cinematic hero for a Japanese teahouse using React, Tailwind CSS, and Lucide React icons. Use the Cormorant Garamond font for headlines and Inter for body/labels, both from Google Fonts. The entire page is one full-height hero — no scrolling, no additional sections.

BACKGROUND VIDEO (fixed ambient loop):

A full-screen background video plays on loop, muted, autoplaying, playsInline, covering the entire viewport with object-cover. Footage: koi drifting slowly across a dark, still teahouse pond. The video is fixed behind everything at z-index 0. Because koi motion is slow and continuous, the loop should feel seamless — set preload="auto" and, if a hard cut is visible, cross-dissolve the last 0.5s to the first frame by stacking two offset <video> elements and fading between them on the loop event.

Video URL: your provided koi-in-a-dark-teahouse-pond footage (bundled asset: https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/koi.mp4)

BOTTOM SCRIM (blur + gentle darkening for legibility):

A fixed full-screen overlay, pointer-events-none, z-index 1, with backdrop-blur-md masked to the bottom only:
mask-image: linear-gradient(to top, black 0%, transparent 42%) (with -webkit- prefix)
Plus a soft warm tint layer: background: linear-gradient(180deg, rgba(10,12,11,0) 45%, rgba(10,12,11,0.7) 100%).

FONT:

Import Cormorant Garamond (weights 300,400,500, italic) and Inter (weights 300,400,500). Headline: Cormorant, letter-spacing -0.01em, emphasis words in italic. Labels: Inter uppercase, letter-spacing 0.24em, text-[11px].

LIQUID GLASS EFFECT (nav CTA + hours pill):

Create a reusable .liquid-glass CSS class with these exact properties:
background: rgba(255, 255, 255, 0.01) with background-blend-mode: luminosity
backdrop-filter: blur(4px) (with -webkit- prefix)
border: none
box-shadow: inset 0 1px 1px rgba(255, 255, 255, 0.1)
position: relative; overflow: hidden
A ::before pseudo-element for a thin glowing border:
position: absolute; inset: 0; border-radius: inherit; padding: 1.4px
background: linear-gradient(180deg, rgba(255,255,255,0.45) 0%, rgba(255,255,255,0.15) 20%, rgba(255,255,255,0) 40%, rgba(255,255,255,0) 60%, rgba(255,255,255,0.15) 80%, rgba(255,255,255,0.45) 100%)
-webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0); -webkit-mask-composite: xor; mask-composite: exclude
pointer-events: none

ANIMATIONS:

@keyframes blurFadeUp — From: opacity:0; filter:blur(20px); transform:translateY(40px). To: opacity:1; filter:blur(0); transform:translateY(0). Class .animate-blur-fade-up, 1.4s ease-out forwards (slow, unhurried), initial opacity 0. Each element gets a staggered inline animationDelay.
@keyframes ripple — a single expanding ring behind the eyebrow: transform scale(0.6)→scale(1.8); opacity 0.5→0; 5s ease-out infinite, using a bordered circle with the accent at low alpha.

NAVBAR (z-index 50, relative):

justify-between, padding px-6 md:px-12 py-6.
Left: wordmark "KOI GARDEN" in Inter 500, tracking 0.28em, text-sm, blur-fade-up 0ms.
Center (hidden below lg): links "The Pond", "Tea Menu", "The Room", "Visit" — text-[13px] text-white/70 hover:text-white transition-colors, staggered 100–250ms.
Right: one glass CTA "Reserve a table" — rounded-full liquid-glass px-5 py-2 text-[13px] with a Lucide Leaf icon (size 16, stroke #ff7a4a), blur-fade-up 300ms. Hamburger (Lucide Menu/X) below lg.

HERO CONTENT (bottom-anchored):

flex-1 flex flex-col justify-end, padding px-6 md:px-12 pb-16 md:pb-24, z-index 10, max-w-3xl.
Eyebrow row (with ripple behind): a small dot in accent + "SINCE 1962 · KYOTO" — Inter text-[11px] uppercase text-[#ff7a4a], blur-fade-up 250ms.
Headline: Cormorant text-6xl md:text-8xl font-light, "Where the water keeps time." (italicize "water") blur-fade-up 400ms.
Sub-line: Inter text-lg md:text-xl text-white/60 max-w-xl mt-5, "A teahouse built around a still, dark pond." blur-fade-up 550ms.
CTA row (flex-wrap gap-3 mt-8):
- "Reserve a table" — bg-white text-[#0a0c0b] rounded-full font-medium px-7 py-3 with Lucide Leaf icon (size 18), hover:bg-white/90, blur-fade-up 700ms.
- "View the tea menu" — rounded-full liquid-glass px-7 py-3, blur-fade-up 800ms.
Hours pill (mt-8, inline-flex): .liquid-glass rounded-full px-4 py-2 Inter text-[11px] text-white/70 with Lucide Clock icon (size 14) — "OPEN DAILY · 11:00 – 21:00", blur-fade-up 900ms.

COLOR PALETTE:
Background: #0a0c0b (near-black green-charcoal)
Text: white; sub-copy white/60
Accent: #ff7a4a (koi orange) — eyebrow, ripple ring, nav icon; used sparingly, one warm note against the dark water
Solid element: the white "Reserve a table" button

STAGGER TIMING SUMMARY:
Wordmark 0ms · Nav links 100/150/200/250ms · Nav CTA 300ms · Eyebrow 250ms · Headline 400ms · Sub-line 550ms · Reserve button 700ms · Tea menu button 800ms · Hours pill 900ms.

RESPONSIVE BREAKPOINTS:
Below sm: headline text-5xl, CTAs stack full-width, tighter padding.
Below lg: nav links hidden, hamburger shown; mobile menu dropdown (bg-[#0a0c0b]/95 backdrop-blur-lg) with the four links + reserve CTA, slide-in with 50ms stagger.
lg and up: full navbar with all links.
Respect prefers-reduced-motion: keep the video looping but disable ripple; elements fade in without blur/translate.
