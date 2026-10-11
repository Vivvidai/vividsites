Build a full-viewport ambient hero section using React, Tailwind CSS, and Lucide React icons. Use the Inter Tight font (display + UI) and IBM Plex Mono (tiny labels) from Google Fonts. The entire page is a single full-height hero — no scrolling. This is SUB2, a race campaign to break the 2-hour marathon: bold, athletic, urgent, human.

BACKGROUND VIDEO:

A full-screen background video plays on loop, muted, autoplaying, playsInline, covering the viewport with object-cover, fixed behind everything at z-index 0.

It is seamless — footage of a lone runner at pace / track at dawn / stride in motion that loops without a hard cut.

Add keyframe "slowPush" scaling 1 to 1.05 over 20s ease-in-out infinite so the frame pushes in like a broadcast plate.

Video URL: your provided race-campaign footage (bundled asset: https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/sub2.mp4)

BOTTOM BLUR OVERLAY (no dark gradient):

A fixed full-screen overlay div, backdrop-blur-xl, masked to the bottom:

mask-image: linear-gradient(to top, black 0%, transparent 45%) — with the -webkit- prefix.

pointer-events-none, z-index 1. Blur only, no darkening.

HEAT SCRIM (accent):

A second fixed overlay, z-index 1, pointer-events-none, mix-blend-mode: screen:

linear-gradient(to top, rgba(255,61,46,0.28), transparent 40%)

so the accent heat rises from the base — the campaign's competitive red.

FONT:

Import Inter Tight (weights 400, 600, 800, 900) and IBM Plex Mono (weights 400, 500) from Google Fonts.

Body font-family: 'Inter Tight', sans-serif.

All uppercase micro-labels, splits, and the timer use 'IBM Plex Mono', monospace with tracking-[0.2em].

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

FREE BADGE:

A small pill top-right of the hero content: .liquid-glass rounded-full px-3 py-1, IBM Plex Mono text-[10px] tracking-[0.25em], content "FREE ENTRY", with a Lucide Ticket icon (size 12) tinted #ff3d2e. blur-fade-up at 200ms.

BLUR-FADE-UP ANIMATION (staggered):

@keyframes blurFadeUp —
From: opacity 0; filter blur(20px); transform translateY(40px)
To: opacity 1; filter blur(0); transform translateY(0)

.animate-blur-fade-up applies animation: blurFadeUp 0.9s ease-out forwards, initial opacity 0. Stagger via inline animationDelay.

@keyframes pulseDot — a small live dot: opacity 1 to 0.3 and scale 1 to 0.85 over 1.4s ease-in-out infinite, used beside the "LIVE CAMPAIGN" label.

NAVBAR (z-index 50, relative):

justify-between, px-4 sm:px-6 md:px-12 py-4 md:py-6.

Left: wordmark "SUB2" in Inter Tight font-black text-xl md:text-2xl tracking-tight, with the "2" tinted #ff3d2e. blur-fade-up 0ms.

Center (hidden below lg): links, text-sm text-white/70 hover:text-white, staggered:
"The Attempt" — 100ms
"The Athlete" — 150ms
"Splits" — 200ms
"Join" — 250ms

Right: "Pledge Support" liquid-glass pill rounded-full px-5 md:px-6 py-2 text-sm with Lucide Heart icon (size 16), blur-fade-up 300ms.

Below lg: w-10 h-10 rounded-full liquid-glass hamburger (Menu/X crossfade rotate-180 scale-50 duration-500) at 300ms.

HERO CONTENT (bottom-anchored, broadcast layout):

Container flex-1 flex flex-col justify-end, padding px-4 sm:px-6 md:px-12 pb-8 md:pb-16, z-index 10. Inner flex-col md:flex-row items-end gap-8.

Left (flex-1):

Status row — flex items-center gap-4 mb-6 text-xs, blur-fade-up 250ms: a live dot (w-2 h-2 rounded-full bg-[#ff3d2e], pulseDot) + IBM Plex Mono "LIVE CAMPAIGN" + a divider + "BERLIN · SEP 2026".

Headline — Inter Tight font-black text-4xl sm:text-6xl md:text-7xl lg:text-[5.5rem] leading-[0.92] tracking-[-0.03em] uppercase, mb-5, blur-fade-up 400ms.
Text: "Two Hours. Not One Second More." with "Two Hours" on its own line.

Sub-line — text-base sm:text-lg text-white/60 max-w-xl mb-8, blur-fade-up 520ms.
Text: "One runner, one wall in human history, and a whole city pacing them through it."

CTA row — flex flex-wrap gap-3:
"Back the Run — Free" — solid bg-white text-black rounded-full font-semibold px-7 py-3 with Lucide ArrowRight icon (size 18), hover:bg-white/90, blur-fade-up 620ms.
"Watch the Film" — liquid-glass rounded-full px-7 py-3 with Lucide Play icon (size 18), blur-fade-up 720ms.

Right (stat rail, md:w-auto):

A row of three stat plates, each a .liquid-glass rounded-2xl px-5 py-4 text-right. Numbers in Inter Tight font-bold text-2xl, labels IBM Plex Mono text-[10px] tracking-[0.2em] text-white/50:
"1:59:XX" — label "TARGET TIME" — blur-fade-up 800ms
"42.2 KM" — label "DISTANCE" — blur-fade-up 860ms
"0.4%" — label "MARGIN LEFT" — blur-fade-up 920ms

On mobile the plates become a horizontal scroll-snap row.

COLOR PALETTE:

Background: bg-[#0b0b0c] beneath the video.
Text: white, white/60 sub-copy, white/50 labels.
Accent: #ff3d2e (campaign red) — the "2", live dot, ticket icon, heat scrim only.
Solid element: the white "Back the Run — Free" button. All else uses .liquid-glass.

STAGGER TIMING SUMMARY:

Logo: 0ms
Nav links: 100ms, 150ms, 200ms, 250ms
Pledge / hamburger: 300ms
FREE badge: 200ms
Status row: 250ms
Headline: 400ms
Sub-line: 520ms
Back the Run: 620ms
Watch the Film: 720ms
Stat plates: 800ms, 860ms, 920ms

RESPONSIVE BREAKPOINTS:

Below sm (< 640px): headline text-4xl, CTAs stack, stat plates become a horizontal scroll-snap strip under the copy.
Below lg (< 1024px): center nav hidden, hamburger shown; mobile dropdown top-[72px] z-40, bg-[#0b0b0c]/95 backdrop-blur-lg, links stacked py-3 with staggered translate-x slide-ins, Pledge button pinned at the bottom of the sheet.
md and up: side-by-side hero copy + stat rail; headline scales to text-[5.5rem].
Respect prefers-reduced-motion: freeze slowPush and pulseDot, keep blurFadeUp once.
