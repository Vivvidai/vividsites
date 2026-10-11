SCROLL MECHANIC — THE SCRUBBED VIDEO IS THE HERO (read this first, it overrides anything below):
There is NO separate autoplay hero above the scrub. The page opens directly on the sticky
scroll-scrub stage — it is the FIRST element on the page, nothing sits above it.
- ONE <video> element for the whole page. Do not load the clip twice.
- The video has NO autoplay and NO loop attributes, and you NEVER call .play().
- Frame 0 IS the landing state: on load the user sees currentTime = 0 as a still frame.
- Scroll position is the only thing that moves the video.
- The hero copy (wordmark, headline, CTA) sits on top of that same sticky stage as the
  first caption beat (progress 0.00), not in a section above it.
If the video plays by itself on load, you built two sections instead of one — start over.

Build a long-scroll cinematic landing page for an industrial-design studio called GRAVEN / DRAFTING WORKS using React, Tailwind CSS, and Lucide React icons. Use the Inter Tight font (display/headings) and IBM Plex Mono (labels, annotations, specs) from Google Fonts. The page is a tall scroll experience: one video is pinned full-bleed while the viewer scrolls, and scroll scrubs the video's playhead so a technical blueprint sheet drawing itself into being — lines tracing, dimensions appearing, an object resolving on the draft — plays out as you scroll. Cool, precise, draughtsman's treatment; steel-grey lines on deep ink.

CONCEPT:

GRAVEN / DRAFTING WORKS — a studio that draws objects before they are built. The footage is a blueprint sheet coming to life; scroll traces the draft from a blank ground to a finished, dimensioned drawing. Everything reads like a drawing board: hairline rules, mono annotations, a single steel accent, generous whitespace on dark.

BACKGROUND VIDEO — STICKY SCROLL-SCRUBBED:

The footage is NOT autoplayed on a loop. It is scrubbed by scroll. Build it like this:

- A tall outer container: <section> with height 500vh (h-[500vh]) and position: relative. This is the scroll track.
- Inside it, a sticky viewport: a div with position: sticky; top: 0; height: 100vh; width: 100%; overflow: hidden. The video and all pinned text beats live here.
- The <video> is object-cover, absolutely positioned, w-full h-full, inset-0, z-index 0. Attributes: muted, playsInline, preload="auto", crossOrigin="anonymous". NO autoPlay, NO loop, NO controls.
- Scroll-scrub logic: on scroll, compute progress = clamp((-rect.top) / (rect.height - window.innerHeight), 0, 1) where rect is the outer container's getBoundingClientRect(). Map to targetTime = progress * video.duration. Apply DAMPING via requestAnimationFrame: current += (target - current) * 0.1 each frame, then set video.currentTime = current only when Math.abs(target - current) > 0.01 (guard readyState >= 2 and isFinite(duration); try/catch for iOS). Smooth, deliberate, like a hand drawing.
- Guard the duration: only scrub after loadedmetadata fires and video.duration is finite.

Video URL: your provided blueprint sheet footage (bundled asset: https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/graven.mp4)

BLUEPRINT GRID + COLD SCRIM:

Fixed pointer-events-none overlays behind the text, above the video:
- Grid overlay z-index 1, opacity 0.10: two repeating-linear-gradients (90deg and 0deg) of rgba(154,164,174,0.5) 1px lines every 40px, so a faint drawing-board grid sits over the footage.
- Text-readability scrim z-index 2: a bottom mask over backdrop-blur-sm — mask-image: linear-gradient(to top, black 0%, transparent 42%) — keeps low text crisp without lifting the ink around the drawing.

FONT:

Import Inter Tight (weights 300–600) for display headings and body; IBM Plex Mono (weight 400) for kickers, annotations, dimension labels, and spec cells. Set font-family: 'Inter Tight', sans-serif on the body. Headings use Inter Tight font-light with letter-spacing -0.03em. Mono labels are uppercase, text-[11px] tracking-[0.28em].

GRAIN:

Fixed pointer-events-none div z-index 3, opacity 0.05, mix-blend-mode: overlay, inline SVG feTurbulence data-URI (fractalNoise, baseFrequency 0.9) — keeps the ink ground from banding.

REUSABLE .liquid-glass CLASS (exact):

