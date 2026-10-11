Build a full-viewport cinematic planetarium hero section using React, Tailwind CSS, and Lucide React icons. Use the Fraunces font from Google Fonts for display type and Inter for UI/body, plus IBM Plex Mono for tiny tracked labels. The entire page is a single full-height hero — no scrolling, no additional sections. The brand is HOURGLASS, a free planetarium whose signature is a cosmic hourglass whose falling sand is made of drifting stars, turning slowly in deep space. The video is a seamless ambient loop behind everything, and admission is FREE.

BACKGROUND VIDEO:

A full-screen background video plays on loop, muted, autoplaying (autoPlay, muted, loop, playsInline), covering the entire viewport with object-cover, fixed-positioned behind everything at z-index 0. It shows a cosmic hourglass turning in deep space, its sands falling as tiny drifting stars, a soft violet nebula behind. The hourglass is centered, motion slow and seamless — pick a clip that loops without a visible cut.

Video URL: your provided cosmic hourglass sands as stars footage (bundled asset: https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/hourglass.mp4)

BOTTOM BLUR + GLOW SCRIM (no flat wash):

Over the video there is a single fixed, full-screen overlay div at z-index 1, pointer-events-none. It applies a strong backdrop-blur-xl gated by a CSS mask so the blur only appears at the bottom and fades to transparent toward the middle: mask-image: linear-gradient(to top, black 0%, transparent 45%) (with the -webkit- prefix too). NO dark gradient darkening — only blur. Add a second fixed pointer-events-none div (z-index 1) with a violet floor glow background: radial-gradient(130% 75% at 50% 100%, rgba(155,107,255,0.14), transparent 55%) so the accent seeps up like nebula light.

GRAIN OVERLAY:

Fixed full-screen pointer-events-none div at z-index 2, inline SVG feTurbulence noise data-URI background, opacity 0.05, mix-blend-mode: overlay.

FONT:

Import Fraunces (weights 400, 500, 600, italic 400) and Inter (weights 300–500) from Google Fonts, plus IBM Plex Mono (400, 500). Set font-family: 'Inter', sans-serif on the body. Use .font-serif ('Fraunces') for the headline and logo wordmark; Inter for nav, sub-line, buttons; .font-mono ('IBM Plex Mono') for tracked micro-labels only.

LIQUID GLASS EFFECT (used on buttons):

Create a reusable .liquid-glass CSS class with these exact properties:

