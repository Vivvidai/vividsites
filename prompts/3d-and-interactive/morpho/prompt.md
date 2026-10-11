Build a full-viewport naturalist field-journal hero section using React, Tailwind CSS, and Lucide React icons. Use the Fraunces font from Google Fonts for display type and Inter for UI/body. The treatment is soft and papery — a warm cream field-journal page, not harsh black. The entire page is a single full-height hero — no scrolling, no additional sections. The brand is MORPHO, a free open field journal whose signature is a living iridescent morpho butterfly holding still in a soft void, its wings catching blue light. The CURSOR shifts its wings — move the mouse and the iridescence and tilt follow.

BACKGROUND VIDEO:

A full-screen background video plays on loop, muted, autoplaying (autoPlay, muted, loop, playsInline), covering the entire viewport with object-cover, fixed-positioned behind everything at z-index 0. It shows an iridescent blue morpho butterfly, wings slowly breathing open and shut in a soft warm void, structural colour flickering across the scales. The butterfly is the centered subject.

Video URL: your provided iridescent morpho butterfly footage (bundled asset: https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/morpho.mp4)

CURSOR-REACTIVE WING SHIFT (signature interaction):

Wrap the video in a fixed container with perspective: 1600px. On pointer move over the hero, drive a gentle 3D tilt so the wings feel like the cursor is turning the specimen in the light. Track mouse position as normalized -1..1 from viewport center (mx, my). Lerp smoothly with requestAnimationFrame (ease factor 0.05 per frame — soft, this is a live insect, not a machine). Apply to the video wrapper:
  transform: scale(1.08) rotateX(calc(var(--my) * -6deg)) rotateY(calc(var(--mx) * 8deg)) translate(calc(var(--mx) * 12px), calc(var(--my) * 12px))
The scale(1.08) guarantees edges never reveal gaps during rotation. Also drive a subtle iridescence layer: a fixed pointer-events-none div (z-index 1, mix-blend-mode: screen) with background: radial-gradient(60% 60% at calc(50% + var(--mx)*20%) calc(45% + var(--my)*20%), rgba(46,107,255,0.16), transparent 60%) so a blue sheen slides across as the cursor moves. Under prefers-reduced-motion and on touch devices, disable both (transform: scale(1.03) only, static sheen).

SOFT LIGHT SCRIM (delicate readability):

This is a light, papery treatment. Add a fixed pointer-events-none overlay at z-index 2 with a whisper-soft cream gradient at the bottom so copy reads without crushing the void:
  background: linear-gradient(to top, rgba(247,244,236,0.92) 0%, rgba(247,244,236,0.5) 28%, rgba(247,244,236,0) 54%)
NO dark overlay. Optionally add backdrop-blur-[2px] on the same masked region for a dreamy edge.

FONT:

Import Fraunces (weights 400, 500, italic 400) and Inter (weights 300–500) from Google Fonts. Set font-family: 'Inter', sans-serif on the body. Use Fraunces for the headline and logo wordmark; Inter for nav, sub-line, buttons, micro-labels.

LIQUID GLASS EFFECT (LIGHT variant, used on buttons):

Create a reusable .liquid-glass CSS class tuned for a light background:
  background: rgba(255, 255, 255, 0.35) with background-blend-mode: luminosity
  backdrop-filter: blur(8px) saturate(1.15) (with -webkit- prefix)
  border: none
  box-shadow: inset 0 1px 1px rgba(255,255,255,0.6), 0 1px 20px rgba(46,107,255,0.08)
  position: relative; overflow: hidden
A ::before pseudo-element for a thin border stroke:
  position: absolute; inset: 0; border-radius: inherit; padding: 1.4px
  background: linear-gradient(180deg, rgba(255,255,255,0.9) 0%, rgba(46,107,255,0.4) 30%, rgba(255,255,255,0) 55%, rgba(46,107,255,0.35) 100%)
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0); -webkit-mask-composite: xor; mask-composite: exclude
  pointer-events: none

IRIDESCENT GRADIENT TEXT (headline word accent):

