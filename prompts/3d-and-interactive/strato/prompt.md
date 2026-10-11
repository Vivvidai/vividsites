Build a full-viewport sneaker-drop hero section using React, Tailwind CSS, and Lucide React icons. Use the Inter Tight font (display) and IBM Plex Mono (readouts + micro-labels) from Google Fonts. The entire page is a single full-height hero — no scrolling, no additional sections. The CURSOR drives the motion: a hero sneaker floats center-stage and spins as the pointer moves. Brand / drop: STRATO.

CONCEPT:

STRATO — a hype sneaker drop. A single hero shoe hangs in a soft-lit studio haze, ice-blue rim light on it. Moving the cursor spins the shoe and parallaxes the whole scene; the shoe eases back to a hero angle at rest. Loud but clean, streetwear-gallery. One periwinkle-blue accent, tight modern grotesk, mono figures. The drop is FREE. Headline: "Reach the strato."

BACKGROUND VIDEO — CURSOR-REACTIVE AMBIENT:

The footage is an ambient loop of the hero sneaker slowly turning in studio haze. It plays full-bleed and fixed; the cursor spins it live on top.

Video URL: your provided hero sneaker footage (bundled asset: https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/strato.mp4)

Implementation:
- Video element: muted, autoPlay, loop, playsInline, object-cover, fixed full-bleed at z-index 0, inside a wrapper we transform.
- CURSOR-DRIVEN MOTION (rAF lerp + transform): a mousemove listener writes normalized target { x: (e.clientX/innerWidth)*2-1, y: (e.clientY/innerHeight)*2-1 } to a ref. A continuous requestAnimationFrame loop lerps a current ref toward target: cur.x += (target.x - cur.x) * 0.07; cur.y += (target.y - cur.y) * 0.07 (snappy but smooth). Each frame apply:
  - Video wrapper (the shoe): transform perspective(1200px) rotateY(cur.x * 16deg) rotateX(cur.y * -8deg) scale(1.06) — the sneaker spins toward the cursor in 3D.
  - Studio glow layer: transform translate3d(cur.x * 20px, cur.y * 16px, 0) so the rim light shifts with it.
  - A soft contact shadow under the shoe skews slightly with cur.x.
  On mouseleave, ease target back to {0,0} so the shoe returns to its hero three-quarter angle. On touch / no-hover, run a slow idle rotateY oscillation (sine of time). Cancel rAF on unmount.

STUDIO SCRIM (no flat wash):

Fixed full-screen overlay z-index 1, pointer-events-none:
- Bottom blur: backdrop-blur-xl gated by mask-image: linear-gradient(to top, black 0%, transparent 40%) (with -webkit- prefix).
- Ice floor glow: radial-gradient(130% 80% at 50% 100%, rgba(159,184,255,0.12), transparent 55%) — the accent pools up from the studio floor.
- Soft top haze: linear-gradient(to bottom, rgba(159,184,255,0.05), transparent 25%).

GRAIN:

Fixed pointer-events-none div z-index 2: fractal-noise SVG data-URI at opacity 0.05, mix-blend-mode: overlay.

FONT:

Import Inter Tight (weights 400, 500, 600, 700, 800) for display/body and IBM Plex Mono (weights 400, 500) via .font-mono for drop metadata, sizes, and readouts. Headline uses Inter Tight 800 with letter-spacing -0.04em, tight leading; emphasis word in .accent-text. NO sci-fi fonts.

REUSABLE .liquid-glass CLASS (exact):

background: rgba(255, 255, 255, 0.01); background-blend-mode: luminosity;
backdrop-filter: blur(4px); -webkit-backdrop-filter: blur(4px);
border: none; box-shadow: inset 0 1px 1px rgba(255,255,255,0.1);
position: relative; overflow: hidden;
::before — position: absolute; inset: 0; border-radius: inherit; padding: 1.4px;
background: linear-gradient(180deg, rgba(255,255,255,0.45) 0%, rgba(255,255,255,0.15) 20%, rgba(255,255,255,0) 40%, rgba(255,255,255,0) 60%, rgba(255,255,255,0.15) 80%, rgba(255,255,255,0.45) 100%);
-webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
-webkit-mask-composite: xor; mask-composite: exclude; pointer-events: none;

