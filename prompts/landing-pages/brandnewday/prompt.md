Build a scroll film called BRAND NEW DAY. React + Vite + @react-three/fiber + three. ONE page, ONE canvas, and no sections at all — a 2200vh track with a single sticky stage over it, and scrolling flies a camera through six acts. The entire argument of this build is that better transitions between sections cannot substitute for not having sections.

THE ONE RULE:
Every value in the scene is a PURE FUNCTION of one scalar `p` (0→1, the scroll position). No state, no springs, no lerping-toward-a-target inside the scene. Write `p` to a plain mutable object once per frame and have every useFrame read it. React must never re-render from scroll. The test that this is right: scrubbing backwards resolves to exactly the frame you saw scrubbing forwards.

Define an act axis `sp = clamp01(p / 0.82)`. Acts 1-5 run on `sp`; the closing wipe runs on real `p`.

COLOUR — a RED black, not a neutral one:
Three tiers: raw primitives, semantic roles, then bind. Primitives:
  --raw-ink-950 #150406   --raw-ink-900 #1e070a   --raw-ink-800 #2c0e13   --raw-ink-700 #431a20
  --raw-bone-50 #f2f3f5   --raw-bone-400 #9a8a8d   --raw-bone-500 #75666a
  --raw-scarlet-500 #e0202b   --raw-scarlet-300 #ff5d64   --raw-cobalt-500 #2b4fd0
Every ink step holds the same hue (~354deg) and only drops chroma, so the darkest field in the frame is the same colour as the accent rather than a grey the accent sits on top of. TWO accents, and they NEVER share a frame: scarlet belongs to the figure, cobalt to the room. Both at once reads as a colour-graded stock template.

THE FIGURE — an instanced bead cloud (act 1):
40,000 instanced spheres (r 0.5, 8x6 segments), positions sampled from the alpha of ONE masked portrait plate you supply — any figure cut out on transparency; draw it to a canvas, read getImageData, and keep a bead wherever alpha passes a threshold. 14 world units tall, centred at (0, 9, 0).
Bake the shade into instanceColor ONCE, not per frame. The form normal is the bead's offset from the FIGURE'S OWN axis (`n.set(x, y*0.15, z).normalize()`), never from the world origin — subtract the centre from itself and you get a degenerate radial and the whole cloud shades flat.
Then REMAP the sampled hue to the suit: rotate each bead to the nearer of scarlet (h 0.985) or cobalt (h 0.625), shortest arc, 85% pull, and keep its own lightness. Skip anything under S 0.12 — those are the specular highlights and tinting them costs you the only near-white in the figure. Remapping keeps the photograph's modelling; replacing the colour outright flattens 40,000 beads into one silhouette.
Idle: a whole-figure float plus a cursor tilt, with the compensating translation that keeps the pivot at the figure's own centre.

THE LATTICE (act 1) and THE GRID ROOM (act 2):
Lattice: a wireframe cage around the figure. Wireframe output is non-indexed vertex PAIRS, so give both vertices of a segment one SHARED random and an end parameter — that is what lets each segment draw itself from one end as a build scalar passes its own staggered threshold. ONE scalar weaves it and un-weaves it.
Room: three nested wireframe cylinders at r 9 / 13.95 / 19.8, rotateX(PI/2) so the axis runs down -Z, camera inside. Drift 0.055 / -0.03 / 0.014 — the far shell COUNTER-rotates, without which the three read as one rotating tube. Line colour cobalt at 0.22 opacity, depthWrite false. No ground plane: where a floor would be, fog is. Any finite plane shows its edge from some keyframe. One thin horizon bar only.