Create a .morpho-text class for one emphasized word so it catches structural blue like a wing scale:
  background: linear-gradient(105deg, #2e6bff 0%, #57c8ff 26%, #8ad0ff 50%, #2e6bff 74%, #1741b8 100%)
  background-size: 200% 100%
  -webkit-background-clip: text; background-clip: text; color: transparent
  animation: morphoShift 10s ease-in-out infinite
@keyframes morphoShift — 0%,100% background-position: 0% 50%; 50% background-position: 100% 50%. Pause under prefers-reduced-motion.

BLUR-FADE-UP ANIMATION (every element, staggered):

@keyframes blurFadeUp — From: opacity: 0; filter: blur(20px); transform: translateY(40px). To: opacity: 1; filter: blur(0); transform: translateY(0). The .animate-blur-fade-up class applies animation: blurFadeUp 1s ease-out forwards with initial opacity: 0. Each element gets a staggered animationDelay via inline style.

NAVBAR (z-index 50, relative):

Horizontal navbar, justify-between, padding px-4 sm:px-6 md:px-12 py-4 md:py-6. All nav text is dark on this light treatment: text-neutral-900.
Left: logo "Morpho" in Fraunces text-xl font-medium tracking-[-0.01em], with "FIELD JOURNAL" in Inter text-[11px] tracking-[0.28em] uppercase text-neutral-500 alongside. Blur-fade-up at 0ms.
Center (hidden below lg): links "Species", "Notes", "Plates", "About" — text-sm text-neutral-600 hover:text-neutral-900 transition-colors, staggered 100–250ms.
Right: a small "FREE" badge — rounded-full bg-[#2e6bff] text-white text-[11px] font-medium tracking-[0.14em] px-3 py-1 — next to a "Read the journal" liquid-glass pill (rounded-full, px-5 py-2, text-sm text-neutral-900) with a Lucide ArrowUpRight icon (size 16), blur-fade-up at 350ms. Hamburger below lg — w-10 h-10 rounded-full liquid-glass, animated Menu↔X (rotate-180, opacity, scale-50, duration-500 ease-out), icon text-neutral-800, blur-fade-up at 350ms.

MOBILE MENU (below lg):

Absolutely positioned dropdown top-[72px], z-40. Slides in translate-y-0 opacity-100 when open; -translate-y-4 opacity-0 pointer-events-none when closed; duration-500 ease-out. Background bg-[#f7f4ec]/90 backdrop-blur-lg, border-t border-b border-neutral-200 shadow-xl. Same 4 links in text-neutral-800, each py-3 px-3 rounded-lg hover:bg-neutral-100, staggered translate-x slide-ins (50ms steps). The FREE badge repeats in a bordered footer section.

HERO CONTENT (bottom of viewport):

A flex container flex-1 flex flex-col justify-end, padding px-4 sm:px-6 md:px-12 pb-10 md:pb-16, z-index 10. Copy here is dark (text-neutral-900 / neutral-600) over the light scrim.

Eyebrow — Inter text-[11px] tracking-[0.28em] uppercase text-neutral-500, mb-5, blur-fade-up at 300ms. Text: "OPEN JOURNAL · NO PAYWALL · ENTRY 041"

Metadata row — flex-wrap gap-x-6 gap-y-2 mb-6 md:mb-8, Inter text-[11px] tracking-[0.22em] uppercase text-neutral-500, blur-fade-up at 380ms. Three items, icon + label:
  Leaf icon (size 14) + "MORPHO DIDIUS"
  MousePointer2 icon (size 14) + "MOVE TO OBSERVE"
  MapPin icon (size 14) + "CANOPY, DAWN"

Headline — Fraunces, text-5xl sm:text-6xl md:text-7xl lg:text-8xl font-medium leading-[0.98] tracking-[-0.015em] text-neutral-900 mb-5, blur-fade-up at 450ms. Two lines: "Blue that" then "isn't there." where "isn't there." carries the .morpho-text class (make it italic Fraunces). Force the break with block spans.

Sub-line — Inter text-base sm:text-lg md:text-xl text-neutral-600 max-w-xl mb-8, blur-fade-up at 560ms. Text: "The colour is structure, not pigment — tilt the wing and it moves with you."

CTA row — flex flex-wrap gap-3 sm:gap-4:
  "Read the entry" — bg-neutral-900 text-white rounded-full font-medium px-6 sm:px-8 py-2.5 sm:py-3 text-sm, Lucide ArrowRight icon (size 16), hover:bg-[#2e6bff] transition-colors, blur-fade-up at 660ms.
  "Field notes" — rounded-full font-medium liquid-glass px-6 sm:px-8 py-2.5 sm:py-3 text-sm text-neutral-900, Lucide BookOpen icon (size 16), blur-fade-up at 760ms.

Bottom hint (right-aligned on md+, under CTAs on mobile) — Inter text-[10px] tracking-[0.26em] uppercase text-neutral-400 flex items-center gap-2, blur-fade-up at 860ms: MousePointer2 icon (size 12) + "MOVE TO SHIFT THE WINGS".

COLOR PALETTE:

Background canvas: warm cream #f7f4ec (used by the light scrim; page bg bg-[#f2efe6]).
Text: neutral-900 for headings, neutral-600 for the sub-line, neutral-500/400 for micro-labels.
Accent: #2e6bff (structural morpho blue) — appears in the iridescent headline word, the sheen layer, the FREE badge, the glass border stroke, and the primary CTA hover.
The only solid elements are the FREE badge (blue) and the "Read the entry" button (neutral-900, white text) until hover, where it flips to blue.

STAGGER TIMING SUMMARY:

Logo 0ms · Nav links 100/150/200/250ms · FREE badge + Read-the-journal 350ms · Hamburger 350ms · Eyebrow 300ms · Metadata row 380ms · Headline 450ms · Sub-line 560ms · Read-the-entry 660ms · Field-notes 760ms · Move-to-shift hint 860ms.

RESPONSIVE BREAKPOINTS:

Below sm (< 640px): headline text-5xl, tighter padding, metadata wraps over two rows, move-to-shift hint sits under the CTAs.
Below lg (< 1024px): nav links hidden, hamburger shown; cursor wing shift stays on for pointer devices, off for touch.
md and up: headline scales up, hint aligns bottom-right.
lg and up: full desktop navbar with all links visible; full cursor-reactive tilt and sheen range.
