Build a full-viewport cinematic hero section for a fine-stationery house called PLUME / PAPERIE using React, Tailwind CSS, and Lucide React icons. Use the Cormorant font (display headings) and Inter (body/UI) from Google Fonts. The entire page is a single full-height hero — no scrolling, no additional sections. The brand is PLUME, a fine paperie of ink and feather — a nib drawing a line, paper catching light. This is the FREE pack, so a small "FREE" ribbon is part of the design. LIGHT, warm, ivory-paper treatment.

BACKGROUND VIDEO:

A full-screen background video plays on loop, muted, autoplaying (autoPlay, muted, loop, playsInline), covering the entire viewport with object-cover. The video is fixed-positioned behind everything at z-index 0. It shows fine stationery — ink, feather, paper — in a slow ambient drift, framed to the right so copy sits on ivory to the left. Seamless loop.

Video URL: your provided paperie footage (bundled asset: https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/plume.mp4)

LIGHT / IVORY-PAPER TREATMENT (this page reads bright):

The overlays are LIGHT ivory washes, not black scrims:
- Text-readability wash: a fixed overlay z-index 1, pointer-events-none, ivory masked to the bottom: background: linear-gradient(to top, rgba(246,241,231,0.74) 0%, rgba(246,241,231,0.18) 38%, transparent 62%). Ink text sits on paper at the lower third.
- A soft top scrim behind the navbar: linear-gradient(to bottom, rgba(246,241,231,0.6), transparent 18%).
- Text color is DARK ink #24211c on this page.

DECKLE + GRAIN:

- .paper-grain — a fixed pointer-events-none overlay z-index 2, opacity 0.05, mix-blend-mode: multiply, inline SVG feTurbulence noise data URI (fractalNoise, baseFrequency 0.85). Fine laid-paper tooth.
- .gild — background: linear-gradient(180deg, #f0d79a 0%, #e8c87a 45%, #caa24f 60%, #f3e2b0 100%); -webkit-background-clip: text; background-clip: text; color: transparent — gilded gold for the headline accent word, like foil on a monogram.
- .hairline { height: 1px; background: linear-gradient(90deg, transparent, rgba(202,162,79,0.6), transparent); } — a thin gold rule under the eyebrow.

FONT:

Import Cormorant (weights 300, 400, 500; italic available) and Inter (weights 300–500) from Google Fonts. Set font-family: 'Inter', sans-serif on the body. Headline and logo use font-family: 'Cormorant', serif with letter-spacing -0.01em, generous leading, italic for the accent word. Labels/eyebrows use Inter with wide tracking.

LIQUID GLASS EFFECT (LIGHT variant, used on buttons):

Create a reusable .liquid-glass CSS class tuned for a light background:
- background: rgba(255, 253, 247, 0.35) with background-blend-mode: luminosity
- backdrop-filter: blur(6px) (with -webkit- prefix)
- border: none
- box-shadow: inset 0 1px 1px rgba(255, 255, 255, 0.6)
- position: relative; overflow: hidden
- A ::before pseudo-element for a thin gold border: position: absolute; inset: 0; border-radius: inherit; padding: 1.4px; background: linear-gradient(180deg, rgba(202,162,79,0.6) 0%, rgba(202,162,79,0.2) 20%, rgba(255,255,255,0) 40%, rgba(255,255,255,0) 60%, rgba(202,162,79,0.2) 80%, rgba(202,162,79,0.6) 100%); -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0); -webkit-mask-composite: xor; mask-composite: exclude; pointer-events: none.

BLUR-FADE-UP ANIMATION (every element, staggered):

@keyframes blurFadeUp — From: opacity 0; filter: blur(20px); transform: translateY(40px). To: opacity 1; filter: blur(0); transform: translateY(0). The .animate-blur-fade-up class applies animation: blurFadeUp 1.1s ease-out forwards with initial opacity 0. Each element gets a staggered animationDelay via inline style.
@keyframes inkDraw { from { transform: scaleX(0);} to { transform: scaleX(1);} } (transform-origin: left) so the eyebrow .hairline draws in like a nib stroke.

FREE RIBBON (signature to this pack):