THE WEB — thwip strands and the swing (acts 2-3, and the thing that makes the middle worth scrolling):
ONE table drives BOTH the strands and the camera. Six entries, each `{ at, span, side, lead, radius, lift }`, spacing tightening across the run (0.045, 0.045, 0.038, 0.035, 0.031 of the act axis) so the corridor accelerates into the next act.
Anchors are DERIVED from the camera spine, `spine(at) + (side*radius, lift, -lead)`, never authored in world space, so they stay framed through any re-tune of the keyframes.
`lead ~= 3.8 * radius`, and that ratio is the whole of whether any of this is visible: it sets the anchor's angle off the view axis, atan(radius/lead), against a half-frame of ~29deg across and ~19deg up. Too short and every anchor sits at ~92% of the half-frame — technically on screen, hard against the edge, and invisible in practice.
Strand phases on its own local t: FIRE 0-0.12 (free end runs out to the anchor), TAUT 0.12-0.55 (near-zero sag — that is what taut means), RELEASE 0.55-0.80 (sag grows, a wave travels it), FADE 0.80-1.0.
Draw with LineSegments2 / LineSegmentsGeometry / LineMaterial — FAT lines. WebGL ignores `linewidth` on LineBasicMaterial outright and a one-pixel strand reads as a scratch on the lens. linewidth 2.4, screen-space, and set `material.resolution` or the width is wildly wrong. The instanced geometry's instanceStart/instanceEnd are two views on one interleaved buffer of stride 6 laid out [x1,y1,z1,x2,y2,z2] per segment, so write it in place every frame and never reallocate.
Strand colour is bone at gain 1.25 — deliberately OVER the bloom threshold so the core blows out and the post chain haloes it. Scarlet appears only as an impulse at the firing edge, and it MIXES rather than adds: added on top of a strand already above threshold it lands around (2.54, 1.22, 1.24) and ACES pulls all three channels to the same point, giving a bright knot with no hue in it.
Blending is ADDITIVE, and not for glow: the material carries one opacity for the whole object, so a per-strand fade has to live in the vertex colours — and under normal blending a colour fading to zero is a BLACK line on a red field rather than an absent one.
THE SWING: add a positional offset to the camera from the same table — lateral `side * 3.2 * sin(pi*u)`, a 1.5 dip so you pass under the anchor, and 0.15 rad of bank into the turn. Add it to POSITION ONLY, never to the look target: the camera then rotates to hold the axis while it translates, which is what makes an offset read as an arc. `u` runs 0.08-0.82 of each strand's life so consecutive windows OVERLAP and, since the sides alternate, the sum crosses zero instead of stopping at it — an S-weave. Every envelope is exactly zero at both ends, which is what lets the terms sum without leaving a permanent offset in every later act.

THE CAMERA:
Keyframes on `sp`, smoothstepped BETWEEN waypoints — but mark the legs from rest through the corridor LINEAR. Smoothstep has zero derivative at both ends, so a chain of smoothstepped legs brings the camera to a complete stop on every waypoint; three corridor waypoints then become three stutters instead of three changes of speed. Gear changes 300 -> 150 -> 360 units per unit of `sp`, stepping exactly where a strand catches and lets go. A speed change with nothing on screen causing it reads as a glitch; the same change with a strand pulling taut across it reads as a swing.
Bank by rotating the UP VECTOR about the view axis (Rodrigues) on a sin envelope, out to ~15deg mid-drop and BACK UPRIGHT by arrival. Guard the near-vertical case. Never a full roll. Set camera.rotation.order = 'YXZ'; the default XYZ leaks visible roll the moment both axes are non-zero.
Fog far closes for the wipe so the far end dissolves instead of showing an end wall.

ACT HANDOFF:
Six acts, every boundary OVERLAPPING its neighbour by 0.06-0.14 of the act axis. A boundary where exactly one act is live is a cut, and a cut is what makes a scroll film read as a slideshow. Expose the gate values on window in dev so the overlap can be PROVEN rather than asserted: at every boundary at least two must be non-zero at once.

THE POST CHAIN — order is the argument:
bloom -> vignette -> tone map (OutputPass) -> grain. Grain sits AFTER the output pass, in display space, which is where film grain actually lands; before the tone map the curve crushes it.
Bloom strength 0.55, radius 0.45, threshold 1.15, and set highPassUniforms.smoothWidth to 0.35 — the default 0.01 clips hard and hands the blur a cut-out, so what comes back is a rim tracing the shape rather than a glow spilling off it.
VIGNETTE: darkness 1.0 and NOT ABOVE. three's VignetteShader mixes toward vec3(1.0 - darkness), so 1.15 mixes toward -0.15, before the tone map, on a float target that keeps the negative — and ACES is a rational curve that maps negative inputs back to POSITIVE, per channel, so the channel that went furthest negative comes back brightest. On a neutral black every channel goes negative together and it still reads black; on a red field only G and B go negative and the corners come back GREEN. Shape the falloff with `offset` (1.3) instead.

THE DOM OVER IT:
Every overlay is position:absolute; inset:0; pointer-events:none, shown only in its own window by a smoothstep opacity ramp, visibility:hidden under 0.01. Only buttons re-enable pointer events. Put the overlay windows on the ACT axis, not on real `p` — with the DOM on `p` while the acts are on `sp`, every overlay fires roughly a third of the page late and each one plays to an empty frame.
Openings leave BACK-TO-FRONT, blurring as they go; closings arrive FRONT-TO-BACK, resolving out of blur. Per-letter spans, promoted once with will-change and backface-visibility, touching only transform/filter/opacity.

COPY — almost none:
Two phrases, repeated, and nothing else but the title. The copy stops being information and becomes rhythm, which forces the figure, the cage and the web to do all of the work. Resist writing sentences: a lyric that states something turns the acts into captions for it.

FLOORS (ship these, they are not optional):
prefers-reduced-motion keeps the strands and zeroes the swing amplitude — the strands are the graphic, the swing is the motion, and only one of those is what the setting asks about. Clamp DPR (1.0 on mobile, 1.5 desktop). Fewer SEGMENTS per strand on mobile, never fewer strands — the camera swings once per table entry, and a strand missing from a swing is exactly the desync one shared table exists to prevent. No horizontal overflow at 390px.
