Build a premium cinematic hero page for FROST — "Cold-brewed, canned". ONE self-contained HTML file: inline <style>, inline <script>, Google Fonts via <link>. No build step, no framework. The only external asset is one background video.

VIDEO BEHAVIOUR — PLAY ONCE, THEN HOLD (do not loop):
The clip plays through exactly once on load and then FREEZES on its final frame and stays there.
- The <video> has NO `loop` attribute.
- Call .play() once on 'canplay' and on window load (catch and ignore rejections).
- On 'ended': pause it and pin currentTime to (duration - 0.05) so it holds the last frame.
A looping clip re-cuts to frame 1 and reads as a cheap GIF. Playing once and resolving reads as film.

BLACK DROPS OUT: the footage sits on a dark background, so set `mix-blend-mode: screen` on the
<video> and paint a warm/tinted gradient underneath. The subject then floats over your own
background instead of a flat black box.

BACKGROUND VIDEO:
<video id="film" src="https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/frost.mp4" muted playsinline preload="auto"></video>
position absolute, inset 0, width/height 100%, object-fit cover, mix-blend-mode screen.
NOTE: no `autoplay` attribute and no `loop` attribute — the script starts it once and holds the end.

STRUCTURE — a single 100vh screen, no scrolling:
- A fixed grain layer (inline SVG feTurbulence, opacity .04, mix-blend-mode screen).
- The video, then a .glow gradient beneath it: radial-gradient(56% 46% at 50% 46%, ice cyan #5fd4ff22, transparent 68%) over a linear-gradient that fades to deep ocean #04101a at top and bottom. Then a vignette: inset box-shadow 0 0 210px 80px rgba(0,0,0,.82).
- Nav across the top: the wordmark FROST in Inter Tight 600 at .22em tracking, four mono uppercase links (The brew / Stockists / Wholesale / About), and an outlined "Find a stockist" pill with a ice cyan #5fd4ff border.
- Centred hero: a mono uppercase kicker "Cold-brewed, canned" in ice cyan #5fd4ff, then the H1, then the sub-line, then a solid CTA pill.
- A spec row pinned near the bottom, divided by hairlines: 20h steeped / 2°C sealed / 0g sugar — figures in ice cyan #5fd4ff, labels in dim mono caps.

COPY:
- H1 (Inter Tight 500, clamp(40px,6.4vw,88px), line-height 1.0, letter-spacing -.035em): "Cold. Then colder." — set the last word/phrase in ice cyan #5fd4ff.
- Sub-line (max 470px, 15px, rgba white .60): "Brewed twenty hours, sealed the same morning."
- CTA: "Find a stockist"

THEME: base deep ocean #04101a, single accent ice cyan #5fd4ff, ink near-white, hairlines rgba(255,255,255,.12). ONE accent only — it appears on the kicker, the highlighted words, the spec figures and the CTA border. Everything else is ink or dim.

FONTS: Inter Tight (500/600) for the wordmark and H1; Inter (400/500) for the sub-line; JetBrains Mono (400/500) for the kicker, nav links, and spec labels — all uppercase with wide letter-spacing.

MOTION: staggered blur-rise entrance — from opacity 0, blur(16px), translateY(26px) to clear, .95s cubic-bezier(.2,.7,.2,1), delays: wordmark 0ms, nav CTA 280ms, kicker 360ms, H1 460ms, sub 620ms, CTA 760ms, specs 920ms.

RESPONSIVE: below 820px hide the nav links and wrap the spec row.
REDUCED MOTION: disable the entrance animation, and give the video normal controls instead of autoplaying it.

VOICE: restrained and specific. One clear promise, one action. No brochure copy — the film carries the emotion.