A small pill top-right of the hero content (or beside the eyebrow), Inter text-[10px] tracking-[0.3em] uppercase, px-3 py-1 rounded-full, background transparent with a 1px gold border (border border-[#caa24f]/60), text-[#caa24f], reading "FREE PACK". blur-fade-up at 260ms.

NAVBAR (z-index 50, relative):

Horizontal navbar, justify-between, padding px-4 sm:px-6 md:px-12 py-4 md:py-6.
Left: text logo "PLUME" in Cormorant text-2xl tracking-[0.04em] text-[#24211c], with a hairline "/ PAPERIE" in Inter text-[10px] tracking-[0.3em] text-[#caa24f] alongside (hidden below sm). Blur-fade-up at 0ms.
Center (hidden below lg): links "Stationery", "Monograms", "Wax & Seals", "Bespoke" — Inter text-sm text-[#24211c]/70 hover:text-[#24211c] transition-colors, staggered 100–250ms (50ms steps).
Right: a "Order a Set" liquid-glass pill (rounded-full, px-5 py-2, text-sm text-[#24211c]) with a Lucide Feather icon (size 16), blur-fade-up at 350ms. A hamburger button below lg — w-10 h-10 rounded-full liquid-glass, animated Menu↔X (rotate-180, opacity, scale-50, duration-500 ease-out), blur-fade-up at 350ms.

MOBILE MENU (below lg):

Absolutely positioned dropdown top-[72px], z-40. Slides in translate-y-0 opacity-100 when open; -translate-y-4 opacity-0 pointer-events-none when closed; duration-500 ease-out. Background bg-[#f6f1e7]/95 backdrop-blur-lg, border-t border-b border-[#24211c]/10 shadow-2xl. Same 4 links, ink text, each py-3 px-3 rounded-lg hover:bg-[#24211c]/5, staggered translate-x slide-ins (50ms steps).

HERO CONTENT (bottom of viewport):

A flex container flex-1 flex flex-col justify-end, padding px-4 sm:px-6 md:px-12 pb-10 md:pb-16, z-index 10.

Eyebrow — Inter, text-[11px] tracking-[0.34em] uppercase text-[#caa24f], mb-3, with a .hairline 64px wide beneath (inkDraw), blur-fade-up at 300ms. Text: "FINE STATIONERY · SINCE 1888"

Metadata row — flex-wrap gap-x-6 gap-y-2 mb-6 md:mb-8, Inter text-[11px] tracking-[0.22em] uppercase text-[#24211c]/50, blur-fade-up at 380ms. Three items, each an icon + label:
  Feather icon (size 14) + "HAND-CUT NIBS"
  Stamp icon (size 14) + "WAX SEALED"
  Droplet icon (size 14) + "IRON-GALL INK"

Headline — Cormorant text-5xl sm:text-6xl md:text-7xl lg:text-8xl font-light leading-[0.98] tracking-[-0.01em] mb-5, blur-fade-up at 450ms. Two lines forced with a block span per line: "Every word" then italic "worth keeping." Apply .gild to "worth keeping."

Sub-line — Inter text-base sm:text-lg md:text-xl text-[#24211c]/65 max-w-xl mb-8, blur-fade-up at 560ms. Text: "Ink that bites the page and paper that remembers it — stationery made to be written on, and read years later."

CTA row — flex flex-wrap gap-3 sm:gap-4, blur-fade-up wrapper:
  "Order a Set" — bg-[#e8c87a] text-[#24211c] rounded-full font-medium px-6 sm:px-8 py-2.5 sm:py-3 text-sm, Lucide Feather icon (size 16), hover:bg-[#efd692] transition-colors, blur-fade-up at 660ms.
  "See the Paperie" — rounded-full font-medium liquid-glass px-6 sm:px-8 py-2.5 sm:py-3 text-sm text-[#24211c], Lucide ArrowRight icon (size 16), blur-fade-up at 760ms.

Bottom hint (right-aligned on md+, under CTAs on mobile) — Inter text-[10px] tracking-[0.28em] uppercase text-[#24211c]/35 flex items-center gap-2, blur-fade-up at 860ms: PenTool icon (size 12) + "PRESSED, NOT PRINTED".

COLOR PALETTE:

Background: warm ivory paper (bg-[#f6f1e7]).
Text: ink #24211c, with #24211c/65 for the sub-line and /50–35 for micro-labels.
Accent: #e8c87a (gilt gold) with a deeper #caa24f for eyebrows/rules on cream. Used in eyebrow, gilded headline word, FREE ribbon, hairline, and the one solid CTA.
The only solid element is the "Order a Set" button (gold bg, ink text).

STAGGER TIMING SUMMARY:

Logo 0ms · Nav links 100/150/200/250ms · Order-a-Set nav pill 350ms · Hamburger 350ms · FREE ribbon 260ms · Eyebrow 300ms · Metadata row 380ms · Headline 450ms · Sub-line 560ms · Order-a-Set CTA 660ms · See-the-Paperie 760ms · Pressed-not-printed hint 860ms.

RESPONSIVE BREAKPOINTS:

Below sm (< 640px): smaller headline (text-5xl), tighter padding, "/ PAPERIE" logo tag hidden, metadata wraps over two rows, hint sits under the CTAs, FREE ribbon sits inline before the eyebrow.
Below lg (< 1024px): nav links hidden, hamburger shown.
md and up: headline scales up, hint aligns bottom-right.
lg and up: full desktop navbar with all links visible.
Respect prefers-reduced-motion: draw the hairline instantly, drop paper-grain motion, reveal elements without blur.