ACCENT GLASS VARIANT (.accent-glass) — same as .liquid-glass but ::before gradient uses periwinkle: linear-gradient(180deg, rgba(159,184,255,0.6) 0%, rgba(159,184,255,0.15) 30%, rgba(159,184,255,0) 50%, rgba(159,184,255,0.15) 75%, rgba(159,184,255,0.55) 100%) plus box-shadow: 0 0 40px -12px rgba(159,184,255,0.5). Used on the primary CTA.
.accent-text { color: #9fb8ff; text-shadow: 0 0 20px rgba(159,184,255,0.5), 0 0 48px rgba(159,184,255,0.24); }

SIGNATURE — TURNTABLE RING + FREE TAG:

- A centered decorative ring behind the shoe, z-index 4, pointer-events-none, mix-blend-mode: screen at low opacity: w-[64vmin] h-[64vmin] rounded-full border border-[#9fb8ff]/25 with 24 short radial ticks (like a shoe turntable dial), plus a faint inner dotted ring in [#9fb8ff]/15. It rotates gently with cur.x * 10deg.
- A bold "FREE" ribbon chip near the headline: bg-[#9fb8ff] text-black .font-mono text-xs font-bold uppercase tracking-[0.2em] px-3 py-1 rounded-full with @keyframes freePop pulse — 0%,100% scale(1); 50% scale(1.06) — 2.4s ease-in-out infinite.

@keyframes hueDrift for the studio glow: 0%,100% { opacity: 0.85; } 50% { opacity: 1; } — 6s ease-in-out infinite.

BLUR-FADE-UP ANIMATION:

@keyframes blurFadeUp { from { opacity:0; filter: blur(20px); transform: translateY(40px);} to { opacity:1; filter: blur(0); transform: translateY(0);} }
.animate-blur-fade-up { animation: blurFadeUp 1s ease-out forwards; opacity: 0; } — staggered inline animationDelay per element.

NAVBAR (z-index 50, relative):

justify-between, px-4 sm:px-6 md:px-12 py-4 md:py-6.
- Left: logo "STRATO" Inter Tight font-extrabold tracking-tight text-lg md:text-xl, with a small .font-mono "DROP 001" beneath in text-[10px] tracking-[0.3em] text-[#9fb8ff] uppercase. Delay 0ms.
- Center (hidden below lg): links "The Shoe", "Sizing", "The Drop", "Lookbook" — Inter Tight text-sm text-white/70 hover:text-white, delays 100/150/200/250ms.
- Right: glass CTA "Claim yours" rounded-full accent-glass px-5 py-2 .font-mono text-xs uppercase + Lucide Zap (size 16), delay 300ms. Below lg: w-10 h-10 liquid-glass hamburger (Menu/X crossfade rotate-180 scale-50 duration-500). Mobile menu: bg-[#05070f]/95 backdrop-blur-lg, border-y border-white/10, links slide-in stagger.

HERO CONTENT (bottom-anchored, over the shoe):

flex-1 flex flex-col justify-end px-4 sm:px-6 md:px-12 pb-12 md:pb-20 z-index 10, max-w-4xl.
- Metadata row (blur-fade-up 300ms), .font-mono text-[11px] sm:text-xs tracking-[0.2em] uppercase text-[#9fb8ff] flex-wrap items-center gap-3 sm:gap-6 mb-6, split by "·": "STRATO 001" · "US 4 — 14" · "LIMITED RUN". The FREE chip sits at the front of this row.
- Headline — Inter Tight 800 text-5xl sm:text-7xl md:text-8xl leading-[0.9] tracking-[-0.04em] mb-5, blur-fade-up 400ms. Text: "Reach the" on line one, "strato." in .accent-text on line two.
- Sub-line — Inter Tight text-base sm:text-lg md:text-xl text-white/65 max-w-xl mb-8 md:mb-10 font-light, blur-fade-up 520ms. Text: "The first STRATO drop — a lighter-than-air silhouette, ice on the rim light. Free while it lasts."
- CTA row — flex-wrap gap-3 sm:gap-4:
  "Claim yours — free" — bg-[#9fb8ff] text-black rounded-full font-semibold px-7 py-3 + Lucide ArrowRight (size 18), freePop pulse, hover:bg-[#b6c9ff], blur-fade-up 640ms.
  "Spin the shoe" — rounded-full liquid-glass px-7 py-3 .font-mono text-xs uppercase text-white + Lucide Rotate3d (size 18), blur-fade-up 740ms.
- Drop meta row (mt-7, blur-fade-up 840ms): .font-mono text-[10px] tracking-[0.2em] text-[#9fb8ff] flex gap-6, hidden below sm — three cells split by "/": "WEIGHT 218 g" / "DROP 8 mm" / "STOCK 500 PAIRS".
- Cursor hint (bottom, blur-fade-up 940ms): .font-mono text-[11px] tracking-[0.3em] text-white/40 "MOVE TO SPIN" + Lucide MousePointer2 (size 13).

COLOR PALETTE:
Background: deep blue-black studio #05070f (bg-[#05070f]) behind the fixed video.
Text: white, white/65 for the sub-line, white/45 for hints.
Accent (the ONE): periwinkle ice-blue #9fb8ff — logo tag, metadata, turntable ring, FREE chip, glowing headline word, and the single solid CTA.

STAGGER TIMING SUMMARY:
Logo 0ms · Nav links 100/150/200/250ms · Claim CTA 300ms · Hero metadata 300ms · Headline 400ms · Sub-line 520ms · Claim-free CTA 640ms · Spin CTA 740ms · Drop meta row 840ms · Cursor hint 940ms.

RESPONSIVE BREAKPOINTS:
Below sm (<640px): headline text-5xl, tighter padding, drop meta row hidden, CTAs stack full-width, turntable ring scales to 88vmin.
Below lg (<1024px): center nav links hide; hamburger + mobile menu appear; cursor spin active on hover devices (touch = idle rotateY oscillation).
md+ : full metadata + drop meta rows, larger Inter Tight headline, ring at 64vmin.
Respect prefers-reduced-motion: disable cursor 3D spin / parallax / freePop / hueDrift (hold the shoe at its hero angle), keep the video looping gently, reveal type with simple fades.
