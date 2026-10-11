Build a full-viewport cinematic hero section for an audio lab using React, Tailwind CSS, and Lucide React icons. Use the DM Serif Display font for the headline and IBM Plex Mono for labels/metadata, both from Google Fonts. The entire page is a single full-height hero — no scrolling, no additional sections.

BACKGROUND VIDEO (ambient loop):

A full-screen background video plays on loop, muted, autoplaying, playsInline, covering the entire viewport with object-cover. The footage is a hero studio speaker with waveforms rippling through the air. The video is fixed-positioned behind everything at z-index 0. It must loop seamlessly — set loop, and if the source has a hard cut, crossfade by holding a second stacked copy is optional; otherwise trust the seamless source.

Video URL: your provided audio-lab-speaker-and-waveforms footage (bundled asset: https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/sonor.mp4)

BOTTOM BLUR OVERLAY (no gradient darkening):

Over the video, a single fixed, full-screen overlay div applies a strong backdrop-blur-xl. It uses a CSS mask so the blur only appears at the bottom and fades to transparent toward the middle: mask-image: linear-gradient(to top, black 0%, transparent 45%) (with the -webkit- prefix too). NO dark gradient — only blur. pointer-events-none, z-index 1.
Add a fine grain layer: a second fixed div, opacity 0.05, mix-blend-mode: overlay, background a tiled SVG feTurbulence noise data URI.

FONT:

Import DM Serif Display (weight 400, normal + italic) and IBM Plex Mono (weights 400,500). The headline uses DM Serif Display with letter-spacing -0.01em. Labels/metadata use IBM Plex Mono uppercase, letter-spacing 0.22em, text-[11px].

LIQUID GLASS EFFECT (nav CTA + hero buttons):

Create a reusable .liquid-glass CSS class with these exact properties:
background: rgba(255, 255, 255, 0.01) with background-blend-mode: luminosity
backdrop-filter: blur(4px) (with -webkit- prefix)
border: none
box-shadow: inset 0 1px 1px rgba(255, 255, 255, 0.1)
position: relative; overflow: hidden
A ::before pseudo-element for a thin glowing border:
position: absolute; inset: 0; border-radius: inherit; padding: 1.4px
background: linear-gradient(180deg, rgba(255,255,255,0.45) 0%, rgba(255,255,255,0.15) 20%, rgba(255,255,255,0) 40%, rgba(255,255,255,0) 60%, rgba(255,255,255,0.15) 80%, rgba(255,255,255,0.45) 100%)
Uses -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0) with -webkit-mask-composite: xor and mask-composite: exclude
pointer-events: none

AMBER ACCENT: a thin stroke uses the accent #e8843d. A reusable .amp-line class: height 1px; background: linear-gradient(90deg, transparent, rgba(232,132,61,0.85), transparent); box-shadow: 0 0 10px rgba(232,132,61,0.35).

EQ BARS (signature ambient detail): a small row of 5 vertical bars near the metadata, each 2px wide, accent-colored, animating height with @keyframes eq — a staggered scaleY loop (0.3→1→0.5→1) so they pulse like a live meter. Bars use animation-delay 0/120/240/360/480ms, duration 900ms infinite ease-in-out.

BLUR-FADE-UP ANIMATION (staggered):

@keyframes blurFadeUp — From: opacity:0; filter:blur(20px); transform:translateY(40px). To: opacity:1; filter:blur(0); transform:translateY(0). Class .animate-blur-fade-up runs it 1s ease-out forwards, initial opacity 0. Each element gets an inline animationDelay.

NAVBAR (z-index 50, relative positioned):

justify-between, padding px-4 sm:px-6 md:px-12 py-4 md:py-6.
Left: text wordmark "SONOR" in IBM Plex Mono 500, tracking 0.3em, blur-fade-up 0ms.
Center (hidden below lg): links "Monitors", "The Lab", "Sessions", "Journal" — text-sm text-white/70 hover:text-white transition-colors, staggered 100/150/200/250ms.
Right: a "Listen" glass pill — rounded-full liquid-glass px-4 md:px-6 py-2 with a Lucide Play icon (size 18, fill #e8843d), blur-fade-up 300ms; and a w-10 h-10 rounded-full liquid-glass icon button with Lucide AudioLines (size 18), blur-fade-up 350ms. Hamburger (Lucide Menu/X, w-10 h-10 liquid-glass, rotate/scale transition duration-500) below lg at 300ms.

MOBILE MENU (below lg):

An absolutely positioned dropdown below the navbar (top-[64px]), z-index 40. It slides in with translate-y-0 opacity-100 when open, and -translate-y-4 opacity-0 pointer-events-none when closed, transition duration-500 ease-out.
Background: bg-[#0b0a09]/95 backdrop-blur-lg, border-t border-b border-white/10, shadow-2xl.
Contains the same 4 nav links, each in a column, py-3 px-3 rounded-lg, hover:bg-white/5, with staggered translate-x slide-ins (50ms increments).
Below sm, also shows the "Listen" and AudioLines buttons in a bordered footer section (border-t border-white/10, pt-3, flex gap-3).

HERO CONTENT (bottom of viewport):

A flex container: flex-1 flex flex-col justify-end, padding px-4 sm:px-6 md:px-12 pb-8 md:pb-16, z-index 10.
Metadata row — flex-wrap gap-3 sm:gap-6 mb-6 md:mb-8 text-[11px] IBM Plex Mono text-white/80, blur-fade-up 300ms: the 5-bar EQ meter + "LIVE ROOM", then "·" + "24-BIT / 96 KHZ", then "·" + "FREE PACK". Set the "FREE PACK" tag in accent #e8843d.
Headline — DM Serif Display text-4xl sm:text-6xl md:text-7xl lg:text-8xl, letter-spacing -0.01em, mb-4 md:mb-6, blur-fade-up 400ms. Text: "Hear it before you build it."
Sub-line — IBM Plex Mono text-base sm:text-lg text-white/60 mb-6 md:mb-10 max-w-xl, blur-fade-up 500ms. Text: "A studio where the sound is the product."
CTA buttons — flex-wrap gap-3 sm:gap-4:
"Play the room" — bg-white text-black rounded-full font-medium px-6 sm:px-8 py-2.5 sm:py-3 with Lucide Play (size 18, fill-black), hover:bg-gray-200, blur-fade-up 600ms.
"Free download" — rounded-full liquid-glass px-6 sm:px-8 py-2.5 sm:py-3 with Lucide Download (size 18, stroke #e8843d), blur-fade-up 700ms.

COLOR PALETTE:
Background: #0b0a09 (warm near-black)
Text: white; sub-copy white/60
Accent: #e8843d (amber signal) — EQ bars, amp-line, FREE PACK tag, and CTA icons only
Solid element: the white "Play the room" button

STAGGER TIMING SUMMARY:
Wordmark 0ms · Nav links 100/150/200/250ms · Listen pill 300ms · Audio icon 350ms · Metadata row 300ms · Headline 400ms · Sub-line 500ms · Play the room 600ms · Free download 700ms.

RESPONSIVE BREAKPOINTS:
Below sm: smaller text, tighter padding; the AudioLines icon button hides (available via menu); CTAs stack full-width.
Below lg: nav links hidden, hamburger shown.
lg and up: full navbar with all links; metadata row and CTAs sit at the lower-left over the seamless loop.
Respect prefers-reduced-motion: if set, pause the EQ bars and the video (show first frame), keep copy static.
