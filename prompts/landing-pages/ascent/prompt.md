Build a scroll-scrubbed cinematic page for ASCENT — "Alpine equipment". ONE self-contained HTML file: inline <style>, inline <script>, Google Fonts via <link>. No build step, no framework. The only external asset is one video.

SCROLL MECHANIC — THE SCRUBBED VIDEO IS THE HERO:
There is NO autoplay hero above the scrub. The sticky stage is the FIRST element on the page.
- ONE <video>. NO autoplay attribute, NO loop attribute, and .play() is NEVER called.
- Frame 0 IS the landing state — on load the user sees currentTime = 0 as a still frame.
- Scroll position is the only thing that moves the video.
- The opening headline is the first caption beat (progress 0.00) on that same sticky stage.
If the video plays by itself on load you built two sections instead of one — start over.

Fetch the clip as a Blob and set src to URL.createObjectURL(blob): some hosts don't serve HTTP
byte-range requests, which pins video.seekable to [0,0] and freezes every seek.

THE VIDEO:
https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/ascent.mp4
<video id="film" muted playsinline preload="auto"></video> — absolute, inset 0, 100%/100%, object-fit cover. Set src from the Blob (see above). Show a minimal mono "Loading" overlay until 'loadeddata', then fade it out and set currentTime = 0.

STRUCTURE:
- <section class="stage"> is the FIRST element on the page, height 700vh, containing one position:sticky, top:0, height:100vh child.
- Inside the sticky child: the video, a vignette (inset box-shadow 0 0 220px 90px rgba(0,0,0,.85)), a top scrim (28vh, rgba(0,0,0,.82) to transparent), a bottom scrim (40vh, rgba(0,0,0,.92) to transparent), and the caption beats.
- Fixed chrome outside the stage: nav at the top (wordmark ASCENT, mono links Gear / Expeditions / Athletes / Store, outlined "Climb with us" pill), a scrub percentage + hairline rail bottom-left, and a spec row bottom-centre: 600m the wall / 9.2kN rated / 0 failures.
- After the stage, a short closing section with the solid "Climb with us" pill.

THE SCRUB LOOP (one requestAnimationFrame loop):
progress = clamp(-stageRect.top / (stageHeight - innerHeight), 0, 1)
Ease it: current += (target - current) * 0.12 — this is what makes the scrub glide rather than snap.
video.currentTime = current * (video.duration - 0.05), but only write when the delta exceeds 0.005 so you don't thrash the decoder.
Update the rail width and the two-digit percentage from the same value.

CAPTION BEATS — absolutely positioned, opacity 0, gaining .on when progress is inside the window:
- 0.00-0.14 (upper third): "Six hundred metres."
- 0.24-0.38 (lower): "Nothing below you but air."
- 0.72-0.88 (lower): "Gear that has never once let go."
Leave the middle band (roughly 0.40-0.70) EMPTY on purpose — the footage carries it alone. That silence is what makes it feel authored; do not fill it.

THEME: base #0d0904, single accent warm gold #e0a95c, ink near-white, hairlines rgba(255,255,255,.12). Headlines Inter Tight 500 at clamp(30px,4.6vw,64px), letter-spacing -.035em, with a heavy text-shadow so they read over the footage. Mono (JetBrains) for nav, specs, percentage.

RESPONSIVE: below 820px hide the nav links and the spec row.
REDUCED MOTION: drop the stage to auto height, make the sticky child static, show every beat at once, and give the video normal controls (still no autoplay).

VOICE: three short lines total across the whole scroll. The footage is the story.