background: rgba(255, 255, 255, 0.01); background-blend-mode: luminosity;
backdrop-filter: blur(4px); -webkit-backdrop-filter: blur(4px);
border: none; box-shadow: inset 0 1px 1px rgba(255,255,255,0.1);
position: relative; overflow: hidden;
::before — position: absolute; inset: 0; border-radius: inherit; padding: 1.4px;
background: linear-gradient(180deg, rgba(255,255,255,0.45) 0%, rgba(255,255,255,0.15) 20%, rgba(255,255,255,0) 40%, rgba(255,255,255,0) 60%, rgba(255,255,255,0.15) 80%, rgba(255,255,255,0.45) 100%);
-webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
-webkit-mask-composite: xor; mask-composite: exclude; pointer-events: none;

SIGNATURE — DRAWN RULES + DIMENSION LINES:

.rule { height: 1px; background: linear-gradient(90deg, transparent, rgba(154,164,174,0.8), transparent); }
.rule-v { width: 1px; background: linear-gradient(180deg, transparent, rgba(154,164,174,0.65), transparent); }
.dim-label { color: #9aa4ae; font-family: 'IBM Plex Mono'; letter-spacing: 0.28em; }
Use thin .rule dividers under kickers and .rule-v between spec cells so the layout looks traced on the same board.

ANIMATIONS:

@keyframes blurFadeUp — From: opacity 0; filter: blur(20px); transform: translateY(40px). To: opacity 1; filter: blur(0); transform: translateY(0). Class .animate-blur-fade-up: animation: blurFadeUp 1.1s ease-out forwards; initial opacity 0. Stagger via inline animationDelay.
@keyframes drawLine — from { transform: scaleX(0); } to { transform: scaleX(1); } (transform-origin: left) so every .rule "draws" in when a beat reveals — like a line pulled across the sheet.
Each scroll beat's text fades in on enter (IntersectionObserver, threshold 0.4, add .animate-blur-fade-up once) and its rules run drawLine. Beats are keyed to scroll-progress windows so only one reads at a time.

NAVBAR (fixed, z-index 50):

Horizontal navbar, justify-between, px-4 sm:px-6 md:px-12 py-4 md:py-6, fixed top-0 w-full backdrop-blur-md.
- Left: logo "GRAVEN" in Inter Tight text-lg md:text-xl tracking-[0.12em] font-light, with a "/ DRAFTING WORKS" tag in IBM Plex Mono text-[10px] tracking-[0.3em] text-[#9aa4ae] beside it (hidden below sm). blur-fade-up 0ms.
- Center (hidden below lg): links "Work", "Method", "The Studio", "Contact" — Inter Tight text-sm text-white/70 hover:text-white transition-colors. Stagger 100–250ms.
- Right: one glass CTA — rounded-full liquid-glass px-5 py-2 text-sm text-white "Start a drawing" with Lucide PenLine icon (size 16). blur-fade-up 300ms. Below lg: w-10 h-10 liquid-glass hamburger (Menu↔X crossfade rotate-180 scale-50 duration-500).

SCROLL PROGRESS RAIL (right edge, desktop only, hidden below lg, z-index 40):

A fixed vertical track right-6 top-1/2 -translate-y-1/2, h-40 bg-white/10 with a filling bar bg-[#9aa4ae] whose height = progress * 100%. An IBM Plex Mono label below shows the current beat name in text-[10px] tracking-[0.25em] uppercase text-white/45.

HERO BEAT (first viewport, low-left):

Inside sticky viewport, z-index 10, flex-col justify-end items-start text-left pb-20 md:pb-28 px-4 sm:px-6 md:px-12 max-w-3xl.
- Metadata row (blur-fade-up 300ms), IBM Plex Mono text-[11px] tracking-[0.24em] uppercase text-white/50 flex-wrap gap-x-6 gap-y-2 mb-6: Ruler icon (size 14) + "SCALE 1:1", PencilRuler icon (size 14) + "SHEET 01 OF 06", Sparkles icon (size 14) + "REV. A".
- A thin .rule ~120px above the headline (drawLine).
- Kicker: "GRAVEN / DRAFTING WORKS" IBM Plex Mono text-[11px] tracking-[0.32em] uppercase text-[#9aa4ae] mb-4.
- Headline "Drawn before it's built." — Inter Tight text-5xl sm:text-6xl md:text-7xl lg:text-8xl font-light tracking-[-0.03em] leading-[0.95], "Drawn" in .dim-label-colored span (color #9aa4ae). blur-fade-up 450ms.
- Sub-line — Inter Tight text-base sm:text-lg text-white/60 max-w-lg mt-5: "Every object begins as a line. Scroll to watch the draft take shape." blur-fade-up 560ms.
- Scroll cue: "SCROLL TO TRACE" IBM Plex Mono text-[11px] tracking-[0.3em] text-white/40 + Lucide ChevronsDown gentle bounce, mt-8. blur-fade-up 680ms.

SCROLL BEATS (4 — full-height sections stacked after the sticky video, alternating sides, z-index 10; the drawing keeps scrubbing behind). Each: a mono kicker with a drawn .rule beneath, an Inter Tight heading, one sub-line, and a 3-cell spec row divided by .rule-v hairlines (IBM Plex Mono values + dim labels).

BEAT 1 — THE SHEET (left) · progress 0.06–0.28:
Kicker "01 · THE SHEET".
Heading "A blank field." Sub "It starts with nothing but a border and a title block — the whole object still only an intention."
Spec: "SIZE · A1" | "MEDIUM · vellum" | "MARKS · 0".

BEAT 2 — THE FRAME (right) · progress 0.30–0.52:
Kicker "02 · THE FRAME".
Heading "Lines find their order." Sub "Construction lines lay down the geometry — axes, centres, and the bones the drawing will hang on."
Spec: "AXES · 3" | "TOLERANCE · ±0.1mm" | "PROJECTION · first-angle".

BEAT 3 — THE SECTION (left) · progress 0.54–0.76:
Kicker "03 · THE SECTION".
Heading "Cut it open." Sub "A section reveals the inside — hatching, wall thickness, and how every part meets the next."
Spec: "CUT · A–A" | "HATCH · 45°" | "WALL · 2.4mm".

BEAT 4 — THE BUILD (centered, final) · progress 0.78–1.00:
Kicker "04 · THE BUILD".
Heading "Ready to make." — "make" in span color #9aa4ae. Sub "Fully dimensioned, checked, and signed. The line becomes a thing you can hold."
Spec: "STATUS · released" | "CHECKED · yes" | "SHEETS · 6".
Final CTA row: "See the work" (bg-[#9aa4ae] text-[#0c0f13] rounded-full px-7 py-3 font-medium + Lucide ArrowRight) + "Read the method" (rounded-full liquid-glass px-7 py-3 text-white + Lucide BookOpen). blur-fade-up staggered.

FOOTER (after the tall container, solid bg #0c0f13):
Full-width .rule, then px-6 md:px-12 py-10 flex flex-col sm:flex-row justify-between gap-4 text-xs text-white/40: left "GRAVEN — DRAFTING WORKS · SHEET SET 0001", right "Work · Method · Studio · Contact". Small logo repeated.

COLOR PALETTE:

Background: deep drafting-ink #0c0f13 (bg-[#0c0f13]).
Text: white, white/60–white/70 for sub-copy and labels.
Accent (only color): #9aa4ae (steel/draughtsman grey) — kickers, drawn rules, dimension labels, the emphasis words, the one solid CTA, and the progress bar.

STAGGER TIMING SUMMARY:

Intro: Logo 0ms · Nav links 100/150/200/250ms · Start-a-drawing 300ms · Hero metadata 300ms · Hero kicker 380ms · Headline 450ms · Sub-line 560ms · Scroll cue 680ms.
Per beat (on intersect): kicker 0ms · rule draw 120ms · heading 200ms · sub 320ms · spec row 440ms · (Beat 4 CTAs 560/680ms).

RESPONSIVE BREAKPOINTS:

Below sm (<640px): headline text-5xl, "/ DRAFTING WORKS" logo tag hidden, metadata wraps over two rows, spec rows stack to 1 col with horizontal .rule dividers instead of vertical.
Below lg (<1024px): center nav links hidden (hamburger → bg-[#0c0f13]/95 backdrop-blur dropdown with the 4 links), scroll progress rail hidden, beats tighten padding.
md+ : alternating beat sides, larger display sizes, vertical .rule-v spec dividers.
Reduce scroll container to h-[360vh] below md. Respect prefers-reduced-motion: skip the damped scrub (seek directly), draw rules instantly, reveal beats without blur, and drop grain motion.