background: rgba(255, 255, 255, 0.01) with background-blend-mode: luminosity
backdrop-filter: blur(4px) (with -webkit- prefix)
border: none
box-shadow: inset 0 1px 1px rgba(255, 255, 255, 0.1)
position: relative; overflow: hidden
A ::before pseudo-element that creates a thin glowing border effect:
position: absolute; inset: 0; border-radius: inherit; padding: 1.4px
background: linear-gradient(180deg, rgba(255,255,255,0.45) 0%, rgba(255,255,255,0.15) 20%, rgba(255,255,255,0) 40%, rgba(255,255,255,0) 60%, rgba(255,255,255,0.15) 80%, rgba(255,255,255,0.45) 100%)
Uses -webkit-mask with linear-gradient(#fff 0 0) content-box and linear-gradient(#fff 0 0) combined with -webkit-mask-composite: xor and mask-composite: exclude to create a border-only gradient stroke
pointer-events: none

ACCENT GLASS VARIANT (.accent-glass) — same as .liquid-glass but the ::before gradient uses the accent: linear-gradient(180deg, rgba(155,107,255,0.65) 0%, rgba(155,107,255,0.16) 30%, rgba(155,107,255,0) 50%, rgba(155,107,255,0.16) 75%, rgba(155,107,255,0.55) 100%) and add box-shadow: 0 0 40px -12px rgba(155,107,255,0.5). Used on the primary CTA.

ACCENT TEXT (.accent-text): background: linear-gradient(180deg, #d6c4ff 0%, #9b6bff 55%, #6a3fd0 100%); -webkit-background-clip: text; background-clip: text; color: transparent. Used on the headline emphasis word.

BLUR-FADE-UP ANIMATION (every element, staggered):

@keyframes blurFadeUp — From: opacity: 0; filter: blur(20px); transform: translateY(40px). To: opacity: 1; filter: blur(0); transform: translateY(0). The .animate-blur-fade-up class applies animation: blurFadeUp 1.1s cubic-bezier(0.2,0.7,0.2,1) forwards with initial opacity: 0. Each element gets a staggered animationDelay via inline style.

@keyframes accentPulse — 7s ease-in-out infinite on the primary CTA: 0%,100% box-shadow 0 0 40px -14px rgba(155,107,255,0.45); 50% box-shadow 0 0 64px -8px rgba(155,107,255,0.72).

NAVBAR (z-index 50, relative positioned):

Horizontal, justify-between, px-4 sm:px-6 md:px-12 py-4 md:py-6.
Left: wordmark "HOURGLASS" in .font-serif text-2xl tracking-[0.02em] text-white, with "PLANETARIUM" in .font-mono text-[11px] tracking-[0.3em] uppercase text-white/45 alongside. Blur-fade-up 0ms.
Center (hidden below lg): links "Shows", "Dome", "Tonight", "Visit" — text-sm text-white/60 hover:text-white transition-colors, staggered 100–250ms.
Right: a small "FREE" badge — rounded-full bg-[#9b6bff] text-white text-[11px] font-medium tracking-[0.14em] px-3 py-1 — next to a "Reserve seats" pill (rounded-full accent-glass px-5 md:px-6 py-2 text-sm text-white) with Lucide ChevronRight (size 16), blur-fade-up 350ms. Below lg: w-10 h-10 rounded-full liquid-glass hamburger (Lucide Menu/X cross-fade, rotate-180 + scale-50, duration-500), 350ms.

MOBILE MENU (below lg):

Absolutely positioned dropdown top-[72px], z-40. Slides in translate-y-0 opacity-100 when open; -translate-y-4 opacity-0 pointer-events-none when closed; duration-500 ease-out. Background bg-[#080611]/95 backdrop-blur-lg, border-y border-white/10 shadow-2xl. Same 4 links, each py-3 px-3 rounded-lg hover:bg-white/5, staggered translate-x slide-ins (50ms steps). The FREE badge repeats in a bordered footer section.

HERO CONTENT (bottom of viewport):

A flex container flex-1 flex flex-col justify-end, padding px-4 sm:px-6 md:px-12 pb-10 md:pb-16, z-index 10.

Eyebrow — .font-mono text-[11px] tracking-[0.3em] uppercase text-white/50, mb-5, blur-fade-up 300ms. Text: "FREE ADMISSION · 45 MIN · FULL-DOME"

Metadata row — flex-wrap gap-3 sm:gap-6 mb-6 md:mb-8 .font-mono text-[11px] sm:text-xs tracking-[0.2em] uppercase text-white/55, blur-fade-up 380ms. Three items, icon + label:
  Star icon (size 14) + "SANDS OF STARS"
  Clock icon (size 14) + "SHOWS EVERY HOUR"
  Ticket icon (size 14) + "NO CHARGE"

Headline — .font-serif text-6xl sm:text-7xl md:text-8xl lg:text-9xl leading-[0.94] tracking-[-0.01em] text-white mb-5, blur-fade-up 450ms. Two lines: "Time falls as" then "starlight." where "starlight." carries the .accent-text class (set in Fraunces italic). Force the break with block spans.

Sub-line — text-base sm:text-lg md:text-xl text-white/60 max-w-xl mb-8, blur-fade-up 560ms. Text: "Sit under the dome and watch the sands run in stars — free, every hour."

CTA row — flex flex-wrap gap-3 sm:gap-4:
  "Reserve a seat" — bg-[#9b6bff] text-neutral-950 rounded-full font-medium px-6 sm:px-8 py-2.5 sm:py-3 text-sm, Lucide ArrowRight icon (size 16), accentPulse, hover:bg-[#b18fff], blur-fade-up 660ms.
  "Watch the trailer" — rounded-full font-medium liquid-glass px-6 sm:px-8 py-2.5 sm:py-3 text-sm text-white, Lucide Play icon (size 16), blur-fade-up 760ms.

Bottom hint (right-aligned on md+, under CTAs on mobile) — .font-mono text-[10px] tracking-[0.26em] uppercase text-white/40 flex items-center gap-2, blur-fade-up 860ms: MapPin icon (size 12) + "NEXT SHOW · 9:00 PM".

COLOR PALETTE:

Background: deep space #080611 (page bg bg-black).
Text: white for headings, white/60 for the sub-line, white/45–55 for mono micro-labels.
Accent (the ONE): nebula violet #9b6bff (with #d6c4ff → #6a3fd0 inside gradient text and glows).
Only solid elements are the FREE badge (violet) and the "Reserve a seat" CTA (violet on near-black text); everything else is glass or type.

STAGGER TIMING SUMMARY:

Logo 0ms · Nav links 100/150/200/250ms · FREE badge + Reserve seats 350ms · Hamburger 350ms · Eyebrow 300ms · Metadata row 380ms · Headline 450ms · Sub-line 560ms · Reserve-a-seat 660ms · Watch-the-trailer 760ms · Next-show hint 860ms.

RESPONSIVE BREAKPOINTS:

Below sm (< 640px): headline text-6xl, tighter padding, metadata wraps over two rows, next-show hint sits under the CTAs.
Below lg (< 1024px): nav links hidden, hamburger + mobile menu shown.
md and up: headline scales up, next-show hint aligns bottom-right.
lg and up: full desktop navbar with all links visible.
Reduced motion: blurFadeUp → simple opacity fades; accentPulse disabled; video stays a gentle autoplay loop.
