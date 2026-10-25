# Build spec: FOLDWORLD — the carousel pop-up book of Odile Penhallow, a fictional paper engineer: a teal cloth-bound cover tied with a pink ribbon shows the live paper book turning on a craft table through a round die-cut window, and "Untie & open" slides the ribbon off, swings the boards open like gatefold doors and flies the camera down into a six-bay star of colour-blocked paper rooms that you turn one chapter at a time with scroll, drag or swipe, whose cut-out props wiggle under the cursor, hop when clicked and unfold paper cards

Recreate this site as a single HTML file: one `index.html`, three.js r169 (0.169.0, `three.module.js`) from jsDelivr through an
import map, with five addons from the same version (`EffectComposer`, `RenderPass`, `GTAOPass`, `ShaderPass`, `OutputPass`),
Pixelify Sans and Gaegu from Google Fonts, fifteen hosted files (six 2048 × 2048 cut-out prop atlases and the JSON of their traced
outlines, a bookcloth, a rag paper, a cardstock detail map, two paper normal maps, a birch table, a designed no-WebGL still, and a
hosted copy of the page's module for checking only), and everything else written in the file: a CSS cloth-bound cover that is also
the loader, whose six pop-up triangles fold upright on real load progress, with a round die-cut window cut through both boards by
a mask, a split paper label, a ribbon, a bow and a hanging tag; a classic-script watchdog that can always lift the cover; a
three.js scene of a carousel book on a lazy susan, six 60° bays between radial page walls, each bay a tunnel book of die-cut
layers (a pegboard, an island and four sea strips, rolling hills, a skyline with punched windows, a glasshouse frame with arched
panes and a fan light, a pigeonhole wall); 120 traced cut-out props that the scene extrudes to card thickness from the atlases;
canvas-drawn chapter signs hung on pink threads among bunting; pendulum hangers that swing with the turn's acceleration;
per-chapter motion (a rocking sea, a bobbing boat and whale, a flickering lantern that really lights its bay, fireflies, a tram on
rails, flapping butterflies, paper planes looping round chapter six); a craft table with a giant pencil, a spool of pink thread, a
ruler and paper scraps; a gradient backdrop dome and floating dust; MSAA, GTAO and a hand-written grade pass; a canvas deckled
paper frame round the viewport; a virtual, endlessly looping turn with inertia and a directional page snap; occlusion-correct
hover picking with spring wiggles, click hops and a folding paper card; chapter tabs, a three-step zoom and a colophon in which
the live scene shrinks to a mounted photograph. One requestAnimationFrame loop drives the scene, the camera and every spring with
exponential easing and explicit spring integration; the cover, the card and the colophon are CSS transitions switched by classes
on `<html>`; no tween library, no scroll library, no build step, no framework. Every number below is the shipped build's, and the
code is quoted whole.

## What it is
Foldworld is the carousel pop-up book of Odile Penhallow, a fictional paper engineer, opened on a craft table as one live paper
diorama in six colour-blocked chapters. A teal cloth cover tied with a pink ribbon shows the book turning through a round die-cut
window, and "Untie & open" swings the boards apart and flies you down into chapter one, where scroll, drag or swipe turns the next
little room round.

The whole page is the book: the document never scrolls, every input turns the paper world, and the only other things on screen are
small pieces of chrome round a deckled cream mat.
- **The cover (loader and title card).** Two teal bookcloth boards, each 50.2% of the width, meet at the centre, with ruled
  borders and cream rag-paper corner protectors. A round window (`--wr` 118 px radius, its centre at `--wy` 31% of the height)
  is cut through both boards by a CSS radial mask and edged by a 14 px rag-paper ring with a dashed stitch; through it you see
  the real 3D book turning slowly on its table. Below it a cream rag label reads `a carousel book in six chapters` /
  **Fold·world** (the middle dot in pink) / `by Odile Penhallow, paper engineer` / `FOLDING 000`. The label, the ring and the
  ribbon are drawn twice, each half clipped by its own board, so they split when the boards open. While the files load, six
  small pop-up triangles in the six chapter colours stand up one by one across the window as the count climbs; at 100 they fade
  and a pink bow with tails, a 30 px pink grosgrain ribbon right across the cover and a cream tag `Untie & open` become
  clickable. The foot reads `~ scroll, drag or swipe to turn the pages ~` and an underlined `colophon & credits`.
- **The opening.** "Untie & open" (or the bow) flings the bow up and away, slides the two ribbon halves off left and right, then
  at 420 ms swings both boards open 100° about their outer edges over 1.5 s, shading them as they turn. 350 ms after the click
  the camera starts a 2.4 s cubic in-out flight from the window view (22 units back, a narrow lens, the projection offset so the
  book sits in the window) down to chapter one with a dolly-zoom, while the book swings from its idle turn to the first bay. At
  1.9 s the cover is gone and the chrome fades in.
- **The book.** A cream mount-board disc on a teal cloth band foil-stamped in gold, `FOLDWORLD ✶ A CAROUSEL BOOK IN SIX CHAPTERS
  ✶ ODILE PENHALLOW ✶ PAPER ENGINEER ✶`, round the base, a teal spine, and six radial page walls whose tops swoop from 2.75 at
  the rim to 3.3 at the spine. The camera stands outside the star and looks into one bay at a time; the neighbouring bays show
  at the sides.
- **The six chapters**, each with a handwritten sign on a pink thread across the front of the bay (its title in Pixelify Sans in
  the chapter's ink, key words picked out in pink), bunting, and Odile herself in a different pose:
  - **I The Workbench** (ochre): a green cutting-mat floor, a pegboard of punched holes hung with scissors, thread and
    pencils, a pop-up desk with the arm lamp, pencils, tea and a cactus, Odile cutting paper, Mouse the cat, a book stack, a
    spool, scissors on the floor, two wall shelves, and a paper crane on the thread.
  - **II The Tide Book** (teal): a paper sun and clouds on the walls, an island with a lighthouse, four rocking sea strips
    with foam, a bobbing sailboat, a rising whale, a buoy, Odile rowing on the sand, a beach hut, a crab, starfish, a rowing
    boat, and two gulls on threads.
  - **III The Night Orchard** (indigo): a moon and foil stars, four rolling hills, poplars and apple trees, Professor the owl,
    toadstools, a sleeping fox, a hedgehog, a rabbit, Odile with a lantern that really lights the bay and flickers, 44
    fireflies, and a lantern and stars on the thread.
  - **IV Market Street** (tomato): a cobbled floor with tram rails, two cut-paper skylines with punched windows and a warm
    glow behind them, townhouses and a bakery, a tram that rolls to and fro, a street lamp, Odile waving, a bicycle, a flower
    cart, a dog, a pigeon and oranges.
  - **V The Glasshouse** (sage): a checker-tiled floor, leafy layers, a die-cut glasshouse frame (eight panes, the upper row
    arched, and a fan light in the gable), monsteras, ferns, two sunflowers, a tall cactus, toadstools, a wheelbarrow, Odile
    with a watering can, a snail, and two butterflies flapping on an inner thread.
  - **VI The Post Room** (rose): a pigeonhole wall of 4 × 5 holes with letters in most of them, the letter desk, potted
    plants, Odile posting a letter, a satchel, parcels, letters, a dove on the wall, two paper planes looping round the room,
    and envelopes and a dove on the thread.
- **The turn.** Scroll, drag (mouse or touch, with inertia) or the arrow, Page and Space keys turn the book; it eases toward the
  target at k = 4.6/s, loops for ever, and after 0.9 s at rest settles on a page, moving one page in the direction of any nudge
  over 3.5%. Hanging things swing with the turn's acceleration; Odile and the plants sway; the camera leans a little with the
  cursor.
- **Touching it.** On a mouse, a prop under the cursor wiggles on a spring and a cream tag follows the pointer with its name
  (`Mouse the cat`, `a paper crane`…) and, if it has a story, a pink `open ↗`. A click (or a tap on a phone) hops the prop and,
  for the 17 props with a story, unfolds a paper card: a top half in the chapter colour with the prop's art folds down onto a
  lower half with the chapter, a title and a short story.
- **Chrome**: the wordmark `Fold·world` with `Odile Penhallow, paper engineer` top left; a cream `Colophon` tag on a pink thread
  top right (it swings on hover); the six coloured index tabs I–VI and the chapter name (`chapter one` / `The Workbench`) bottom
  left, the active tab taller with a pink underline; a cream zoom pill (−, a magnifier, three level dots, +) bottom right; and
  the hint `~ scroll, drag or swipe to turn the book ~` bottom centre until the first turn., inside a deckled cream mat 10 px
  wide.
- **The colophon.** The live scene shrinks to half size, tips −2.2° and slides left onto a rag-paper page as a mounted
  photograph with a 14 px cream border and four black photo corners, while `Colophon.` and four short paragraphs fade in on the
  right.

The palette: the six chapter walls are ochre `#c9973f`, tide teal `#3f7f7b`, night indigo `#3d4672`, tomato `#c4583f`, glasshouse
sage `#8aa27a` and post-room rose `#c27a86`, set on cream board `#f3ead8` / paper `#e9dfcb` with warm ink `#2a2622`, the cover in
bookcloth teal `#2c5653`, and ONE spark, riso fluoro pink `#ff4f8b` (deep `#d8336f` for text on paper), on every thread and pin,
the ribbon and bow, the wordmark's dot, the active tab and highlighted words.

## Shell, libraries, fonts
The head is the build's. The page waits for the fonts (up to 5 s) before it draws the signs and the base band onto canvases.
```html
<!doctype html>
<html lang="en">
<head>
<meta charset="utf-8">
<meta name="viewport" content="width=device-width, initial-scale=1, viewport-fit=cover">
<meta name="theme-color" content="#2c4f4c">
<title>Foldworld · the carousel book of Odile Penhallow</title>
<meta name="description" content="Foldworld: a six-chapter paper carousel book by Odile Penhallow, paper engineer. Turn it with scroll, drag or swipe.">
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Gaegu:wght@400;700&family=Pixelify+Sans:wght@400..700&display=swap" rel="stylesheet">
<style>
/* the tokens and the whole stylesheet below */
</style>
</head>
```
At the end of `<body>`, in this order: the classic watchdog script (quoted below in its own section), the import map, then ONE
inline module holding every system, in the order of the sections below. The module tag keeps the build's `onerror`: if three.js or
an addon cannot be fetched, the module graph fails and the cover falls back to the still at once (the watchdog also catches it
after 10 s).
```html
<script>/* the watchdog */</script>
<script type="importmap">
{"imports":{"three":"https://cdn.jsdelivr.net/npm/three@0.169.0/build/three.module.js","three/addons/":"https://cdn.jsdelivr.net/npm/three@0.169.0/examples/jsm/"}}
</script>
<script type="module" onerror="window.__fwFail&&__fwFail('module failed to load')">
/* … the module, every section from "Module prelude" to "Boot" … */
</script>
</body>
</html>
```
Faces: **Pixelify Sans** 400–700 (`--pix`: the wordmark, the label title, the tabs, the chapter name, the tags, the zoom glyphs,
card titles and kickers, the colophon heading, sign titles, the base band and the ruler numbers) and **Gaegu** 400/700 (`--hand`:
the body face, the sign copy, card copy, the colophon text, the hint and the cover foot). Pixelify Sans has no `fi` / `fl` / `ff`
glyph, so canvas text puts a zero-width non-joiner between those pairs. There is no favicon and no Lenis.

## Tokens and root
One flat tier of tokens. The body never scrolls (`overflow:hidden`, `touch-action:none`, `overscroll-behavior:none`); every
gesture is read by the script.
```css
:root{
  --ink:#2a2622; --cream:#f3ead8; --paper:#e9dfcb; --spark:#ff4f8b; --spark-d:#d8336f;
  --cloth:#2c5653; --cloth-d:#1d3c3a;
  --c0:#c9973f; --c1:#3f7f7b; --c2:#3d4672; --c3:#c4583f; --c4:#8aa27a; --c5:#c27a86;
  --ui:#f7f0e2; --pix:'Pixelify Sans', ui-monospace, monospace; --hand:'Gaegu', 'Comic Sans MS', cursive;
}
*{box-sizing:border-box;margin:0;padding:0}
html,body{height:100%;overflow:hidden;background:#3b322b;color:var(--ui);-webkit-tap-highlight-color:transparent}
body{font-family:var(--hand);overscroll-behavior:none;touch-action:none;-webkit-font-smoothing:antialiased}
button{font:inherit;color:inherit;background:none;border:0;cursor:pointer}
a{color:inherit}
```

## The whole stylesheet
Quote it as is, the phone and short-screen rules included. Layers: the stage (the WebGL canvas, or the still) under the deckled
frame canvas (z 40), the chrome (45) and the cursor tag (46); the colophon page (30) slides under the shrunk stage (31) and its
photo corners (32); the cover (60) and the card (70) sit above everything. The cover's die-cut window is two masks: the left
board's circle is centred at `50vw`, the right board's at `.2vw` of its own box (it starts at 49.8vw), so the hole is one circle
across the seam. Short screens move the window up so the ribbon, bow and tag clear the foot: above 760 px wide and under 900 px
tall `--wy` becomes `min(31%, 100% − 469px − --wr)` (and `--wr` 92 px under 760 px tall); the foot then hides its hint line
(`font-size:0`, the `<br>` dropped) and keeps only the colophon link 14 px off the bottom.
```css
/* ---------- stage ---------- */
#stage{position:fixed;inset:0;transform-origin:50% 50%;transition:transform .9s cubic-bezier(.7,0,.2,1),border-radius .9s;will-change:transform;overflow:hidden;background:#3b322b}
#gl{position:absolute;inset:0;width:100%;height:100%;display:block;outline:none}
#still{position:absolute;inset:0;background:#3b322b url(https://www.vividsites.app/media/flagship/foldworld/still.jpg) center/cover no-repeat;display:none}
#still p{position:absolute;left:50%;bottom:118px;transform:translateX(-50%);background:var(--cream);color:var(--ink);font:700 19px/1.2 var(--hand);padding:10px 18px;border-radius:3px;box-shadow:0 6px 18px rgba(0,0,0,.28);text-align:center;width:max-content;max-width:86vw}
html.nogl #still{display:block}
html.nogl #gl{display:none}
html.nogl #chap,html.nogl #zoom,html.nogl #hint{display:none}
#frame{position:fixed;inset:0;width:100%;height:100%;pointer-events:none;z-index:40}

/* ---------- chrome ---------- */
.chrome{position:fixed;z-index:45;opacity:0;transition:opacity .8s .2s}
html.open .chrome{opacity:1}
#mark{left:30px;top:24px;text-shadow:0 1px 2px rgba(0,0,0,.35),0 0 18px rgba(30,20,10,.25)}
#mark b{display:block;font:600 23px/1 var(--pix);letter-spacing:.01em}
#mark b i{font-style:normal;color:var(--spark)}
#mark span{display:block;font:700 16px/1.1 var(--hand);margin-top:5px;opacity:.92}
#colo{right:28px;top:20px;display:flex;align-items:center;gap:0;transform-origin:100% 50%}
.tag{position:relative;background:var(--cream);color:var(--ink);font:500 15px/1 var(--pix);padding:9px 14px 9px 24px;clip-path:polygon(12px 0,100% 0,100% 100%,12px 100%,0 50%);box-shadow:0 2px 0 rgba(0,0,0,.15)}
.tag::before{content:"";position:absolute;left:10px;top:50%;width:6px;height:6px;margin-top:-3px;border-radius:50%;background:#3b322b;box-shadow:inset 0 0 0 1.5px rgba(0,0,0,.25)}
.tagwrap{filter:drop-shadow(0 3px 5px rgba(20,10,0,.3))}
#colo .string{width:26px;height:2px;background:var(--spark);margin-right:-3px;border-radius:2px}
#colo:hover .tagwrap{animation:swing 0.9s cubic-bezier(.3,1.6,.4,1)}
@keyframes swing{0%{transform:rotate(0)}30%{transform:rotate(-7deg)}60%{transform:rotate(4deg)}100%{transform:rotate(0)}}
#chap{left:30px;bottom:26px;display:flex;align-items:flex-end;gap:16px}
#tabs{display:flex;align-items:flex-end;gap:4px;height:34px}
#tabs button{width:30px;height:24px;border-radius:5px 5px 2px 2px;font:600 11px/1 var(--pix);color:rgba(255,250,240,.92);position:relative;transition:height .45s cubic-bezier(.3,1.5,.4,1),transform .3s;box-shadow:inset 0 -2px 0 rgba(0,0,0,.18),0 2px 4px rgba(0,0,0,.25)}
#tabs button.on{height:34px}
#tabs button.on::after{content:"";position:absolute;left:5px;right:5px;bottom:-7px;height:3px;border-radius:2px;background:var(--spark)}
#tabs button:hover{transform:translateY(-3px)}
#chapname{font:500 17px/1 var(--pix);text-shadow:0 1px 2px rgba(0,0,0,.4);white-space:nowrap;padding-bottom:4px;min-width:16ch}
#chapname small{display:block;font:700 15px/1 var(--hand);opacity:.85;margin-bottom:5px}
#zoom{right:28px;bottom:24px;display:flex;align-items:center;gap:2px;background:var(--cream);color:var(--ink);border-radius:20px;padding:4px;box-shadow:0 3px 8px rgba(20,10,0,.3)}
#zoom button{width:30px;height:30px;border-radius:50%;font:600 18px/1 var(--pix);display:grid;place-items:center}
#zoom button:hover{background:rgba(0,0,0,.07)}
#zoom .lv{display:flex;gap:4px;padding:0 6px;align-items:center}
#zoom .lv i{width:6px;height:6px;border-radius:50%;background:rgba(42,38,34,.25);transition:background .3s,transform .3s}
#zoom .lv i.on{background:var(--spark);transform:scale(1.25)}
#zoom svg{width:16px;height:16px;margin:0 2px;opacity:.75}
#hint{left:50%;bottom:30px;transform:translateX(-50%);font:700 17px/1 var(--hand);text-shadow:0 1px 3px rgba(0,0,0,.5);white-space:nowrap;pointer-events:none;transition:opacity .8s}
html.turned #hint{opacity:0!important}

/* hover label that follows the cursor */
#tip{position:fixed;z-index:46;left:0;top:0;pointer-events:none;background:var(--cream);color:var(--ink);font:700 16px/1 var(--hand);padding:6px 10px 5px;border-radius:3px;box-shadow:0 3px 8px rgba(0,0,0,.25);opacity:0;transform:translate(-50%,-150%) scale(.85);transition:opacity .2s,transform .25s cubic-bezier(.3,1.6,.4,1);white-space:nowrap}
#tip.on{opacity:1;transform:translate(-50%,-160%) scale(1)}
#tip i{font-style:normal;color:var(--spark-d);font-family:var(--pix);font-size:12px;margin-left:6px}

/* ---------- cover (loader + title card) ---------- */
#cover{position:fixed;inset:0;z-index:60;perspective:1900px;perspective-origin:50% 50%}
.board{position:absolute;top:0;bottom:0;width:50.2%;background:var(--cloth) url(https://www.vividsites.app/media/flagship/foldworld/tex/cloth.jpg) 0 0/420px;overflow:hidden;transition:transform 1.5s cubic-bezier(.66,0,.22,1),filter 1.5s;backface-visibility:hidden;will-change:transform}
.board.l{left:0;transform-origin:0 50%;box-shadow:inset -10px 0 18px -10px rgba(0,0,0,.45)}
.board.r{right:0;transform-origin:100% 50%;box-shadow:inset 10px 0 18px -10px rgba(0,0,0,.45);background-position:-210px 0}
.board::before{content:"";position:absolute;inset:30px;border:2px solid rgba(0,0,0,.22);box-shadow:0 1px 0 rgba(255,255,255,.08),inset 0 1px 0 rgba(255,255,255,.08);pointer-events:none}
.board.l::before{right:-10px}.board.r::before{left:-10px}
.board::after{content:"";position:absolute;inset:0;background:radial-gradient(120% 90% at 50% 45%,rgba(255,240,220,.06),rgba(0,0,0,.28));pointer-events:none}
.corner{position:absolute;width:64px;height:64px;background:var(--paper) url(https://www.vividsites.app/media/flagship/foldworld/tex/rag.jpg) 0 0/300px;box-shadow:0 1px 3px rgba(0,0,0,.35)}
.board.l .corner.t{left:0;top:0;clip-path:polygon(0 0,100% 0,0 100%)}
.board.l .corner.b{left:0;bottom:0;clip-path:polygon(0 0,100% 100%,0 100%)}
.board.r .corner.t{right:0;top:0;clip-path:polygon(0 0,100% 0,100% 100%)}
.board.r .corner.b{right:0;bottom:0;clip-path:polygon(100% 0,100% 100%,0 100%)}
.shade{position:absolute;inset:0;background:#000;opacity:0;transition:opacity 1.5s cubic-bezier(.66,0,.22,1);pointer-events:none}
/* the label and the die-cut window are drawn twice, each half clipped by its board */
#cover{--wy:31%;--wr:118px}
.board.l{-webkit-mask:radial-gradient(circle var(--wr) at 50vw var(--wy),transparent calc(var(--wr) - .5px),#000 var(--wr));mask:radial-gradient(circle var(--wr) at 50vw var(--wy),transparent calc(var(--wr) - .5px),#000 var(--wr))}
.board.r{-webkit-mask:radial-gradient(circle var(--wr) at .2vw var(--wy),transparent calc(var(--wr) - .5px),#000 var(--wr));mask:radial-gradient(circle var(--wr) at .2vw var(--wy),transparent calc(var(--wr) - .5px),#000 var(--wr))}
.ring{position:absolute;top:calc(var(--wy) - var(--wr) - 14px);width:calc(2 * var(--wr) + 28px);height:calc(2 * var(--wr) + 28px);border-radius:50%;border:14px solid var(--paper);background:transparent;box-shadow:0 3px 10px rgba(0,0,0,.4);-webkit-mask:none}
.ring::after{content:"";position:absolute;inset:-14px;border-radius:50%;background:url(https://www.vividsites.app/media/flagship/foldworld/tex/rag.jpg) 0 0/300px;-webkit-mask:radial-gradient(circle,transparent calc(var(--wr) - .5px),#000 var(--wr));mask:radial-gradient(circle,transparent calc(var(--wr) - .5px),#000 var(--wr));opacity:.9}
.ring::before{content:"";position:absolute;inset:4px;border-radius:50%;border:1.5px dashed rgba(42,38,34,.35);z-index:1;margin:-12px}
.board.l .ring{right:calc(-1 * var(--wr) - 14px)}
.board.r .ring{left:calc(-1 * var(--wr) - 14px)}
.label{position:absolute;top:calc(var(--wy) + var(--wr) + 30px);width:min(640px,88vw);height:236px;background:var(--paper) url(https://www.vividsites.app/media/flagship/foldworld/tex/rag.jpg) 0 0/360px;color:var(--ink);box-shadow:0 1px 0 rgba(255,255,255,.4) inset,0 3px 10px rgba(0,0,0,.35);border-radius:2px;text-align:center}
.board.l .label{right:calc(.2vw - min(320px,44vw))}
.board.r .label{left:calc(.2vw - min(320px,44vw))}
.label::before{content:"";position:absolute;inset:12px;border:1.5px solid rgba(42,38,34,.35);border-radius:2px}
.label .k{position:absolute;left:0;right:0;top:30px;font:700 19px/1 var(--hand);color:#6f5a3c}
.label h1{position:absolute;left:0;right:0;top:56px;font:600 clamp(50px,7.6vw,92px)/1 var(--pix);letter-spacing:-.01em;color:var(--ink)}
.label h1 i{font-style:normal;color:var(--spark)}
.label .by{position:absolute;left:0;right:0;top:160px;font:700 21px/1.1 var(--hand)}
.pop{position:absolute;left:calc(50% + 0px);top:calc(var(--wy) - 13px);transform:translateX(-50%);display:flex;gap:10px;align-items:flex-end;perspective:300px;z-index:2}
.pop i{display:block;width:30px;height:24px;clip-path:polygon(50% 0,100% 100%,0 100%);transform-origin:50% 100%;transform:rotateX(84deg);transition:transform .7s cubic-bezier(.3,1.7,.4,1),opacity .6s;background:var(--c0);filter:drop-shadow(0 2px 2px rgba(0,0,0,.4))}
.pop i.up{transform:rotateX(0)}
.pct{position:absolute;left:0;right:0;top:196px;font:500 14px/1 var(--pix);color:#6f5a3c;letter-spacing:.06em}
.ribbon{position:absolute;top:calc(var(--wy) + var(--wr) + 300px);height:30px;left:0;right:0;background:var(--spark);box-shadow:0 2px 0 rgba(0,0,0,.18),inset 0 3px 0 rgba(255,255,255,.18),inset 0 -3px 0 rgba(0,0,0,.12);transition:transform .7s cubic-bezier(.6,0,.3,1)}
.ribbon::after{content:"";position:absolute;inset:0;background:repeating-linear-gradient(90deg,transparent 0 7px,rgba(255,255,255,.14) 7px 9px);mix-blend-mode:overlay}
#bow{position:absolute;left:50%;top:calc(31% + 118px + 315px);width:150px;height:110px;margin:-55px 0 0 -75px;z-index:3;transition:transform .55s cubic-bezier(.5,-0.4,.5,1),opacity .4s .15s;cursor:pointer;filter:drop-shadow(0 4px 5px rgba(0,0,0,.3))}
#bow:hover{animation:bowwig .7s cubic-bezier(.3,1.6,.4,1)}
@keyframes bowwig{30%{transform:rotate(-6deg) scale(1.04)}65%{transform:rotate(4deg)}}
#open{position:absolute;left:50%;top:calc(31% + 118px + 380px);transform:translateX(-50%);z-index:4;opacity:0;pointer-events:none;transition:opacity .6s}
#open .tag{font-size:19px;padding:12px 20px 12px 30px}
#open .tag::before{left:13px}
#open:hover .tagwrap{animation:swing .9s cubic-bezier(.3,1.6,.4,1)}
html.ready #open{opacity:1;pointer-events:auto}
#cover .foot{position:absolute;left:0;right:0;bottom:34px;text-align:center;font:700 18px/1.3 var(--hand);color:var(--cream);z-index:4;text-shadow:0 1px 2px rgba(0,0,0,.4)}
#cover .foot button{font:700 15px/1 var(--hand);text-decoration:underline;text-underline-offset:3px;margin-top:10px;opacity:.85}
html.opening #bow{transform:translateY(-30px) rotate(-30deg) scale(.6);opacity:0}
html.opening .board.l .ribbon{transform:translateX(-105%)}
html.opening .board.r .ribbon{transform:translateX(105%)}
html.opening #open,html.opening #cover .foot,html.opening #pop{opacity:0;transition:opacity .3s}
html.ready #pop i{opacity:0;transition-delay:.4s}
html.swing .board.l{transform:rotateY(100deg)}
html.swing .board.r{transform:rotateY(-100deg)}
html.swing .board .shade{opacity:.55}
html.open #cover{display:none}

/* ---------- prop card ---------- */
#card{position:fixed;inset:0;z-index:70;display:grid;place-items:center;pointer-events:none;perspective:1400px}
#card .scrim{position:absolute;inset:0;background:rgba(36,26,18,.42);opacity:0;transition:opacity .45s}
#card.on{pointer-events:auto}
#card.on .scrim{opacity:1}
.fold{position:relative;width:min(400px,86vw);transform-style:preserve-3d;transform:translateY(40px) rotateX(18deg) scale(.9);opacity:0;transition:transform .7s cubic-bezier(.2,1.25,.3,1),opacity .35s}
#card.on .fold{transform:none;opacity:1}
.half{position:relative;background:var(--paper) url(https://www.vividsites.app/media/flagship/foldworld/tex/rag.jpg) 0 0/360px;color:var(--ink);box-shadow:0 10px 30px rgba(0,0,0,.3)}
.half.top{height:250px;border-radius:4px 4px 0 0;transform-origin:50% 100%;transform:rotateX(-178deg);transition:transform .9s .12s cubic-bezier(.25,1.3,.35,1);display:grid;place-items:center;background-color:var(--cc,#c9973f);background-blend-mode:multiply;z-index:2}
#card.on .half.top{transform:rotateX(0)}
.half.top .art{width:78%;height:82%;background-repeat:no-repeat;filter:drop-shadow(0 6px 4px rgba(0,0,0,.28))}
.half.top::after{content:"";position:absolute;left:0;right:0;bottom:0;height:16px;background:linear-gradient(rgba(0,0,0,0),rgba(0,0,0,.12))}
.half.bot{border-radius:0 0 4px 4px;padding:22px 26px 24px}
.half.bot::before{content:"";position:absolute;left:0;right:0;top:0;height:14px;background:linear-gradient(rgba(0,0,0,.1),rgba(0,0,0,0))}
.half.bot small{font:500 12px/1 var(--pix);letter-spacing:.08em;text-transform:uppercase;color:#7b6545}
.half.bot h3{font:600 27px/1.05 var(--pix);margin:8px 0 10px}
.half.bot p{font:700 19px/1.22 var(--hand)}
.half.bot p em{font-style:normal;color:var(--spark-d)}
.x{position:absolute;right:10px;top:10px;width:34px;height:34px;border-radius:50%;background:var(--cream);color:var(--ink);font:600 16px/1 var(--pix);z-index:3;box-shadow:0 2px 5px rgba(0,0,0,.25)}

/* ---------- colophon ---------- */
#colophon{position:fixed;inset:0;z-index:30;background:#d9cdb5 url(https://www.vividsites.app/media/flagship/foldworld/tex/rag.jpg) 0 0/420px;pointer-events:none;opacity:0;transition:opacity .5s}
#colophon .txt{position:absolute;left:60%;top:50%;transform:translateY(-50%);width:min(500px,35vw);color:var(--ink);opacity:0;transition:opacity .5s .35s}
#colophon h2{font:600 58px/1 var(--pix);margin-bottom:20px}
#colophon h2 i{font-style:normal;color:var(--spark)}
#colophon p{font:700 22px/1.3 var(--hand);margin-bottom:14px}
#colophon p em{font-style:normal;color:var(--spark-d)}
#colophon .x2{position:absolute;right:28px;top:20px;z-index:2}
html.colo #colophon{opacity:1;pointer-events:auto}
html.colo #colophon .txt{opacity:1}
html.colo #stage{transform:translate(-21vw,0) scale(.5) rotate(-2.2deg);border-radius:4px;box-shadow:0 0 0 14px #f6efe1,0 24px 50px rgba(40,25,10,.35);z-index:31}
html.colo .chrome,html.colo #frame{opacity:0!important;pointer-events:none}
.pc{position:fixed;z-index:32;width:60px;height:60px;background:#2a2622;opacity:0;transition:opacity .4s .5s;pointer-events:none}
html.colo .pc{opacity:.88}
html.nogl .pc{display:none}

@media (min-width:761px) and (max-width:1199px){#hint{bottom:88px}}
@media (max-width:760px){
  #mark{left:20px;top:18px}
  #mark b{font-size:19px}
  #mark span{font-size:14px}
  #colo{right:16px;top:16px}
  #colo .string{width:12px}
  #chap{left:18px;bottom:20px;flex-direction:column;align-items:flex-start;gap:8px}
  #chapname{font-size:15px}
  #tabs button{width:26px}
  #zoom{right:16px;bottom:20px}
  #zoom .lv{display:none}
  #hint{bottom:auto;top:76px;font-size:15px}
  #cover{--wy:27%;--wr:92px}
  .label{height:204px}
  .label .k{top:26px;font-size:16px}
  .label h1{top:50px}
  .label .by{top:126px;font-size:17px}
  .pop{gap:7px}.pop i{width:22px;height:18px}
  .pct{top:162px}
  .ribbon{top:calc(var(--wy) + var(--wr) + 252px)}
  #bow{top:calc(27% + 92px + 267px);transform:scale(.85)}
  #open{top:calc(27% + 92px + 322px)}
  .corner{width:44px;height:44px}
  .board::before{inset:18px}
  html.colo #stage{transform:translate(0,calc(60px - 27vh)) scale(.46) rotate(-2deg)}
  #colophon .txt{left:24px;right:24px;width:auto;top:auto;bottom:28px;transform:none}
  #colophon h2{font-size:30px;margin-bottom:8px}
  #colophon p{font-size:15.5px;line-height:1.25;margin-bottom:7px}
  #colophon .txt{bottom:22px}
}
/* short viewports: the cover's window rides up so the ribbon, bow and "Untie & open" stay clear of the footer */
@media (min-width:761px) and (max-height:899px){
  #cover{--wy:min(31%, calc(100% - 469px - var(--wr)))}
  #bow{top:calc(var(--wy) + var(--wr) + 315px)}
  #open{top:calc(var(--wy) + var(--wr) + 380px)}
}
@media (min-width:761px) and (max-height:760px){#cover{--wr:92px}}
@media (max-width:760px) and (max-height:760px){
  #cover{--wy:min(27%, calc(100% - 411px - var(--wr)))}
  #bow{top:calc(var(--wy) + var(--wr) + 267px)}
  #open{top:calc(var(--wy) + var(--wr) + 322px)}
}
@media (max-width:760px) and (max-height:760px){html.colo #stage{transform:translate(0,calc(60px - 30vh)) scale(.4) rotate(-2deg)}}
@media (min-width:761px) and (max-height:899px),(max-width:760px) and (max-height:760px){
  #cover .foot{bottom:14px;font-size:0}
  #cover .foot br{display:none}
  #cover .foot button{font-size:15px;margin-top:0}
}
@media (prefers-reduced-motion:reduce){*{transition-duration:.01s!important;animation:none!important}}
```

## Markup
`#tabs` is filled by the script; the card's title, kicker, copy and art are written when a card opens; the four `.pc` elements are
the colophon's photo corners. Copy every string exactly.
```html
<body>
<div id="stage">
  <canvas id="gl" tabindex="0" aria-label="A paper carousel book in six chapters. Scroll, drag or use the arrow keys to turn it."></canvas>
  <div id="still"><p>This book turns with WebGL. Here's a photo of the first chapter.</p></div>
</div>
<canvas id="frame" aria-hidden="true"></canvas>

<header class="chrome" id="mark"><b>Fold<i>·</i>world</b><span>Odile Penhallow, paper engineer</span></header>
<button class="chrome" id="colo" aria-label="Open the colophon"><span class="string"></span><span class="tagwrap"><span class="tag">Colophon</span></span></button>
<nav class="chrome" id="chap" aria-label="Chapters"><div id="tabs"></div><div id="chapname"><small>chapter one</small>The Workbench</div></nav>
<div class="chrome" id="zoom" role="group" aria-label="Zoom">
  <button id="zout" aria-label="Zoom out">−</button>
  <svg viewBox="0 0 16 16" aria-hidden="true"><circle cx="6.5" cy="6.5" r="4.6" fill="none" stroke="currentColor" stroke-width="1.8"/><path d="M10 10l4.2 4.2" stroke="currentColor" stroke-width="2" stroke-linecap="round"/></svg>
  <span class="lv"><i class="on"></i><i></i><i></i></span>
  <button id="zin" aria-label="Zoom in">+</button>
</div>
<div class="chrome" id="hint">~ scroll, drag or swipe to turn the book ~</div>
<div id="tip"></div>

<div id="card" aria-hidden="true">
  <div class="scrim"></div>
  <div class="fold" role="dialog" aria-modal="true" aria-labelledby="cardh">
    <div class="half top"><div class="art"></div></div>
    <div class="half bot"><small id="cards">chapter</small><h3 id="cardh">Title</h3><p id="cardp"></p></div>
    <button class="x" aria-label="Close">✕</button>
  </div>
</div>

<div id="colophon" aria-hidden="true">
  <button class="x2" id="colox"><span class="tagwrap"><span class="tag">Close the colophon</span></span></button>
  <div class="txt">
    <h2>Colophon<i>.</i></h2>
    <p>Foldworld is a carousel book: six pages tied back to back so they open into a star of little rooms. Each room is a chapter of <em>Odile Penhallow</em>'s work as a paper engineer.</p>
    <p>Everything you see is paper: folded, scored and stood up in three.js. The paper, the props and Odile herself were drawn for this book, then cut out and given thickness in code.</p>
    <p>Set in Pixelify Sans and Gaegu. Odile, her studio and Foldworld are fictional, made up for this book.</p>
    <p>Write to <em>hello@foldworld.studio</em>. She replies on paper.</p>
  </div>
</div>
<i class="pc" id="pc1"></i><i class="pc" id="pc2"></i><i class="pc" id="pc3"></i><i class="pc" id="pc4"></i>

<div id="cover">
  <div class="board l"><div class="corner t"></div><div class="corner b"></div>
    <div class="label"><div class="k">a carousel book in six chapters</div><h1>Fold<i>·</i>world</h1><div class="by">by Odile Penhallow, paper engineer</div><div class="pct">FOLDING 000</div></div>
    <div class="ring"></div><div class="ribbon"></div><div class="shade"></div></div>
  <div class="board r"><div class="corner t"></div><div class="corner b"></div>
    <div class="label"><div class="k">a carousel book in six chapters</div><h1>Fold<i>·</i>world</h1><div class="by">by Odile Penhallow, paper engineer</div><div class="pct">FOLDING 000</div></div>
    <div class="ring"></div><div class="ribbon"></div><div class="shade"></div></div>
  <div class="pop" id="pop"><i></i><i></i><i></i><i></i><i></i><i></i></div>
  <svg id="bow" viewBox="0 0 150 110" aria-hidden="true">
    <path d="M75 52 C52 20 18 8 10 30 C4 48 30 62 75 56Z" fill="#ff4f8b"/><path d="M75 52 C98 20 132 8 140 30 C146 48 120 62 75 56Z" fill="#ff4f8b"/>
    <path d="M75 52 C55 30 30 22 22 34 C30 30 52 38 75 55Z" fill="#d8336f" opacity=".6"/><path d="M75 52 C95 30 120 22 128 34 C120 30 98 38 75 55Z" fill="#d8336f" opacity=".6"/>
    <path d="M70 56 L52 104 L62 98 L68 106 L76 58Z" fill="#e8407c"/><path d="M80 56 L98 102 L88 97 L83 106 L74 58Z" fill="#ff5f95"/>
    <rect x="64" y="45" width="22" height="18" rx="6" fill="#e8407c"/><rect x="66" y="47" width="18" height="5" rx="2.5" fill="#fff" opacity=".2"/>
  </svg>
  <button id="open" aria-label="Untie the ribbon and open the book"><span class="tagwrap"><span class="tag">Untie &amp; open</span></span></button>
  <div class="foot">~ scroll, drag or swipe to turn the pages ~<br><button id="cocred">colophon &amp; credits</button></div>
</div>
```

## The watchdog (classic script, before the module)
This runs before anything else and needs neither WebGL nor three.js. `__fwFail(why)` puts `nogl` and `ready` on `<html>`, writes
`READY` into both counts and stands all six triangles up (the `ready` rule then fades them): the still shows with its caption, the
tabs, zoom and hint hide, and "Untie & open" becomes clickable. With no WebGL context at all it fires at once; otherwise a 10 s
timer fires it unless the module has set `__ready` (`assets slow` if the module started, `module did not boot` if it never did).
Its opener plays the same CSS sequence as the module's (opening, then swing at 420 ms, then open at 1900 ms) and hands over to
`__fwOpen` when the module defined one; its colophon handlers act only under `nogl`.
```html
<script>
// classic-script watchdog: the cover must always be able to lift, even with no WebGL or no three.js
(function(){
  var d=document.documentElement;
  function gl(){try{var c=document.createElement('canvas');return !!(c.getContext('webgl2')||c.getContext('webgl'))}catch(e){return false}}
  window.__fwFail=function(why){ if(d.classList.contains('nogl'))return; d.classList.add('nogl','ready'); console.warn('foldworld fallback:',why);
    var p=document.querySelectorAll('.pct'); for(var i=0;i<p.length;i++)p[i].textContent='READY';
    var t=document.querySelectorAll('.pop i'); for(i=0;i<t.length;i++)t[i].classList.add('up'); };
  if(!gl()) window.__fwFail('no webgl');
  setTimeout(function(){ if(!window.__ready) window.__fwFail(window.__booted?'assets slow':'module did not boot'); }, 10000);
  function open(){ if(d.classList.contains('opening'))return; if(window.__fwOpen){window.__fwOpen();return;}
    d.classList.add('opening'); setTimeout(function(){d.classList.add('swing')},420); setTimeout(function(){d.classList.add('open')},1900); }
  window.__fwOpenFallback=open;
  function ng(){return d.classList.contains('nogl')}
  var co=document.getElementById('colophon');
  function coOpen(){ d.classList.add('colo'); co.setAttribute('aria-hidden','false'); document.getElementById('colox').focus({preventScroll:true}); }
  function coClose(){ if(!d.classList.contains('colo'))return; d.classList.remove('colo'); co.setAttribute('aria-hidden','true'); document.getElementById('colo').focus({preventScroll:true}); }
  document.getElementById('colo').addEventListener('click',function(){ if(ng()) coOpen(); });
  document.getElementById('colox').addEventListener('click',function(){ if(ng()) coClose(); });
  document.addEventListener('keydown',function(e){ if(e.key==='Escape'&&ng()) coClose(); });
  document.getElementById('cocred').addEventListener('click',function(){ if(ng()){ open(); setTimeout(coOpen,1950); } });
  document.getElementById('open').addEventListener('click',open);
  document.getElementById('bow').addEventListener('click',function(){ if(d.classList.contains('ready')) open(); });
})();
</script>
```

## Module prelude — imports, constants and the chapter data
`window.__booted` is set the moment the imports resolve; if the watchdog has already shown the still, the module stops there. The
book: 6 bays, radius `R` 3, spine height `H` 3.3, wall rim height `HOUT` 2.75, wall thickness `T` .036, floor thickness .05, and
`TAN` = tan 30° for the half-width of a bay at depth z. `PHONE` is a coarse pointer or a short side under 560 px; `PORTRAIT` is a
width-to-height ratio under .9. `CH` holds each chapter's name, wall, floor and ink colours, its sign's side offset `sx` on the
thread (centred in portrait) and its sign copy (`*…*` marks a pink word); `CARDS` the 19 card stories (a prop
named with a trailing digit, e.g. `lighthouse2`, falls back to its base story, so all 19 open); `LABELS` the hover names.
```js
import * as THREE from 'three';
import { EffectComposer } from 'three/addons/postprocessing/EffectComposer.js';
import { RenderPass } from 'three/addons/postprocessing/RenderPass.js';
import { GTAOPass } from 'three/addons/postprocessing/GTAOPass.js';
import { ShaderPass } from 'three/addons/postprocessing/ShaderPass.js';
import { OutputPass } from 'three/addons/postprocessing/OutputPass.js';
window.__booted = true;
if (document.documentElement.classList.contains('nogl')) throw new Error('fallback already shown');

/* ================================================================ constants */
const D2R = Math.PI / 180, TAU = Math.PI * 2;
const NB = 6, R = 3.0, H = 3.3, HOUT = 2.75, T = 0.036, TAN = Math.tan(30 * D2R), FLOOR = 0.05;
const html = document.documentElement;
const PHONE = matchMedia('(pointer:coarse)').matches || Math.min(innerWidth, innerHeight) < 560;
const PORTRAIT = innerWidth / innerHeight < 0.9;
const Q = new URLSearchParams(location.search);
const CH = [
  { id: 'work', n: 'The Workbench', num: 'one', wall: '#c9973f', floor: '#4a7862', ink: '#7a4d14', sx: -0.6,
    sign: { t: "Hello, I'm Odile!", b: ["I'm a *paper engineer*. I fold, score", 'and glue little worlds that stand', 'up when you open a book.', '', 'Every one of them started flat, on', 'this table: *4,000 sheets* so far.'] } },
  { id: 'tide', n: 'The Tide Book', num: 'two', wall: '#3f7f7b', floor: '#d6c29a', ink: '#24585a', sx: -0.62,
    sign: { t: 'My first book', b: ["A lighthouse keeper's daughter, a", 'boat with a paper sail and *forty-*', '*one waves* that all had to fold flat.', '', 'It took me a year to make the sea', 'lie down. Published *2014*.'] } },
  { id: 'night', n: 'The Night Orchard', num: 'three', wall: '#3d4672', floor: '#3f553b', ink: '#2e3766', sx: -0.62,
    sign: { t: 'Bedtime books', b: ['Lanterns that open when the page', 'does. An owl who turns his head', 'when you pull the tab.', '', 'Small hands are rough, so every', 'hinge is tested *500 times*.'] } },
  { id: 'market', n: 'Market Street', num: 'four', wall: '#c4583f', floor: '#a59b90', ink: '#8c3523', sx: 0.62,
    sign: { t: 'Commissions', b: ["A street of shops for a bakery's", '*hundredth birthday*. A tram for a', 'museum. A whole town for a wedding.', '', 'If it can be drawn, it can', 'usually be *folded*.'] } },
  { id: 'glass', n: 'The Glasshouse', num: 'five', wall: '#8aa27a', floor: '#b8744e', ink: '#45603c', sx: 0.62,
    sign: { t: 'Workshops', b: ['Every spring I teach folding in an', 'old glasshouse. Bring scissors,', 'leave with a *fern that stands up*.', '', 'Saturdays, March to May.', 'Ages *6 to 96*.'] } },
  { id: 'post', n: 'The Post Room', num: 'six', wall: '#c27a86', floor: '#3e6a68', ink: '#8a3a4c', sx: -0.62,
    sign: { t: 'Write to me', b: ['Commissions, workshops, or just', 'a letter. I read every one and I', 'always *reply on paper*.', '', '*hello@foldworld.studio*', 'Studio 3, Rope Walk Yard'] } },
];
const CARDS = {
  odile_cut: ['Odile Penhallow', 'Paper engineer, ex-architect, keeper of one very good pair of scissors. She has made *nineteen* pop-up books since 2014.'],
  lamp: ['The arm lamp', 'Rescued from a skip in 2012. Every book in this room was cut under it, mostly after dark.'],
  cat: ['Mouse, studio cat', 'Head of quality control. Has sat on every prototype. Approves of *none* of them.'],
  books2: ['The take-apart shelf', 'Old pop-up books bought at fairs, taken apart very gently, and put back together. That is how you learn.'],
  lighthouse: ['The lighthouse fold', 'The first pop-up I ever got right: four layers and one V-fold, and the light *swings out* as the page opens.'],
  odile_row: ['Row, row', 'The girl in The Tide Book rows out to her father every night with a paper lamp. Children still write to ask if she got there.'],
  whale: ['Forty-one waves', 'Every wave is its own strip on a hidden slide. Pull the tab and the whole sea *rolls*.'],
  owl2: ['The pull-tab owl', 'A paper wheel behind the page turns his head *a quarter turn* when you pull. His name is Professor.'],
  odile_lantern2: ['Lantern pages', 'The lantern opens into a six-sided paper globe as the page turns. The hardest fold in the whole book.'],
  fox: ['Sleeping fox', 'The fox has never once woken up, in any printing. That was on purpose.'],
  tram: ['The museum tram', 'For a city transport museum: a tram that *rolls along a paper track* as you turn the page.'],
  bakery: ['A hundred years of bread', 'A bakery asked for its street as it looked in 1925. Every window opens, with a loaf behind each one.'],
  odile_wave2: ['Commissions are open', 'Books, invitations, shop windows: anything that ought to *stand up*. Spring dates are filling.'],
  wateringcan: ['Saturday workshops', 'Two hours, one fern, all ages. Scissors, paper and tea provided. Bring nothing but *patience*.'],
  sunflower: ['The tallest fold', 'This sunflower stands *30 cm* tall from a flat page. It took eleven tries and a lot of tape.'],
  odile_water: ['Growing paper', 'Each workshop ends with a little paper garden that folds flat into an envelope to take home.'],
  odile_post: ['Write to me', '*hello@foldworld.studio*, or post it to Studio 3, Rope Walk Yard. Every letter gets read.'],
  dove: ['Replies by paper', 'Every letter gets a folded reply. Some of them *stand up* when you open them.'],
  desk2: ['The letter desk', 'An old typewriter for addresses, because handwriting on a thousand envelopes is a lot.'],
};
const LABELS = { lamp: 'the arm lamp', lamp2: 'a lamp', cat: 'Mouse the cat', cat2: 'Mouse again', books: 'books', books2: 'old pop-up books', scissors: 'scissors', scissors2: 'scissors',
  spool: 'pink thread', spool2: 'thread', pencils: 'pencils', pencils2: 'pencils', teacup: 'tea, cold', teacup2: 'tea', cactus: 'a cactus', cactus2: 'a cactus', crane: 'a paper crane', crane2: 'a crane',
  lighthouse: 'the lighthouse', lighthouse2: 'a lighthouse', sailboat: 'a sailboat', sailboat2: 'a sailboat', gull: 'a gull', gull2: 'a gull', crab: 'a crab', crab2: 'a crab', buoy: 'a buoy', buoy2: 'a buoy',
  rowboat: 'a rowing boat', rowboat2: 'a boat', whale: 'the whale', whale2: 'a whale', starfish: 'a starfish', starfish2: 'a starfish', hut: 'a beach hut', hut2: 'a beach hut',
  appletree: 'an apple tree', appletree2: 'an apple tree', owl: 'an owl', owl2: 'Professor the owl', lantern: 'a lantern', lantern2: 'a lantern', fox: 'a sleeping fox', fox2: 'a fox', moon: 'the moon', moon2: 'the moon',
  hedgehog: 'a hedgehog', hedgehog2: 'a hedgehog', poplar: 'a poplar', poplar2: 'a poplar', toadstools: 'toadstools', toadstools2: 'toadstools', rabbit: 'a rabbit', rabbit2: 'a rabbit',
  bakery: 'the bakery', bakery2: 'a bakery', townhouse: 'a townhouse', townhouse2: 'a townhouse', tram: 'the tram', tram2: 'a tram', bicycle: 'a bicycle', bicycle2: 'a bicycle', flowercart: 'a flower cart', flowercart2: 'flowers',
  streetlamp: 'a street lamp', streetlamp2: 'a street lamp', dog: 'a scruffy dog', dog2: 'a dog', pigeon: 'a pigeon', pigeon2: 'a pigeon', fruitstall: 'oranges', fruitstall2: 'oranges',
  fern: 'a fern', fern2: 'a fern', monstera: 'a monstera', monstera2: 'a monstera', snail: 'a snail', snail2: 'a snail', wateringcan: 'the watering can', wateringcan2: 'a watering can', cactustall: 'a tall cactus', cactustall2: 'a cactus',
  mushroom: 'a toadstool', mushroom2: 'a toadstool', wheelbarrow: 'a wheelbarrow', wheelbarrow2: 'a wheelbarrow', butterfly: 'a butterfly', butterfly2: 'a butterfly', sunflower: 'the sunflower', sunflower2: 'a sunflower',
  postbox: 'the letter box', postbox2: 'a letter box', envelope: 'a letter', envelope2: 'a letter', plane: 'a paper plane', plane2: 'a paper plane', parcel: 'a parcel', parcel2: 'a parcel', satchel: 'the post bag', satchel2: 'a satchel',
  dove: 'the post dove', dove2: 'a dove', letters: 'letters', letters2: 'letters', desk: 'a desk', desk2: 'the letter desk', stoolplant: 'a plant', stoolplant2: 'a plant',
  odile_cut: 'Odile', odile_row: 'Odile', odile_lantern2: 'Odile', odile_wave2: 'Odile', odile_water: 'Odile', odile_post: 'Odile' };
```

## Renderer, camera and lights
No canvas antialiasing (the composer's render target carries 4× MSAA), Neutral tone mapping at exposure 1.1, PCF soft shadows. DPR
is capped at 1.5 on desktop and 1.6 on phones. A warm `#77624f` background and fog from 13 to 30; the 34° desktop camera stands at
(0, 2.95, 7.3) looking at (0, 1.3, 1.25), the phone-portrait one at (0, 2.45, 6.5) with a 47° lens looking at (0, 1.5, 1.7); three
zoom steps scale the lens. The lights are fixed to the room and the book turns beneath them: a hemisphere fill, a warm key from
the upper left with a 2048 shadow map (1024 on phones) at intensity .72 and radius 3, a cool fill and a warm rim.
```js
/* ================================================================ renderer */
const canvas = document.getElementById('gl');
let renderer;
try {
  renderer = new THREE.WebGLRenderer({ canvas, antialias: false, powerPreference: 'high-performance', stencil: false });
} catch (e) { window.__fwFail && window.__fwFail('renderer'); throw e; }
const DPR = Math.min(devicePixelRatio || 1, PHONE ? 1.6 : 1.5);
renderer.setPixelRatio(DPR);
renderer.setSize(innerWidth, innerHeight, false);
renderer.toneMapping = THREE.NeutralToneMapping;
renderer.toneMappingExposure = 1.1;
renderer.shadowMap.enabled = true;
renderer.shadowMap.type = THREE.PCFSoftShadowMap;
const MAXANI = renderer.capabilities.getMaxAnisotropy();

const scene = new THREE.Scene();
const BG = new THREE.Color('#77624f');
scene.background = BG;
scene.fog = new THREE.Fog(BG, 13, 30);
const camera = new THREE.PerspectiveCamera(34, innerWidth / innerHeight, 0.1, 80);
const CAM = PHONE && PORTRAIT
  ? { pos: new THREE.Vector3(0, 2.45, 6.5), look: new THREE.Vector3(0, 1.5, 1.7), fov: 47 }
  : { pos: new THREE.Vector3(0, 2.95, 7.3), look: new THREE.Vector3(0, 1.3, 1.25), fov: 34 };
const ZOOMS = PHONE && PORTRAIT ? [1, 0.86, 0.74] : [1, 0.8, 0.64];
let zoomI = 0, zoomF = 1;

/* lights: fixed to the room; the book turns on a lazy susan beneath them */
scene.add(new THREE.HemisphereLight('#fff5e6', '#7a6552', 1.45));
const key = new THREE.DirectionalLight('#fff0db', 2.35);
key.position.set(-4.2, 8.5, 6.5); key.target.position.set(0, 0.9, 0.4);
key.castShadow = true;
key.shadow.mapSize.set(PHONE ? 1024 : 2048, PHONE ? 1024 : 2048);
Object.assign(key.shadow.camera, { left: -4.4, right: 4.4, top: 4.4, bottom: -4.4, near: 2, far: 22 });
key.shadow.intensity = 0.72; key.shadow.bias = -0.0005; key.shadow.normalBias = 0.025; key.shadow.radius = 3;
scene.add(key, key.target);
const fill = new THREE.DirectionalLight('#dfe7ff', 0.45); fill.position.set(6, 3, 4); scene.add(fill);
const rim = new THREE.DirectionalLight('#ffd9b0', 0.5); rim.position.set(2, 6, -7); scene.add(rim);
```

## Loading — the pop-up count and the hosted files
Every texture and atlas loads through one `LoadingManager`, whose progress fills 82% of the count; the build steps add 88, 94 and
100. The shown number chases the real one (12% of the gap plus .25 a frame, never past it) as `FOLDING 000` and stands up one
triangle per sixth, each painted its chapter's wall colour. The textures are WebGL samples from another origin, so the loader sets
`crossOrigin = 'anonymous'` (three's default, made explicit here: added), and the rag paper `Image`, which is drawn into the sign
canvases that become textures, needs `crossOrigin = 'anonymous'` before its `src` (added), or the canvases would be tainted and
refuse to upload. The six atlases are named by chapter id from one base: `PROPS + c.id + '.webp'` with `PROPS =
'https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/flagship/foldworld/props/'` (added as a constant; the
build used a relative folder), which resolves to `work`, `tide`, `night`, `market`, `glass` and `post`. `PATIENCE` (5 s) caps the
wait on the fonts and on the textures: the book builds with what has arrived and late textures fill in.
```js
/* ================================================================ loading */
const pops = [...document.querySelectorAll('.pop i')].filter((_, i) => i < 6);
const pops2 = [...document.querySelectorAll('.pop i')].filter((_, i) => i >= 6);
const pcts = document.querySelectorAll('.pct');
let shownPct = 0, realPct = 0;
function setPct(p) { realPct = Math.max(realPct, p); }
function tickPct() {
  shownPct += (realPct - shownPct) * 0.12 + (realPct > shownPct ? 0.25 : 0);
  shownPct = Math.min(shownPct, realPct);
  const v = Math.round(shownPct);
  pcts.forEach(e => e.textContent = 'FOLDING ' + String(v).padStart(3, '0'));
  const n = Math.floor(v / 100 * 6 + 0.001);
  [pops, pops2].forEach(set => set.forEach((e, i) => { e.classList.toggle('up', i < n); e.style.background = CH[i].wall; }));
}
const manager = new THREE.LoadingManager();
manager.onProgress = (u, a, b) => setPct(a / b * 82);
const tl = new THREE.TextureLoader(manager);
tl.setCrossOrigin('anonymous');   // added: the textures come from another origin
const PROPS = 'https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/flagship/foldworld/props/';   // added: the atlas base
function tex(url, { srgb = true, rep = 1 } = {}) {
  const t = tl.load(url);
  t.colorSpace = srgb ? THREE.SRGBColorSpace : THREE.NoColorSpace;
  t.wrapS = t.wrapT = THREE.RepeatWrapping; t.repeat.set(rep, rep); t.anisotropy = Math.min(8, MAXANI);
  return t;
}
const detailTex = tex('https://www.vividsites.app/media/flagship/foldworld/tex/paper_detail.jpg', { srgb: false });
const normalTex = tex('https://www.vividsites.app/media/flagship/foldworld/tex/paper_normal.jpg', { srgb: false });
const ragNormal = tex('https://www.vividsites.app/media/flagship/foldworld/tex/rag_normal.jpg', { srgb: false });
const woodTex = tex('https://www.vividsites.app/media/flagship/foldworld/tex/wood.jpg', { rep: 1 });
const ATLAS = {};
for (const c of CH) ATLAS[c.id] = tl.load(PROPS + c.id + '.webp', t => { t.colorSpace = THREE.SRGBColorSpace; t.anisotropy = Math.min(8, MAXANI); });
const ragImg = new Image(); ragImg.crossOrigin = 'anonymous'; ragImg.src = 'https://www.vividsites.app/media/flagship/foldworld/tex/rag.jpg';   // crossOrigin added: it is drawn into canvases that become textures
const metaP = fetch('https://www.vividsites.app/media/flagship/foldworld/props/props.json').then(r => r.json());
const fontsP = Promise.all([document.fonts.load('600 60px "Pixelify Sans"'), document.fonts.load('700 40px "Gaegu"'), document.fonts.load('400 40px "Gaegu"')]).catch(() => {});
const loadedP = new Promise(res => { manager.onLoad = res; });
/* loader patience: if a texture or a font stalls, build with what has arrived (late textures still fill in) */
const PATIENCE = 5000;
const patient = p => Promise.race([p, new Promise(r => setTimeout(r, PATIENCE))]);
```

## Paper materials and geometry helpers
Every built surface is `MeshStandardMaterial` paper: the colour lifted ×1.14, the cardstock detail map as `map` (loaded without a
colour space, so it reads bright and only adds fibre), a paper normal map at .5, roughness .94, metalness 0, cached by its
parameters. `worldUV` projects UVs from the dominant normal axis so the fibre runs continuously across faces. A cut edge is the
face colour lerped 38% toward cream. `ext` extrudes a shape to card thickness (face and edge materials), `box` makes a card slab,
`profileShape` turns a height function into a die-cut strip, `cloudShape` and `starShape` make the wall cut-outs, and `rnd` is a
seeded LCG so every layout is the same on every load.
```js
/* ================================================================ materials */
function worldUV(g, s = 0.62) {
  const p = g.attributes.position, n = g.attributes.normal, uv = new Float32Array(p.count * 2);
  for (let i = 0; i < p.count; i++) {
    const ax = Math.abs(n.getX(i)), ay = Math.abs(n.getY(i)), az = Math.abs(n.getZ(i));
    let u, v;
    if (ay >= ax && ay >= az) { u = p.getX(i); v = p.getZ(i); } else if (ax >= az) { u = p.getZ(i); v = p.getY(i); } else { u = p.getX(i); v = p.getY(i); }
    uv[2 * i] = u * s; uv[2 * i + 1] = v * s;
  }
  g.setAttribute('uv', new THREE.BufferAttribute(uv, 2));
  return g;
}
const mats = new Map();
function paper(hex, { ns = 0.5, rough = 0.94, lift = 1.14, nmap = normalTex, side = THREE.FrontSide } = {}) {
  const k = hex + ns + rough + lift + side + (nmap === ragNormal ? 'r' : 'n');
  if (mats.has(k)) return mats.get(k);
  const m = new THREE.MeshStandardMaterial({ color: new THREE.Color(hex).multiplyScalar(lift), map: detailTex, normalMap: nmap,
    normalScale: new THREE.Vector2(ns, ns), roughness: rough, metalness: 0, side });
  mats.set(k, m); return m;
}
function edgeOf(hex, amt = 0.38) { return paper('#' + new THREE.Color(hex).lerp(new THREE.Color('#f1e7d3'), amt).getHexString(), { ns: 0.2 }); }
const PINK = '#ff4f8b';
const pinkMat = new THREE.MeshStandardMaterial({ color: new THREE.Color(PINK), roughness: 0.7, emissive: new THREE.Color('#ff2f78'), emissiveIntensity: 0.12 });

/* ================================================================ geometry helpers */
function ext(shape, depth, hex, { edge, center = true, ns } = {}) {
  const g = new THREE.ExtrudeGeometry(shape, { depth, bevelEnabled: false, curveSegments: 20 });
  if (center) g.translate(0, 0, -depth / 2);
  worldUV(g);
  const m = new THREE.Mesh(g, [paper(hex, ns != null ? { ns } : {}), edge ? paper(edge, { ns: 0.2 }) : edgeOf(hex)]);
  m.castShadow = m.receiveShadow = true;
  return m;
}
function box(w, h, d, hex, edge) {
  const g = worldUV(new THREE.BoxGeometry(w, h, d));
  const f = paper(hex), e = edge ? paper(edge, { ns: 0.2 }) : edgeOf(hex);
  const m = new THREE.Mesh(g, [e, e, f, f, f, f]);
  m.castShadow = m.receiveShadow = true; return m;
}
function profileShape(hw, fn, n = 64, y0 = 0) {
  const s = new THREE.Shape(); s.moveTo(-hw, y0);
  for (let i = 0; i <= n; i++) { const x = -hw + 2 * hw * i / n; s.lineTo(x, fn(x, i / n)); }
  s.lineTo(hw, y0); s.closePath(); return s;
}
function cloudShape(w, h, seed = 1) {
  const r = rnd(seed); const cs = [];
  const k = 4 + Math.floor(r() * 2);
  for (let i = 0; i < k; i++) { const t = (i + 0.5) / k; cs.push([(t - 0.5) * w * 0.8, h * (0.25 + 0.5 * Math.sin(t * Math.PI) * (0.7 + r() * 0.5)), h * (0.35 + r() * 0.25)]); }
  return profileShape(w / 2, x => { let m = 0; for (const [cx, cy, cr] of cs) { const d = cr * cr - (x - cx) ** 2; if (d > 0) m = Math.max(m, cy + Math.sqrt(d) * 0.75); } return Math.max(0.02, m); }, 56);
}
function starShape(ro, ri = ro * 0.45) {
  const s = new THREE.Shape();
  for (let i = 0; i < 10; i++) { const a = Math.PI / 2 + i * Math.PI / 5, r = i % 2 ? ri : ro; const x = Math.cos(a) * r, y = Math.sin(a) * r; i ? s.lineTo(x, y) : s.moveTo(x, y); }
  s.closePath(); return s;
}
function rnd(seed) { let s = seed * 9301 + 49297; return () => ((s = (s * 9301 + 49297) % 233280) / 233280); }
```

## Props from the atlases
`props.json` holds, per chapter, each cut-out's atlas rectangle `uv [u0, v0, u1, v1]`, its `aspect` and its traced outlines
(`shapes`: an outer ring `o` and holes `h`, in 0–1 across and 0–1 up). Each becomes an `ExtrudeGeometry` .03 deep, one unit tall,
centred on x, with its front and back UVs remapped into the atlas rectangle; the side walls take the same mapping, which smears
the art's edge colour round the cut like real printed card. The face material uses the atlas with `alphaTest` .5 and
alpha-to-coverage, roughness .9 and the paper normal map tiled 9× at .35; the edge material is the atlas tinted (.86, .84, .8).
`prop()` wraps each in a pivot group carrying its spring state, its card and its label; names matching `SWAY` sway gently (Odile
.018 rad, the lighthouse and street lamp .004, plants .012). The work atlas holds Odile's twelve poses, so other chapters borrow
her with `atlas: 'work'`.
```js
/* ================================================================ props from the atlases */
let META;
const propGeo = new Map();
const faceMats = {}, edgeMats = {};
const atlasNormal = normalTex.clone(); atlasNormal.repeat.set(9, 9); atlasNormal.needsUpdate = true;
function propMats(ch) {
  if (!faceMats[ch]) {
    faceMats[ch] = new THREE.MeshStandardMaterial({ map: ATLAS[ch], alphaTest: 0.5, alphaToCoverage: true, roughness: 0.9, metalness: 0,
      normalMap: atlasNormal, normalScale: new THREE.Vector2(0.35, 0.35), side: THREE.FrontSide });
    edgeMats[ch] = new THREE.MeshStandardMaterial({ map: ATLAS[ch], color: new THREE.Color(0.86, 0.84, 0.8), roughness: 0.95 });
  }
  return [faceMats[ch], edgeMats[ch]];
}
function propGeometry(ch, name) {
  const k = ch + '/' + name;
  if (propGeo.has(k)) return propGeo.get(k);
  const p = META[ch][name];
  if (!p) { console.warn('missing prop', k); return null; }
  const a = p.aspect, shapes = [];
  for (const s of p.shapes) {
    const sh = new THREE.Shape(s.o.map(([x, y]) => new THREE.Vector2((x - 0.5) * a, y)));
    for (const hh of s.h) sh.holes.push(new THREE.Path(hh.map(([x, y]) => new THREE.Vector2((x - 0.5) * a, y))));
    shapes.push(sh);
  }
  const depth = 0.03;
  const g = new THREE.ExtrudeGeometry(shapes, { depth, bevelEnabled: false });
  g.translate(0, 0, -depth / 2);
  const pos = g.attributes.position, uv = g.attributes.uv;
  const [u0, v0, u1, v1] = p.uv;
  for (let i = 0; i < pos.count; i++) uv.setXY(i, u0 + (pos.getX(i) / a + 0.5) * (u1 - u0), v0 + pos.getY(i) * (v1 - v0));
  g.computeBoundingBox(); g.computeBoundingSphere();
  const out = { g, aspect: a };
  propGeo.set(k, out); return out;
}
const interactive = [];   // pivots that wiggle
const springs = [];
const swayers = [];
const SWAY = /^(odile|fern|monstera|sunflower|appletree|poplar|cactustall|stoolplant|flowercart|lighthouse|streetlamp|toadstools|mushroom)/;
function prop(ch, name, h, opt = {}) {
  const pg = propGeometry(opt.atlas || ch, name);
  const pivot = new THREE.Group();
  if (!pg) return pivot;
  const mesh = new THREE.Mesh(pg.g, propMats(opt.atlas || ch));
  mesh.scale.set(h, h, opt.thick || 1);
  mesh.castShadow = true; mesh.receiveShadow = true;
  pivot.add(mesh);
  pivot.userData = { name, ch: opt.atlas || ch, bay: opt.bay, h, card: CARDS[name] || CARDS[name.replace(/\d$/, '')], label: LABELS[name] || name.replace(/\d$/, ''), s: { a: 0, v: 0, y: 0, vy: 0 }, base: 0 };
  mesh.userData.pivot = pivot;
  if (SWAY.test(name)) { pivot.userData.sw = Math.random() * 6; pivot.userData.sa = name.startsWith('odile') ? 0.018 : name.startsWith('lighthouse') || name.startsWith('streetlamp') ? 0.004 : 0.012; swayers.push(pivot); }
  if (!opt.inert) interactive.push(mesh);
  return pivot;
}
```

## Signs — the copy on paper cards
Each sign is a 1100 × 760 canvas: the rag paper as a pattern at .9 over `#ece2cd`, a ruled border 26 px in, the title in Pixelify
Sans 600 70 px in the chapter ink with a 120 × 7 pink underline, the body in Gaegu 700 47 px on a 62 px line (a blank line adds
26), pink `#d8336f` for starred words, and `chapter one` in Pixelify 30 px bottom right. It is a 1.36-wide card (1.5 in phone
portrait) hung under the thread by two short pink threads with pink pins.
```js
/* ================================================================ signs (copy on paper cards) */
const nolig = t => t.replace(/f([ilf])/g, 'f\u200c$1');
function signTexture(c) {
  const W = 1100, Hh = 760, cv = document.createElement('canvas'); cv.width = W; cv.height = Hh;
  const x = cv.getContext('2d');
  x.fillStyle = '#ece2cd'; x.fillRect(0, 0, W, Hh);
  if (ragImg.complete && ragImg.naturalWidth) { x.globalAlpha = 0.9; const p = x.createPattern(ragImg, 'repeat'); x.fillStyle = p; x.fillRect(0, 0, W, Hh); x.globalAlpha = 1; }
  x.strokeStyle = 'rgba(42,38,34,.32)'; x.lineWidth = 3; x.strokeRect(26, 26, W - 52, Hh - 52);
  x.fillStyle = c.ink; x.font = '600 70px "Pixelify Sans"'; x.textBaseline = 'alphabetic';
  x.fillText(nolig(c.sign.t), 64, 136);
  x.fillStyle = PINK; x.fillRect(64, 158, 120, 7);
  let y = 236; x.font = '700 47px "Gaegu"';
  for (const line of c.sign.b) {
    if (!line) { y += 26; continue; }
    let cx = 64;
    line.split(/(\*[^*]+\*)/).forEach(seg => {
      if (!seg) return;
      const hl = seg.startsWith('*');
      const s = hl ? seg.slice(1, -1) : seg;
      x.fillStyle = hl ? '#d8336f' : '#2a2622';
      x.fillText(nolig(s), cx, y); cx += x.measureText(nolig(s)).width;
    });
    y += 62;
  }
  x.fillStyle = 'rgba(42,38,34,.55)'; x.font = '500 30px "Pixelify Sans"';
  x.fillText(nolig('chapter ' + c.num), W - 64 - x.measureText(nolig('chapter ' + c.num)).width, Hh - 56);
  const t = new THREE.CanvasTexture(cv); t.colorSpace = THREE.SRGBColorSpace; t.anisotropy = Math.min(16, MAXANI);
  return t;
}
function sign(c) {
  const w = PHONE && PORTRAIT ? 1.5 : 1.36, h = w * 760 / 1100;
  const g = new THREE.BoxGeometry(w, h, 0.02);
  const side = paper('#e9dfcb', { ns: 0.2 });
  const face = new THREE.MeshStandardMaterial({ map: signTexture(c), roughness: 0.95, normalMap: ragNormal, normalScale: new THREE.Vector2(0.25, 0.25) });
  const m = new THREE.Mesh(g, [side, side, side, side, face, paper('#e9dfcb')]);
  m.castShadow = m.receiveShadow = true;
  m.position.y = -h / 2 - 0.08;
  const grp = new THREE.Group(); grp.add(m);
  // two short pink threads to the line and a pin
  for (const sx of [-0.42, 0.42]) {
    const th = new THREE.Mesh(new THREE.CylinderGeometry(0.005, 0.005, 0.11, 5), pinkMat); th.position.set(sx * w, -0.045, 0); grp.add(th);
    const pin = new THREE.Mesh(new THREE.SphereGeometry(0.026, 12, 8), pinkMat); pin.position.set(sx * w, -0.1, 0.02); pin.castShadow = true; grp.add(pin);
  }
  grp.userData.signMesh = m;
  return grp;
}
```

## The book — base, walls, threads and hangers
`onWall` places a cut-out flat against the left or right wall of a bay at a distance from the spine; `layer` builds a die-cut
strip spanning the bay at depth z; `thread` hangs a sagging pink tube across the bay and returns a function for points on it;
`hang` puts an object under a pivot on the thread (with a pink string when the drop is longer than .02) and registers it as a
pendulum; `bunting` hangs triangle flags along a thread, skipping given gaps (each chapter leaves ±.75 clear round its sign). The
base band's lettering is drawn on a canvas sized to the text and repeated round the circumference.
```js
/* ================================================================ the book */
const book = new THREE.Group(); scene.add(book);
const bays = [];
const hangers = [];     // pendulums
const anims = [];       // per-frame callbacks (t, dt)

function bayGroup(k) { const g = new THREE.Group(); g.rotation.y = k * 60 * D2R; book.add(g); bays[k] = g; return g; }
function at(obj, x, z, y = FLOOR, ry = 0) { obj.position.set(x, y, z); obj.rotation.y = ry * D2R; return obj; }
/* a point on a wall of the bay: side -1 = left wall, +1 = right; s = distance from spine along the wall, off = inwards */
function onWall(obj, side, s, y, off = 0.025, tilt = 0) {
  const dir = new THREE.Vector2(side * Math.sin(30 * D2R), Math.cos(30 * D2R));
  const nrm = new THREE.Vector2(-side * Math.cos(30 * D2R), Math.sin(30 * D2R));
  obj.position.set(dir.x * s + nrm.x * off, y, dir.y * s + nrm.y * off);
  obj.rotation.y = Math.atan2(nrm.x, nrm.y) + tilt * D2R;
  return obj;
}
function layer(bay, z, hex, fn, { y0 = FLOOR, n = 72, holes = [], d = 0.022, inset = 0.004 } = {}) {
  const hw = z * TAN - inset;
  const s = profileShape(hw, (x, t) => fn(x, t, hw), n, y0);
  for (const h of holes) s.holes.push(h);
  const m = ext(s, d, hex);
  m.position.z = z; bay.add(m); return m;
}
/* a pink thread across the bay with things hanging from it */
function thread(bay, z, y, sag = 0.12, inset = 0.03) {
  const hw = z * TAN - inset;
  const pts = []; for (let i = 0; i <= 24; i++) { const t = i / 24, x = -hw + 2 * hw * t; pts.push(new THREE.Vector3(x, y - sag * 4 * t * (1 - t), z)); }
  const curve = new THREE.CatmullRomCurve3(pts);
  const m = new THREE.Mesh(new THREE.TubeGeometry(curve, 48, 0.0065, 5), pinkMat); m.castShadow = true; bay.add(m);
  return { at: x => new THREE.Vector3(x, y - sag * 4 * ((x + hw) / (2 * hw)) * (1 - (x + hw) / (2 * hw)), z), hw };
}
function hang(bay, th, x, obj, drop = 0.0, opts = {}) {
  const piv = new THREE.Group(); piv.position.copy(th.at(x)); bay.add(piv);
  obj.position.y -= drop; piv.add(obj);
  if (drop > 0.02 && !opts.nostring) {
    const s = new THREE.Mesh(new THREE.CylinderGeometry(0.0045, 0.0045, drop, 4), pinkMat); s.position.y = -drop / 2; piv.add(s);
  }
  hangers.push({ piv, a: 0, v: 0, b: 0, vb: 0, ph: Math.random() * 6, r: th.at(x).z, len: Math.max(0.2, drop + (opts.len || 0.3)) });
  return piv;
}
function bunting(bay, th, colors, step = 0.2, skip = []) {
  const tri = new THREE.Shape(); tri.moveTo(-0.075, 0); tri.lineTo(0.075, 0); tri.lineTo(0, -0.15); tri.closePath();
  let i = 0;
  for (let x = -th.hw + 0.12; x < th.hw - 0.08; x += step) {
    if (skip.some(([a, b]) => x > a && x < b)) continue;
    const m = ext(tri, 0.008, colors[i++ % colors.length]); m.castShadow = true;
    hang(bay, th, x, m, 0.0, { nostring: true, len: 0.1 });
  }
}
function floorSector(bay, hex, map) {
  const s = new THREE.Shape(); s.moveTo(0, 0.02);
  for (let i = 0; i <= 24; i++) { const a = (-30 + 60 * i / 24) * D2R; s.lineTo(Math.sin(a) * (R + 0.01), Math.cos(a) * (R + 0.01)); }
  s.closePath();
  const g = new THREE.ExtrudeGeometry(s, { depth: FLOOR, bevelEnabled: false, curveSegments: 4 });
  g.rotateX(Math.PI / 2); g.translate(0, FLOOR, 0); worldUV(g, 0.5);
  let mat = paper(hex, { ns: 0.4 });
  if (map) { mat = mat.clone(); mat.map = map; mat.color = new THREE.Color(1, 1, 1); }
  const m = new THREE.Mesh(g, [mat, edgeOf(hex)]); m.receiveShadow = true; bay.add(m); return m;
}
function canvasTex(w, h, draw, rep = 1) {
  const cv = document.createElement('canvas'); cv.width = w; cv.height = h; draw(cv.getContext('2d'), w, h);
  const t = new THREE.CanvasTexture(cv); t.colorSpace = THREE.SRGBColorSpace; t.wrapS = t.wrapT = THREE.RepeatWrapping; t.repeat.set(rep, rep); t.anisotropy = Math.min(8, MAXANI); return t;
}
function grain(x, w, h, amt = 18, n = 9000) { for (let i = 0; i < n; i++) { x.fillStyle = `rgba(${Math.random() < .5 ? '0,0,0' : '255,255,255'},${Math.random() * amt / 255})`; x.fillRect(Math.random() * w, Math.random() * h, 1 + Math.random() * 2, 1 + Math.random() * 2); } }

function buildBook() {
  // base board: cream mount board with a cloth edge
  const top = new THREE.Mesh(worldUV(new THREE.CylinderGeometry(R + 0.32, R + 0.32, 0.02, 128, 1), 0.5), paper('#e6dac2', { ns: 0.3 }));
  top.position.y = -0.01; top.receiveShadow = true; book.add(top);
  // the cloth band round the base, foil-stamped
  const bcv = document.createElement('canvas'), bx = bcv.getContext('2d'), txt = 'FOLDWORLD  ✶  A CAROUSEL BOOK IN SIX CHAPTERS  ✶  ODILE PENHALLOW  ✶  PAPER ENGINEER  ✶  ';
  bx.font = '500 54px "Pixelify Sans"'; const tw = Math.ceil(bx.measureText(txt).width);
  bcv.width = tw; bcv.height = 128;
  bx.fillStyle = '#2c5653'; bx.fillRect(0, 0, tw, 128);
  bx.fillStyle = '#d9b46a'; bx.font = '500 54px "Pixelify Sans"'; bx.textBaseline = 'middle'; bx.fillText(txt, 0, 70);
  bx.fillRect(0, 12, tw, 3); bx.fillRect(0, 113, tw, 3);
  const band = new THREE.CanvasTexture(bcv); band.colorSpace = THREE.SRGBColorSpace; band.wrapS = THREE.RepeatWrapping; band.anisotropy = Math.min(8, MAXANI);
  band.repeat.set(Math.max(1, Math.round(TAU * (R + 0.34) / (0.12 * tw / 128))), 1);
  const side = new THREE.Mesh(new THREE.CylinderGeometry(R + 0.32, R + 0.36, 0.12, 128, 1, true), new THREE.MeshStandardMaterial({ map: band, roughness: 0.8, normalMap: ragNormal, normalScale: new THREE.Vector2(0.5, 0.5) }));
  side.position.y = -0.06; side.receiveShadow = true; book.add(side);
  // page walls: two half-thickness slabs so each face takes its own chapter colour
  const ps = new THREE.Shape();
  ps.moveTo(0.03, 0); ps.lineTo(R, 0); ps.lineTo(R, HOUT - 0.22); ps.quadraticCurveTo(R, HOUT, R - 0.22, HOUT);
  ps.bezierCurveTo(R * 0.58, HOUT + 0.02, R * 0.32, H, 0.03, H); ps.closePath();
  for (let j = 0; j < NB; j++) {
    const th = (j * 60 + 30) * D2R, wg = new THREE.Group(); wg.rotation.y = th - Math.PI / 2; book.add(wg);
    const a = ext(ps, T / 2, CH[j].wall, { center: false, edge: '#efe5d1' });
    const b = ext(ps, T / 2, CH[(j + 1) % NB].wall, { center: false, edge: '#efe5d1' }); b.position.z = -T / 2;
    wg.add(a, b);
  }
  // spine
  const sp = new THREE.Mesh(new THREE.CylinderGeometry(0.06, 0.06, H, 16), paper('#2c5653', { nmap: ragNormal, ns: 0.6 })); sp.position.y = H / 2; sp.castShadow = true; book.add(sp);
  CH.forEach((c, k) => { const b = bayGroup(k); BUILD[c.id](b, c, k); });
  book.traverse(o => { if (o.isMesh) { o.castShadow = true; o.receiveShadow = true; } });
}
```

## The six chapters
Every placement is in bay-local units: x across the bay, z out from the spine (the rim is at 3), y up from the floor; the angle is
the last argument in degrees. The front thread is at z 2.85, 2.62 high.
```js
/* ---------------------------------------------------------------- chapters */
const BUILD = {
  work(b, c, k) {
    const mat = canvasTex(512, 512, (x, w, h) => {
      x.fillStyle = '#4a7862'; x.fillRect(0, 0, w, h);
      x.strokeStyle = 'rgba(230,240,225,.32)'; x.lineWidth = 1.5;
      for (let i = 0; i <= 16; i++) { x.beginPath(); x.moveTo(i * 32, 0); x.lineTo(i * 32, h); x.moveTo(0, i * 32); x.lineTo(w, i * 32); x.stroke(); }
      x.strokeStyle = 'rgba(240,248,235,.55)'; x.lineWidth = 3;
      for (let i = 0; i <= 4; i++) { x.beginPath(); x.moveTo(i * 128, 0); x.lineTo(i * 128, h); x.moveTo(0, i * 128); x.lineTo(w, i * 128); x.stroke(); }
      grain(x, w, h, 14);
    }, 1);
    floorSector(b, c.floor, mat);
    // pegboard with punched holes
    const holes = []; const hw = 0.85 * TAN;
    for (let yy = 0.5; yy < 2.25; yy += 0.155) for (let xx = -hw + 0.09; xx < hw - 0.06; xx += 0.155) { const p = new THREE.Path(); p.absarc(xx, yy, 0.022, 0, TAU, true); holes.push(p); }
    layer(b, 0.85, '#a9782d', (x) => 2.35, { holes, n: 4 });
    // pop-up desk
    const top = box(1.3, 0.045, 0.46, '#e5d8bf'); at(top, 0.22, 1.55, 0.55); b.add(top);
    for (const sx of [-0.58, 0.58]) { const l = box(0.04, 0.5, 0.42, '#d7c7aa'); at(l, 0.22 + sx, 1.55, FLOOR + 0.25); b.add(l); }
    b.add(at(prop('work', 'lamp', 0.8, { bay: k }), 0.6, 1.58, 0.575, -12));
    b.add(at(prop('work', 'pencils', 0.36, { bay: k }), -0.18, 1.6, 0.575, 6));
    b.add(at(prop('work', 'teacup2', 0.2, { bay: k }), 0.17, 1.66, 0.575, -8));
    b.add(at(prop('work', 'cactus2', 0.3, { bay: k }), -0.42, 1.52, 0.575, 10));
    // pegboard tools
    b.add(at(prop('work', 'scissors2', 0.36, { bay: k }), -0.18, 0.87, 1.55, 0));
    b.add(at(prop('work', 'spool2', 0.26, { bay: k }), 0.2, 0.87, 1.75, 0));
    b.add(at(prop('work', 'pencils2', 0.3, { bay: k }), 0.08, 0.87, 1.05, 0));
    // floor
    b.add(at(prop('work', 'odile_cut', 1.0, { bay: k }), -0.42, 2.2, FLOOR, 8));
    b.add(at(prop('work', 'cat', 0.56, { bay: k }), 0.66, 2.3, FLOOR, -14));
    b.add(at(prop('work', 'books2', 0.44, { bay: k }), -1.02, 2.5, FLOOR, 22));
    b.add(at(prop('work', 'spool', 0.36, { bay: k }), 1.12, 2.62, FLOOR, -26));
    const sc = prop('work', 'scissors', 0.5, { bay: k }); at(sc, 0.15, 2.72, FLOOR + 0.02, 0); sc.rotation.x = -Math.PI / 2; sc.rotation.z = 0.5; b.add(sc);
    // shelves on the walls
    for (const [side, s, y, items] of [[-1, 1.75, 1.55, [['books', 0.38], ['cactus', 0.32]]], [1, 1.9, 1.3, [['teacup', 0.2], ['crane2', 0.36]]]]) {
      const sh = box(0.62, 0.035, 0.2, '#e5d8bf'); onWall(sh, side, s, y, 0.11); b.add(sh);
      items.forEach(([n, h], i) => { const p = prop('work', n, h, { bay: k }); onWall(p, side, s + (i - 0.5) * 0.3, y + 0.018, 0.12); b.add(p); });
    }
    b.add(onWall(prop('work', 'lamp2', 0.5, { bay: k }), 1, 1.0, 2.25, 0.03));
    const th = thread(b, 2.85, 2.62, 0.14);
    bunting(b, th, ['#ff4f8b', '#efe5d1', '#3f7f7b', '#e0a43c'], 0.19, [[c.sx * (PORTRAIT ? 0 : 1) - 0.75, c.sx * (PORTRAIT ? 0 : 1) + 0.75]]);
    hang(b, th, 0.95, at(prop('work', 'crane', 0.32, { bay: k }), 0, 0, -0.32), 0.12);
    hang(b, th, PORTRAIT ? 0 : c.sx, sign(c), 0.0, { len: 0.55 });
  },

  tide(b, c, k) {
    floorSector(b, c.floor);
    // sun and clouds on the walls
    const sun = ext((() => { const s = new THREE.Shape(); s.absarc(0, 0, 0.34, 0, TAU, false); return s; })(), 0.02, '#e9a447');
    onWall(sun, 1, 1.0, 2.3, 0.03); b.add(sun);
    [[-1, 2.0, 2.55, 0.8, 3], [-1, 1.0, 2.6, 0.7, 5], [1, 2.3, 2.1, 0.55, 7], [1, 1.7, 2.75, 0.5, 9]].forEach(([sd, s, y, w, sd2]) => { const m = ext(cloudShape(w, w * 0.45, sd2), 0.03, '#eee6d6'); onWall(m, sd, s, y, 0.05); b.add(m); });
    // island with the lighthouse
    layer(b, 0.78, '#7f9a72', (x, t, hw) => 0.42 + 0.28 * Math.exp(-(((x - 0.24) / 0.22) ** 2)) + 0.03 * Math.sin(x * 19));
    b.add(at(prop('tide', 'lighthouse2', 1.45, { bay: k }), 0.24, 0.93, 0.5, 0));
    // sea: four rocking layers
    const sea = [[1.22, '#24566b', 0.52, 0.06], [1.62, '#3f8b98', 0.44, 0.07], [2.05, '#2f6f86', 0.36, 0.06], [2.42, '#4f9ca3', 0.27, 0.05]];
    sea.forEach(([z, col, base, amp], i) => {
      const m = layer(b, z, col, (x) => base + amp * Math.sin(x * 7.5 + i * 1.7) + amp * 0.35 * Math.sin(x * 17 + i));
      const foam = layer(b, z + 0.02, '#ece4d3', (x) => base * 0.42 + amp * 0.5 * Math.sin(x * 7.5 + i * 1.7 + 0.6), { y0: base * 0.42 - 0.05, d: 0.008 });
      foam.visible = i % 2 === 1;
      anims.push((t) => { m.rotation.x = Math.sin(t * 0.9 + i) * 0.035; m.position.x = Math.sin(t * 0.7 + i * 2) * 0.012; });
    });
    const boat = at(prop('tide', 'sailboat', 0.72, { bay: k }), -0.36, 1.42, 0.2, 8); b.add(boat);
    anims.push((t) => { boat.position.y = 0.2 + Math.sin(t * 1.3) * 0.035; boat.rotation.z = Math.sin(t * 1.1) * 0.06; });
    const wh = at(prop('tide', 'whale', 0.55, { bay: k }), 0.58, 1.85, 0.14, -6); b.add(wh);
    anims.push((t) => { wh.position.y = 0.14 + Math.sin(t * 0.8 + 1) * 0.05; });
    b.add(at(prop('tide', 'buoy2', 0.32, { bay: k }), -0.82, 1.82, 0.2, 0));
    // beach
    b.add(at(prop('tide', 'odile_row', 0.8, { atlas: 'work', bay: k }), -0.5, 2.62, FLOOR, 6));
    b.add(at(prop('tide', 'hut', 0.78, { bay: k }), 1.0, 2.6, FLOOR, -24));
    b.add(at(prop('tide', 'crab', 0.22, { bay: k }), 0.32, 2.82, FLOOR, -10));
    const sf = prop('tide', 'starfish', 0.2, { bay: k }); at(sf, -0.05, 2.78, FLOOR + 0.02); sf.rotation.x = -Math.PI / 2; b.add(sf);
    b.add(at(prop('tide', 'rowboat2', 0.3, { bay: k }), 0.5, 2.5, FLOOR, -18));
    b.add(at(prop('tide', 'starfish2', 0.16, { bay: k }), 1.38, 2.86, FLOOR, -30));
    const th = thread(b, 2.85, 2.62, 0.13);
    const g1 = hang(b, th, PORTRAIT ? -0.95 : 0.62, at(prop('tide', 'gull', 0.3, { bay: k }), 0, 0, -0.5), 0.36);
    const g2 = hang(b, th, PORTRAIT ? 1.0 : 1.2, at(prop('tide', 'gull2', 0.26, { bay: k }), 0, 0, -0.3), 0.18);
    bunting(b, th, ['#efe5d1', '#24566b', '#ff4f8b'], 0.2, [[(PORTRAIT ? 0 : c.sx) - 0.75, (PORTRAIT ? 0 : c.sx) + 0.75], [0.45, 0.8], [1.05, 1.4], [-1.1, -0.8]]);
    hang(b, th, PORTRAIT ? 0 : c.sx, sign(c), 0, { len: 0.55 });
  },

  night(b, c, k) {
    floorSector(b, c.floor);
    // moon, stars
    b.add(onWall(prop('night', 'moon', 0.62, { bay: k }), -1, 1.45, 2.05, 0.04));
    [[1, 1.0, 2.6, 0.07], [1, 2.2, 2.25, 0.05], [-1, 2.35, 2.5, 0.06], [-1, 0.7, 2.75, 0.045], [1, 1.6, 2.85, 0.04]].forEach(([sd, s, y, r]) => { const m = ext(starShape(r), 0.012, '#f0d58a'); onWall(m, sd, s, y, 0.03); b.add(m); });
    // rolling hills
    const hills = [[0.75, '#26384a', 0.85, 0.22], [1.25, '#2d4a3d', 0.62, 0.16], [1.85, '#3a5a40', 0.4, 0.12], [2.5, '#4a6a43', 0.18, 0.05]];
    hills.forEach(([z, col, base, amp], i) => layer(b, z, col, (x) => base + amp * Math.sin(x * (3.2 + i) + i * 2.1) + (i === 3 ? 0.04 * Math.abs(Math.sin(x * 40)) : 0)));
    b.add(at(prop('night', 'poplar', 1.05, { bay: k }), 0.28, 1.05, 0.42, 0));
    b.add(at(prop('night', 'poplar2', 0.85, { bay: k }), -0.32, 0.98, 0.5, 0));
    b.add(at(prop('night', 'appletree', 1.0, { bay: k }), -0.55, 1.55, 0.28, 6));
    b.add(at(prop('night', 'appletree2', 0.86, { bay: k }), 0.7, 1.98, 0.2, -10));
    b.add(onWall(prop('night', 'owl2', 0.46, { bay: k }), 1, 1.65, 1.35, 0.06, -8));
    b.add(at(prop('night', 'toadstools', 0.3, { bay: k }), 0.22, 2.75, FLOOR, -6));
    b.add(at(prop('night', 'fox', 0.32, { bay: k }), 0.92, 2.6, FLOOR, -22));
    b.add(at(prop('night', 'hedgehog', 0.24, { bay: k }), -1.0, 2.66, FLOOR, 18));
    b.add(at(prop('night', 'rabbit2', 0.36, { bay: k }), -0.68, 2.22, FLOOR, 12));
    const od = at(prop('night', 'odile_lantern2', 1.0, { atlas: 'work', bay: k }), -0.08, 2.3, FLOOR, 0); b.add(od);
    // her lantern glows: a warm light and a soft sprite
    const lamp = new THREE.PointLight('#ffc46b', PHONE ? 1.4 : 2.2, 2.6, 1.6); lamp.position.set(0.27, 0.5, 0.12); od.add(lamp);
    const glow = new THREE.Sprite(new THREE.SpriteMaterial({ map: glowTex(), color: '#ffcf7a', transparent: true, blending: THREE.AdditiveBlending, depthWrite: false, opacity: 0.75 }));
    glow.scale.set(0.5, 0.5, 1); glow.position.set(0.27, 0.48, 0.05); od.add(glow);
    anims.push((t) => { const f = 0.85 + Math.sin(t * 7) * 0.05 + Math.sin(t * 13.3) * 0.04; lamp.intensity = (PHONE ? 1.4 : 2.2) * f; glow.material.opacity = 0.7 * f; });
    // fireflies
    const N = PHONE ? 26 : 44, ff = new Float32Array(N * 3), seeds = [];
    for (let i = 0; i < N; i++) { const z = 0.9 + Math.random() * 1.9, x = (Math.random() * 2 - 1) * z * TAN * 0.9, y = 0.35 + Math.random() * 1.9; seeds.push([x, y, z, Math.random() * 6]); }
    const fg = new THREE.BufferGeometry(); fg.setAttribute('position', new THREE.BufferAttribute(ff, 3));
    const fp = new THREE.Points(fg, new THREE.PointsMaterial({ map: glowTex(), color: '#ffe08a', size: 0.09, transparent: true, depthWrite: false, blending: THREE.AdditiveBlending }));
    b.add(fp);
    anims.push((t) => { for (let i = 0; i < N; i++) { const [x, y, z, p] = seeds[i]; ff[i * 3] = x + Math.sin(t * 0.5 + p) * 0.08; ff[i * 3 + 1] = y + Math.sin(t * 0.7 + p * 2) * 0.07; ff[i * 3 + 2] = z + Math.cos(t * 0.4 + p) * 0.06; } fg.attributes.position.needsUpdate = true; fp.material.opacity = 0.75 + 0.25 * Math.sin(t * 3); });
    const th = thread(b, 2.85, 2.62, 0.13);
    hang(b, th, PORTRAIT ? 0.95 : 0.55, at(prop('night', 'lantern', 0.42, { bay: k }), 0, 0, -0.42), 0.12);
    [-1.25, -0.05, 1.0, 1.3].forEach((x, i) => { if (Math.abs(x - (PORTRAIT ? 0 : c.sx)) < 0.75) return; hang(b, th, x, ext(starShape(0.07 + i * 0.01), 0.012, '#f0d58a'), 0.18 + i * 0.09); });
    hang(b, th, PORTRAIT ? 0 : c.sx, sign(c), 0, { len: 0.55 });
  },

  market(b, c, k) {
    const cob = canvasTex(512, 512, (x, w, h) => {
      x.fillStyle = '#8f857a'; x.fillRect(0, 0, w, h);
      for (let r = 0; r < 16; r++) for (let q = 0; q < 12; q++) {
        const ox = (q + (r % 2) * 0.5) * 44, oy = r * 32; const l = 150 + Math.random() * 40;
        x.fillStyle = `rgb(${l + 10},${l},${l - 12})`; x.beginPath(); x.roundRect(ox + 2, oy + 2, 40, 28, 9); x.fill();
      }
      grain(x, w, h, 16);
    }, 1);
    floorSector(b, c.floor, cob);
    // rails for the tram
    for (const dz of [-0.09, 0.09]) { const rl = box(3.0, 0.012, 0.025, '#5b5550'); at(rl, 0, 2.18 + dz, FLOOR + 0.006); b.add(rl); }
    // skyline: two cut-paper rows with punched windows
    const sky = (z, hex, seed, hmin, hmax) => {
      const hw = z * TAN, r = rnd(seed), xs = []; let x = -hw;
      while (x < hw) { const w = 0.16 + r() * 0.16; xs.push([x, x + w, hmin + r() * (hmax - hmin), r() < 0.5]); x += w; }
      const s = new THREE.Shape(); s.moveTo(-hw, FLOOR);
      for (const [a, bb, hh, peak] of xs) { s.lineTo(a, hh); if (peak) s.lineTo((a + bb) / 2, hh + 0.12); s.lineTo(Math.min(bb, hw), hh); }
      s.lineTo(hw, FLOOR); s.closePath();
      for (const [a, bb, hh] of xs) for (let yy = 0.35; yy < hh - 0.12; yy += 0.2) for (let xx = a + 0.05; xx < bb - 0.06 && xx < hw - 0.08; xx += 0.09) { if (xx < -hw + 0.05) continue; const p = new THREE.Path(); p.moveTo(xx, yy); p.lineTo(xx + 0.04, yy); p.lineTo(xx + 0.04, yy + 0.07); p.lineTo(xx, yy + 0.07); p.closePath(); s.holes.push(p); }
      const m = ext(s, 0.02, hex); m.position.z = z; b.add(m);
    };
    sky(0.72, '#e6d6ba', 3, 1.5, 2.3);
    sky(1.05, '#2f5f5c', 8, 0.9, 1.6);
    // windows glow behind the back row
    const back = layer(b, 0.66, '#f4c46a', () => 1.45, { n: 2 }); back.material[0] = new THREE.MeshStandardMaterial({ color: '#f2c06a', emissive: '#f0b04a', emissiveIntensity: 0.35, roughness: 1 });
    b.add(at(prop('market', 'townhouse', 1.28, { bay: k }), 0.32, 1.32, FLOOR, -4));
    b.add(at(prop('market', 'bakery', 1.12, { bay: k }), -0.42, 1.45, FLOOR, 6));
    b.add(at(prop('market', 'townhouse2', 1.18, { bay: k }), -0.98, 1.92, FLOOR, 24));
    b.add(at(prop('market', 'bakery2', 1.02, { bay: k }), 1.0, 1.98, FLOOR, -26));
    const tram = at(prop('market', 'tram', 0.56, { bay: k }), 0, 2.18, FLOOR + 0.012, 0); b.add(tram);
    anims.push((t) => { tram.position.x = Math.sin(t * 0.32) * 0.32; });
    b.add(at(prop('market', 'streetlamp', 1.0, { bay: k }), -0.72, 2.5, FLOOR, 0));
    b.add(at(prop('market', 'odile_wave2', 0.96, { atlas: 'work', bay: k }), -0.3, 2.58, FLOOR, 4));
    b.add(at(prop('market', 'bicycle', 0.4, { bay: k }), 0.66, 2.6, FLOOR, -12));
    b.add(at(prop('market', 'flowercart', 0.5, { bay: k }), -1.14, 2.76, FLOOR, 24));
    b.add(at(prop('market', 'dog', 0.3, { bay: k }), 0.28, 2.8, FLOOR, -10));
    b.add(at(prop('market', 'pigeon', 0.17, { bay: k }), -0.02, 2.92, FLOOR, 14));
    b.add(at(prop('market', 'fruitstall2', 0.42, { bay: k }), 1.24, 2.78, FLOOR, -30));
    const th = thread(b, 2.85, 2.62, 0.14);
    bunting(b, th, ['#ff4f8b', '#e9a447', '#efe5d1', '#3f7f7b'], 0.18, [[(PORTRAIT ? 0 : c.sx) - 0.75, (PORTRAIT ? 0 : c.sx) + 0.75]]);
    hang(b, th, PORTRAIT ? 0 : c.sx, sign(c), 0, { len: 0.55 });
  },

  glass(b, c, k) {
    const tiles = canvasTex(512, 512, (x, w, h) => {
      for (let r = 0; r < 8; r++) for (let q = 0; q < 8; q++) { const l = (r + q) % 2; x.fillStyle = l ? '#b8744e' : '#e4d2b0'; x.fillRect(q * 64, r * 64, 64, 64); }
      x.strokeStyle = 'rgba(70,40,20,.35)'; x.lineWidth = 2; for (let i = 0; i <= 8; i++) { x.beginPath(); x.moveTo(i * 64, 0); x.lineTo(i * 64, h); x.moveTo(0, i * 64); x.lineTo(w, i * 64); x.stroke(); }
      grain(x, w, h, 16);
    }, 1);
    floorSector(b, c.floor, tiles);
    // leafy backdrop
    layer(b, 0.8, '#5f7d55', (x) => 1.25 + 0.12 * Math.abs(Math.sin(x * 9)) + 0.08 * Math.sin(x * 3));
    layer(b, 1.15, '#76955f', (x) => 0.55 + 0.1 * Math.abs(Math.sin(x * 12 + 1)));
    // the glasshouse: a die-cut frame of arched panes
    const z = 2.35, hw = z * TAN - 0.004, top = 2.35, bar = 0.055;
    const s = new THREE.Shape(); s.moveTo(-hw, FLOOR); s.lineTo(hw, FLOOR); s.lineTo(hw, top - 0.5); s.quadraticCurveTo(hw, top, 0, top + 0.12); s.quadraticCurveTo(-hw, top, -hw, top - 0.5); s.closePath();
    const cols = 4, pw = (2 * hw - bar * (cols + 1)) / cols;
    for (let i = 0; i < cols; i++) {
      const x0 = -hw + bar + i * (pw + bar);
      for (const [y0, y1, arch] of [[0.42, 1.02, false], [1.02 + bar, 1.6, true]]) {
        const p = new THREE.Path(); p.moveTo(x0, y0); p.lineTo(x0 + pw, y0); p.lineTo(x0 + pw, y1 - (arch ? pw * 0.5 : 0));
        if (arch) p.quadraticCurveTo(x0 + pw, y1, x0 + pw / 2, y1 + 0.02), p.quadraticCurveTo(x0, y1, x0, y1 - pw * 0.5);
        if (!arch) p.lineTo(x0, y1);
        p.lineTo(x0, y0); s.holes.push(p);
      }
    }
    // a fan light in the gable
    const fc = 1.72, fr = 0.5, nf = 5;
    for (let i = 0; i < nf; i++) {
      const a0 = (i / nf) * Math.PI + 0.06, a1 = ((i + 1) / nf) * Math.PI - 0.06;
      const p = new THREE.Path(); p.moveTo(Math.cos(a0) * 0.12, fc + Math.sin(a0) * 0.12);
      p.absarc(0, fc, fr, a0, a1, false); p.lineTo(Math.cos(a1) * 0.12, fc + Math.sin(a1) * 0.12); p.absarc(0, fc, 0.12, a1, a0, true); s.holes.push(p);
    }
    const gh = ext(s, 0.024, '#e8dfcb'); gh.position.z = z; b.add(gh);
    b.add(at(prop('glass', 'monstera', 0.74, { bay: k }), -0.45, 1.32, FLOOR, 8));
    b.add(at(prop('glass', 'fern', 0.6, { bay: k }), 0.38, 1.2, FLOOR, -6));
    b.add(at(prop('glass', 'sunflower', 1.12, { bay: k }), -0.12, 1.62, FLOOR, 0));
    b.add(at(prop('glass', 'sunflower2', 0.95, { bay: k }), 0.22, 1.85, FLOOR, -4));
    b.add(at(prop('glass', 'cactustall', 0.68, { bay: k }), 0.72, 1.78, FLOOR, -14));
    b.add(at(prop('glass', 'monstera2', 0.64, { bay: k }), -0.86, 2.02, FLOOR, 20));
    b.add(at(prop('glass', 'mushroom', 0.28, { bay: k }), -0.38, 2.1, FLOOR, 4));
    b.add(at(prop('glass', 'wheelbarrow', 0.38, { bay: k }), 0.58, 2.18, FLOOR, -18));
    b.add(at(prop('glass', 'odile_water', 0.86, { atlas: 'work', bay: k }), -0.3, 2.66, FLOOR, 4));
    b.add(at(prop('glass', 'wateringcan2', 0.3, { bay: k }), 0.5, 2.72, FLOOR, -14));
    b.add(at(prop('glass', 'snail', 0.17, { bay: k }), 0.08, 2.86, FLOOR, -6));
    b.add(at(prop('glass', 'fern2', 0.5, { bay: k }), 1.2, 2.66, FLOOR, -28));
    b.add(at(prop('glass', 'mushroom2', 0.24, { bay: k }), -1.12, 2.78, FLOOR, 24));
    b.add(onWall(prop('glass', 'cactus2', 0.28, { atlas: 'work', bay: k }), -1, 1.7, 1.05, 0.05));
    const th = thread(b, 2.85, 2.62, 0.13);
    const th2 = thread(b, 1.5, 2.25, 0.1);
    [[-0.4, 'butterfly', 0.3], [0.45, 'butterfly2', 0.5]].forEach(([x, n, d], i) => {
      const bf = prop('glass', n, 0.26, { bay: k }); const p = hang(b, th2, x, bf, d);
      anims.push((t) => { bf.scale.x = 0.55 + 0.45 * Math.abs(Math.cos(t * 5 + i * 2)); bf.position.y = -d + Math.sin(t * 1.4 + i) * 0.04; });
    });
    bunting(b, th, ['#ede4d2', '#ff4f8b', '#5f7d55'], 0.2, [[(PORTRAIT ? 0 : c.sx) - 0.75, (PORTRAIT ? 0 : c.sx) + 0.75]]);
    hang(b, th, PORTRAIT ? 0 : c.sx, sign(c), 0, { len: 0.55 });
  },

  post(b, c, k) {
    floorSector(b, c.floor);
    // pigeonholes
    const z = 0.95, hw = z * TAN - 0.004, s = profileShape(hw, () => 2.3, 2), cols = 4, rows = 5, pw = (2 * hw - 0.06 * (cols + 1)) / cols, ph = 0.28;
    for (let i = 0; i < cols; i++) for (let j = 0; j < rows; j++) { const x0 = -hw + 0.06 + i * (pw + 0.06), y0 = 0.62 + j * (ph + 0.06); const p = new THREE.Path(); p.moveTo(x0, y0); p.lineTo(x0 + pw, y0); p.lineTo(x0 + pw, y0 + ph); p.lineTo(x0, y0 + ph); p.closePath(); s.holes.push(p); }
    const pg = ext(s, 0.03, '#e9dfcb'); pg.position.z = z; b.add(pg);
    layer(b, z - 0.12, '#7d4652', () => 2.3, { n: 2 });
    const r = rnd(4);
    for (let i = 0; i < cols; i++) for (let j = 0; j < rows; j++) {
      if (r() < 0.3) continue;
      const x0 = -hw + 0.06 + i * (pw + 0.06) + pw / 2, y0 = 0.62 + j * (ph + 0.06);
      const e = prop('post', r() < 0.5 ? 'envelope' : 'envelope2', 0.14 + r() * 0.06, { bay: k, inert: true }); at(e, x0 + (r() - 0.5) * 0.05, z - 0.06, y0 + 0.01, 0); e.rotation.z = (r() - 0.5) * 0.4; b.add(e);
    }
    b.add(at(prop('post', 'desk2', 0.72, { bay: k }), 0.42, 1.5, FLOOR, -8));
    b.add(at(prop('post', 'stoolplant', 0.56, { bay: k }), -0.52, 1.45, FLOOR, 8));
    b.add(at(prop('post', 'odile_post', 1.06, { atlas: 'work', bay: k }), -0.22, 2.32, FLOOR, 4));
    b.add(at(prop('post', 'satchel', 0.3, { bay: k }), 0.72, 2.5, FLOOR, -14));
    b.add(at(prop('post', 'parcel2', 0.28, { bay: k }), 1.08, 2.74, FLOOR, -26));
    b.add(at(prop('post', 'parcel', 0.24, { bay: k }), 1.06, 2.74, FLOOR + 0.25, -20));
    b.add(at(prop('post', 'letters', 0.22, { bay: k }), 0.28, 2.82, FLOOR, -6));
    b.add(at(prop('post', 'letters2', 0.2, { bay: k }), -1.02, 2.72, FLOOR, 22));
    b.add(at(prop('post', 'stoolplant2', 0.48, { bay: k }), -0.95, 2.1, FLOOR, 22));
    b.add(onWall(prop('post', 'dove2', 0.36, { bay: k }), 1, 1.75, 1.55, 0.06, -6));
    // paper planes loop round the room
    [['plane', 0], ['plane2', Math.PI]].forEach(([n, ph0]) => {
      const pl = prop('post', n, 0.24, { bay: k }); const holder = new THREE.Group(); holder.add(pl); b.add(holder);
      anims.push((t) => { const a = t * 0.55 + ph0; holder.position.set(Math.sin(a) * 0.62, 1.95 + Math.sin(a * 2) * 0.12, 1.75 + Math.cos(a) * 0.45); holder.rotation.y = a + Math.PI / 2 + Math.PI; holder.rotation.z = Math.sin(a * 2) * 0.15; });
    });
    const th = thread(b, 2.85, 2.62, 0.13);
    [-1.3, -0.05, 0.35, 1.25].forEach((x, i) => { if (Math.abs(x - (PORTRAIT ? 0 : c.sx)) < 0.75) return; hang(b, th, x, at(prop('post', i % 2 ? 'envelope' : 'envelope2', 0.17, { bay: k }), 0, 0, -0.18), 0.1); });
    hang(b, th, PORTRAIT ? 0.9 : 0.85, at(prop('post', 'dove', 0.3, { bay: k }), 0, 0, -0.3), 0.3);
    hang(b, th, PORTRAIT ? 0 : c.sx, sign(c), 0, { len: 0.55 });
  },
};
let _glow;
function glowTex() {
  if (_glow) return _glow;
  const cv = document.createElement('canvas'); cv.width = cv.height = 64; const x = cv.getContext('2d');
  const g = x.createRadialGradient(32, 32, 0, 32, 32, 32); g.addColorStop(0, 'rgba(255,255,255,1)'); g.addColorStop(0.25, 'rgba(255,240,200,.6)'); g.addColorStop(1, 'rgba(255,220,150,0)');
  x.fillStyle = g; x.fillRect(0, 0, 64, 64); _glow = new THREE.CanvasTexture(cv); return _glow;
}
```

## The table, the backdrop dome and the dust
The book stands on a birch table (a 26-radius disc, the wood repeated 5×, tinted `#d8c8ae`), on a green cutting mat 9.5 × 7.2
turned .12 rad; a giant hexagonal yellow pencil with a ferrule and a pink eraser, a spool of pink thread, a ruler with drawn ticks
and numbers, and 18 paper scraps in the chapter colours lie round it. The background is a back-faced 45-radius sphere shaded by
height from `#77624f` to `#3a2f27`, with a warm `#b39676` glow behind the book, drawn without fog. 90 dust motes (40 on phones)
rise slowly through the lamp light.
```js
/* ================================================================ the table and its giant tools */
function buildBackdrop() {
  const m = new THREE.ShaderMaterial({ side: THREE.BackSide, depthWrite: false, fog: false,
    uniforms: { top: { value: new THREE.Color('#3a2f27') }, mid: { value: new THREE.Color('#77624f') }, glow: { value: new THREE.Color('#b39676') } },
    vertexShader: 'varying vec3 vD; void main(){ vD = normalize(position); gl_Position = projectionMatrix*modelViewMatrix*vec4(position,1.); }',
    fragmentShader: `uniform vec3 top, mid, glow; varying vec3 vD;
      void main(){ float y = vD.y; vec3 c = mix(mid, top, smoothstep(0.02, 0.5, y));
        float g = pow(max(0., dot(normalize(vD), normalize(vec3(-0.25, 0.12, -1.)))), 6.); c = mix(c, glow, g*.8);
        gl_FragColor = vec4(c, 1.); }` });
  const sky = new THREE.Mesh(new THREE.SphereGeometry(45, 32, 16), m); scene.add(sky);
  scene.background = null;
}
function buildDust() {
  const N = PHONE ? 40 : 90, pos = new Float32Array(N * 3), seed = [];
  for (let i = 0; i < N; i++) seed.push([(Math.random() - 0.5) * 7, Math.random() * 3.2, 0.5 + Math.random() * 4.5, Math.random() * 6, 0.3 + Math.random() * 0.7]);
  const g = new THREE.BufferGeometry(); g.setAttribute('position', new THREE.BufferAttribute(pos, 3));
  const m = new THREE.PointsMaterial({ map: glowTex(), color: '#fff1d6', size: 0.035, transparent: true, opacity: 0.55, depthWrite: false, blending: THREE.AdditiveBlending });
  const pts = new THREE.Points(g, m); scene.add(pts);
  anims.push((t) => { for (let i = 0; i < N; i++) { const [x, y, z, p, sp] = seed[i]; pos[i * 3] = x + Math.sin(t * 0.13 * sp + p) * 0.4; pos[i * 3 + 1] = ((y + t * 0.035 * sp) % 3.4) + 0.05; pos[i * 3 + 2] = z + Math.cos(t * 0.11 * sp + p) * 0.3; } g.attributes.position.needsUpdate = true; });
}
function buildTable() {
  const t = new THREE.Mesh(new THREE.CircleGeometry(26, 64), new THREE.MeshStandardMaterial({ map: woodTex, roughness: 0.82, color: new THREE.Color('#d8c8ae') }));
  t.rotation.x = -Math.PI / 2; t.position.y = -0.12; t.receiveShadow = true;
  woodTex.repeat.set(5, 5);
  scene.add(t);
  // a cutting mat under the book
  const mat = new THREE.Mesh(new THREE.BoxGeometry(9.5, 0.02, 7.2), paper('#3b6b5a', { ns: 0.3 })); worldUV(mat.geometry, 0.4);
  mat.position.set(0.4, -0.11, -0.4); mat.rotation.y = 0.12; mat.receiveShadow = true; scene.add(mat);
  // giant pencil
  const pencil = new THREE.Group();
  const body = new THREE.Mesh(new THREE.CylinderGeometry(0.16, 0.16, 5.2, 6), paper('#e3a63c', { ns: 0.3 })); body.rotation.z = Math.PI / 2;
  const wood = new THREE.Mesh(new THREE.ConeGeometry(0.16, 0.5, 6), paper('#e8cfa4')); wood.rotation.z = -Math.PI / 2; wood.position.x = 2.85;
  const lead = new THREE.Mesh(new THREE.ConeGeometry(0.055, 0.17, 6), paper('#3a3633')); lead.rotation.z = -Math.PI / 2; lead.position.x = 3.18;
  const ferr = new THREE.Mesh(new THREE.CylinderGeometry(0.17, 0.17, 0.3, 12), new THREE.MeshStandardMaterial({ color: '#b9b3a6', roughness: 0.35, metalness: 0.7 })); ferr.rotation.z = Math.PI / 2; ferr.position.x = -2.75;
  const eras = new THREE.Mesh(new THREE.CylinderGeometry(0.16, 0.16, 0.26, 12), paper('#ff7aa3')); eras.rotation.z = Math.PI / 2; eras.position.x = -3.02;
  pencil.add(body, wood, lead, ferr, eras); pencil.traverse(o => { o.castShadow = o.receiveShadow = true; });
  pencil.position.set(-5.3, 0.04, 2.6); pencil.rotation.y = -0.95; scene.add(pencil);
  // giant spool of pink thread
  const spool = new THREE.Group();
  const s1 = new THREE.Mesh(new THREE.CylinderGeometry(0.75, 0.75, 0.12, 40), paper('#cfa874')); const s2 = s1.clone(); s2.position.y = 1.18;
  const th = new THREE.Mesh(new THREE.CylinderGeometry(0.62, 0.62, 1.06, 40), new THREE.MeshStandardMaterial({ color: '#ff6f9c', roughness: 0.85, normalMap: ragNormal, normalScale: new THREE.Vector2(0.6, 0.6) }));
  s1.position.y = 0.06; th.position.y = 0.6; spool.add(s1, s2, th); spool.traverse(o => { o.castShadow = o.receiveShadow = true; });
  spool.position.set(5.0, -0.12, 0.4); scene.add(spool);
  // ruler
  const rul = new THREE.Mesh(new THREE.BoxGeometry(6, 0.05, 0.7), new THREE.MeshStandardMaterial({ map: canvasTex(1024, 128, (x, w, h) => { x.fillStyle = '#efe6cf'; x.fillRect(0, 0, w, h); x.fillStyle = '#3a3633'; for (let i = 0; i < 100; i++) { const L = i % 10 === 0 ? 46 : i % 5 === 0 ? 30 : 18; x.fillRect(12 + i * 10, 0, 2, L); if (i % 10 === 0) { x.font = '600 20px "Pixelify Sans"'; x.fillText(String(i / 10), 16 + i * 10, 74); } } }), roughness: 0.6 }));
  rul.position.set(3.4, -0.08, 4.6); rul.rotation.y = 0.32; rul.receiveShadow = true; rul.castShadow = true; scene.add(rul);
  // paper scraps
  const r = rnd(11);
  for (let i = 0; i < 18; i++) {
    const a = r() * TAU, d = 4.0 + r() * 3.0; if (Math.cos(a) > 0.55 && d < 5) continue;
    const s = new THREE.Shape(); const n = 3 + Math.floor(r() * 3); for (let j = 0; j < n; j++) { const aa = j / n * TAU + r() * 0.6, rr = 0.12 + r() * 0.2; j ? s.lineTo(Math.cos(aa) * rr, Math.sin(aa) * rr) : s.moveTo(Math.cos(aa) * rr, Math.sin(aa) * rr); }
    const m = ext(s, 0.01, ['#c9973f', '#3f7f7b', '#c4583f', '#8aa27a', '#c27a86', '#efe5d1', '#ff4f8b'][i % 7]);
    m.rotation.x = -Math.PI / 2; m.rotation.z = r() * 6; m.position.set(Math.sin(a) * d, -0.095, Math.cos(a) * d); scene.add(m);
  }
}
```

## Post-processing — GTAO and the grade
A half-float render target with 4 samples; the scene pass; GTAO on desktop only (radius .32, 16 samples, denoised, blended at .85;
`?noao` turns it off); the output pass (tone mapping and sRGB); then the grade, in display space: 7% desaturation, a warm tint
(1.025, 1, .965), an 18% smoothstep contrast, a vignette of .22 from .42 to 1.12 of the aspect-corrected radius, and ±.016
animated grain.
```js
/* ================================================================ post */
let composer, gtao, grade;
function buildPost() {
  const rt = new THREE.WebGLRenderTarget(innerWidth * DPR, innerHeight * DPR, { type: THREE.HalfFloatType, samples: 4 });
  composer = new EffectComposer(renderer, rt);
  composer.setPixelRatio(DPR); composer.setSize(innerWidth, innerHeight);
  composer.addPass(new RenderPass(scene, camera));
  if (!PHONE && !Q.has('noao')) {
    gtao = new GTAOPass(scene, camera, innerWidth, innerHeight);
    gtao.updateGtaoMaterial({ radius: 0.32, distanceExponent: 1.4, thickness: 0.6, scale: 1.0, samples: 16 });
    gtao.updatePdMaterial({ lumaPhi: 10, depthPhi: 2, normalPhi: 3, radius: 6, rings: 2, samples: 12 });
    gtao.blendIntensity = 0.85;
    composer.addPass(gtao);
  }
  composer.addPass(new OutputPass());
  grade = new ShaderPass({
    uniforms: { tDiffuse: { value: null }, uTime: { value: 0 }, uRes: { value: new THREE.Vector2(innerWidth, innerHeight) } },
    vertexShader: 'varying vec2 vUv; void main(){ vUv=uv; gl_Position=projectionMatrix*modelViewMatrix*vec4(position,1.); }',
    fragmentShader: `uniform sampler2D tDiffuse; uniform float uTime; uniform vec2 uRes; varying vec2 vUv;
      float h(vec2 p){ return fract(sin(dot(p,vec2(12.9898,78.233)))*43758.5453); }
      void main(){
        vec3 c = texture2D(tDiffuse, vUv).rgb;
        float l = dot(c, vec3(.299,.587,.114));
        c = mix(vec3(l), c, .93);
        c *= vec3(1.025, 1.0, .965);
        c = mix(c, c*c*(3.-2.*c), .18);
        vec2 q = vUv - .5; q.x *= uRes.x/uRes.y;
        c *= 1. - .22*smoothstep(.42, 1.12, length(q));
        c += (h(floor(vUv*uRes) + fract(uTime*7.)*97.) - .5) * .032;
        gl_FragColor = vec4(c, 1.);
      }`,
  });
  composer.addPass(grade);
}
```

## The deckled frame
A full-screen canvas above the stage: cream `#efe6d3` everywhere except a hole whose edge is a jittered line every 5 px, 10 px in
(7 px under 760 px wide), cut with `destination-out`; an inner shadow drawn by stroking the edge off-screen with a shadow offset
back on, so only the shadow lands inside the mat; and faint fibres speckled over the mat. It is redrawn on resize.
```js
/* ================================================================ deckled frame */
const frame = document.getElementById('frame');
function drawFrame() {
  const d = Math.min(2, devicePixelRatio || 1), W = innerWidth, Hh = innerHeight; frame.width = W * d; frame.height = Hh * d;
  const x = frame.getContext('2d'); x.setTransform(d, 0, 0, d, 0, 0);
  const b = W < 760 ? 7 : 10;
  x.fillStyle = '#efe6d3'; x.fillRect(0, 0, W, Hh);
  const r = rnd(5), pts = [];
  const edge = (x0, y0, x1, y1) => { const L = Math.hypot(x1 - x0, y1 - y0), n = Math.ceil(L / 5); for (let i = 0; i < n; i++) { const t = i / n; const j = (r() - 0.5) * 2.6 + Math.sin(i * 0.37) * 0.8; pts.push([x0 + (x1 - x0) * t + (y1 === y0 ? 0 : j), y0 + (y1 - y0) * t + (x1 === x0 ? 0 : j)]); } };
  edge(b, b, W - b, b); edge(W - b, b, W - b, Hh - b); edge(W - b, Hh - b, b, Hh - b); edge(b, Hh - b, b, b);
  x.globalCompositeOperation = 'destination-out'; x.beginPath(); pts.forEach(([a, c], i) => i ? x.lineTo(a, c) : x.moveTo(a, c)); x.closePath(); x.fill();
  x.globalCompositeOperation = 'source-over';
  x.save(); x.beginPath(); pts.forEach(([a, c], i) => i ? x.lineTo(a, c) : x.moveTo(a, c)); x.closePath(); x.clip();
  x.shadowColor = 'rgba(30,15,0,.45)'; x.shadowBlur = 10; x.strokeStyle = 'rgba(0,0,0,1)'; x.lineWidth = 6; x.translate(-W * 3, 0); x.shadowOffsetX = W * 3;
  x.beginPath(); pts.forEach(([a, c], i) => i ? x.lineTo(a - 2, c - 2) : x.moveTo(a - 2, c - 2)); x.closePath(); x.stroke(); x.restore();
  // fibres on the mat
  x.save(); x.beginPath(); x.rect(0, 0, W, Hh); pts.forEach(([a, c], i) => i ? x.lineTo(a, c) : x.moveTo(a, c)); x.closePath(); x.clip('evenodd');
  for (let i = 0; i < (W + Hh) * 1.2; i++) { x.fillStyle = `rgba(90,70,40,${r() * 0.12})`; const side = r(); const px = side < 0.5 ? r() * W : (r() < 0.5 ? r() * b : W - r() * b), py = side < 0.5 ? (r() < 0.5 ? r() * b : Hh - r() * b) : r() * Hh; x.fillRect(px, py, 1 + r() * 2, 1); }
  x.restore();
}
```

## Interaction — the turn, picking, wiggles, the card, the colophon, tabs and zoom
`state.target` is in pages (1 = one bay) and is unbounded. 240 px of wheel delta is .15 of a page, so a typical 100 px notch is
about .06 (clamped to ±.5 per event, line and page delta modes scaled); a mouse drag is −dx / width × 1.7, a touch drag −dx /
width × 1.5 − dy / height × 1.2, with the velocity smoothed (.6 / .4) and carried as inertia on release; the arrow, Page and Space
keys step to the next whole page. Input waits for the book to open and pauses under a card or the colophon (Escape closes either);
the first turn past .3 of a page fades the hint. A press that moves under 7 px and lasts under .6 s is a click. Picking casts
against the whole book and returns the pivot of the FIRST mesh hit, so walls, signs and layers in front block the props behind
them. Hover kicks a prop's angle spring by ±7; a click adds an upward hop of 2.2 and a kick of 9, and opens its card 160 ms later.
The card's art (at most 300 × 200 px) is the prop's atlas rectangle as a CSS background positioned from its UVs. The colophon
places its four photo corners on the shrunk stage's rectangle 950 ms after it opens. A chapter tab turns the shortest way to that
bay.
```js
/* ================================================================ interaction */
const state = { rest: 0, snap: null, target: 0, cur: 0, vel: 0, last: 0, lastInput: -9, drag: null, intro: 0, introT: -1, open: false, hover: null, mx: 0, my: 0, px: 0, py: 0, moved: false, w: 0, card: false, colo: false };
const ray = new THREE.Raycaster(), ndc = new THREE.Vector2();
const tip = document.getElementById('tip');
function now() { return performance.now() / 1000; }
function input(d) { if (!state.open || state.card || state.colo) return; state.target += d; state.lastInput = now(); markTurned(); }
let turned = false; function markTurned() { if (!turned && Math.abs(state.target) > 0.3) { turned = true; html.classList.add('turned'); } }
addEventListener('wheel', e => { e.preventDefault(); const k = e.deltaMode === 1 ? 16 : e.deltaMode === 2 ? innerHeight : 1; const d = (Math.abs(e.deltaY) > Math.abs(e.deltaX) ? e.deltaY : e.deltaX) * k; input(Math.max(-0.5, Math.min(0.5, d / 240 * 0.15))); }, { passive: false });
canvas.addEventListener('pointerdown', e => { if (!state.open) return; state.drag = { x: e.clientX, y: e.clientY, x0: e.clientX, y0: e.clientY, t: now(), id: e.pointerId, type: e.pointerType }; state.vel = 0; canvas.setPointerCapture(e.pointerId); });
canvas.addEventListener('pointermove', e => {
  state.mx = e.clientX; state.my = e.clientY; state.moved = true;
  const d = state.drag; if (!d || d.id !== e.pointerId) return;
  const dx = e.clientX - d.x, dy = e.clientY - d.y; d.x = e.clientX; d.y = e.clientY;
  const k = d.type === 'touch' ? (-dx / innerWidth * 1.5 - dy / innerHeight * 1.2) : (-dx / innerWidth * 1.7);
  input(k); state.vel = state.vel * 0.6 + k * 0.4;
});
function endDrag(e) {
  const d = state.drag; if (!d) return; state.drag = null;
  const dist = Math.hypot(e.clientX - d.x0, e.clientY - d.y0);
  if (dist < 7 && now() - d.t < 0.6) { clickAt(e.clientX, e.clientY); state.vel = 0; }
}
canvas.addEventListener('pointerup', endDrag); canvas.addEventListener('pointercancel', endDrag);
canvas.addEventListener('pointerleave', () => { state.mx = -1; setHover(null); });
addEventListener('keydown', e => {
  if (e.key === 'Escape') { closeCard(); closeColo(); return; }
  if (!state.open || state.card || state.colo) return;
  if (['ArrowRight', 'ArrowDown', 'PageDown', ' '].includes(e.key)) { e.preventDefault(); state.target = Math.round(state.target) + 1; state.lastInput = now(); markTurned(); }
  if (['ArrowLeft', 'ArrowUp', 'PageUp'].includes(e.key)) { e.preventDefault(); state.target = Math.round(state.target) - 1; state.lastInput = now(); markTurned(); }
});
function pick(x, y) {
  ndc.set(x / innerWidth * 2 - 1, -(y / innerHeight) * 2 + 1);
  ray.setFromCamera(ndc, camera);
  const hits = ray.intersectObject(book, true);
  for (const h of hits) { if (!h.object.isMesh) continue; return h.object.userData.pivot || null; }
  return null;
}
function setHover(p) {
  if (p === state.hover) return;
  state.hover = p;
  canvas.style.cursor = p ? 'pointer' : (state.drag ? 'grabbing' : 'grab');
  if (p) { kick(p, 7); tip.innerHTML = p.userData.label + (p.userData.card ? '<i>open ↗</i>' : ''); tip.classList.add('on'); }
  else tip.classList.remove('on');
}
function kick(p, v) { const s = p.userData.s; s.v += v * (Math.random() < 0.5 ? -1 : 1); if (!springs.includes(p)) springs.push(p); }
function hop(p) { const s = p.userData.s; s.vy += 2.2; kick(p, 9); }
function clickAt(x, y) {
  const p = pick(x, y);
  if (!p) return;
  hop(p);
  if (p.userData.card) setTimeout(() => openCard(p), 160);
}
const cardEl = document.getElementById('card');
function openCard(p) {
  const [t, body] = p.userData.card, c = CH[p.userData.bay];
  document.getElementById('cardh').textContent = t;
  document.getElementById('cardp').innerHTML = body.replace(/\*([^*]+)\*/g, '<em>$1</em>');
  document.getElementById('cards').textContent = 'chapter ' + c.num + ' · ' + c.n;
  const meta = META[p.userData.ch][p.userData.name], [u0, v0, u1, v1] = meta.uv, du = u1 - u0, dv = v1 - v0;
  const art = cardEl.querySelector('.art'); const maxW = Math.min(300, innerWidth * 0.62), maxH = 200;
  let w = maxW, h = w / meta.aspect; if (h > maxH) { h = maxH; w = h * meta.aspect; }
  Object.assign(art.style, { width: w + 'px', height: h + 'px', backgroundImage: `url(${PROPS}${p.userData.ch}.webp)`, backgroundSize: `${100 / du}% ${100 / dv}%`, backgroundPosition: `${u0 / (1 - du) * 100}% ${(1 - v1) / (1 - dv) * 100}%` });
  cardEl.querySelector('.half.top').style.setProperty('--cc', c.wall);
  cardEl.classList.add('on'); cardEl.setAttribute('aria-hidden', 'false'); state.card = true;
  setHover(null);
  setTimeout(() => cardEl.querySelector('.x').focus({ preventScroll: true }), 50);
}
function closeCard() { if (!state.card) return; cardEl.classList.remove('on'); cardEl.setAttribute('aria-hidden', 'true'); state.card = false; canvas.focus({ preventScroll: true }); }
cardEl.querySelector('.x').addEventListener('click', closeCard); cardEl.querySelector('.scrim').addEventListener('click', closeCard);
// colophon
const coloEl = document.getElementById('colophon');
function openColo() { html.classList.add('colo'); state.colo = true; setHover(null); placeCorners(); coloEl.setAttribute('aria-hidden', 'false'); document.getElementById('colox').focus({ preventScroll: true }); }
function closeColo() { if (!state.colo) return; html.classList.remove('colo'); state.colo = false; coloEl.setAttribute('aria-hidden', 'true'); document.getElementById('colo').focus({ preventScroll: true }); }
document.getElementById('colo').addEventListener('click', openColo);
document.getElementById('colox').addEventListener('click', closeColo);
document.getElementById('cocred').addEventListener('click', () => { if (!state.open) { state.wantColo = true; window.__fwOpen(); } });
function placeCorners() {
  requestAnimationFrame(() => setTimeout(() => {
    const r = document.getElementById('stage').getBoundingClientRect();
    const cs = [['pc1', r.left - 6, r.top - 6, 0], ['pc2', r.right - 54, r.top - 6, 90], ['pc3', r.right - 54, r.bottom - 54, 180], ['pc4', r.left - 6, r.bottom - 54, 270]];
    for (const [id, x, y, rot] of cs) Object.assign(document.getElementById(id).style, { left: x + 'px', top: y + 'px', clipPath: 'polygon(0 0,100% 0,0 100%)', transform: `rotate(${rot}deg)`, width: '60px', height: '60px' });
  }, 950));
}
// chapter tabs
const tabs = document.getElementById('tabs'), chapname = document.getElementById('chapname');
const NUMS = ['I', 'II', 'III', 'IV', 'V', 'VI'];
CH.forEach((c, i) => { const bt = document.createElement('button'); bt.textContent = NUMS[i]; bt.style.background = c.wall; bt.setAttribute('aria-label', 'Chapter ' + c.num + ': ' + c.n); bt.onclick = () => goTo(i); tabs.appendChild(bt); });
function goTo(i) { const cur = state.target, base = Math.round(cur); let best = base, bd = 99; for (let k = base - 6; k <= base + 6; k++) if ((((k % 6) + 6) % 6) === i && Math.abs(k - cur) < bd) { bd = Math.abs(k - cur); best = k; } state.target = best; state.lastInput = now(); markTurned(); }
let shownChap = -1;
function updateChrome() {
  const i = ((Math.round(state.cur) % 6) + 6) % 6;
  if (i === shownChap) return; shownChap = i;
  [...tabs.children].forEach((b, j) => b.classList.toggle('on', j === i));
  chapname.innerHTML = `<small>chapter ${CH[i].num}</small>${CH[i].n}`;
}
// zoom
const lv = [...document.querySelectorAll('#zoom .lv i')];
function setZoom(i) { zoomI = Math.max(0, Math.min(2, i)); lv.forEach((e, j) => e.classList.toggle('on', j === zoomI)); }
document.getElementById('zin').onclick = () => setZoom(zoomI + 1);
document.getElementById('zout').onclick = () => setZoom(zoomI - 1);
```

## The die-cut window and resize
The pre-opening camera has to land the book inside the cover's window, so the module reads the window from the page rather than
repeating the CSS numbers: the left board's ring element gives the radius (its width minus the 28 px of ring, halved) and the
centre as a fraction of the height. It is measured at start and on every resize until the boards swing, so the short-screen rules
that move the window stay in step with the camera.
```js
/* ================================================================ resize */
/* the cover's die-cut window, measured from the page so short viewports that move it stay in step */
const win = { wr: innerWidth < 760 ? 92 : 118, wy: innerWidth < 760 ? 0.27 : 0.31 };
function measureWin() {
  if (html.classList.contains('swing')) return;
  const r = document.querySelector('.board.l .ring').getBoundingClientRect();
  if (r.width) { win.wr = (r.width - 28) / 2; win.wy = (r.top + r.height / 2) / innerHeight; }
}
measureWin();
function resize() {
  measureWin();
  const w = innerWidth, h = innerHeight;
  renderer.setSize(w, h, false); camera.aspect = w / h; camera.updateProjectionMatrix();
  if (composer) { composer.setSize(w, h); grade.uniforms.uRes.value.set(w, h); }
  if (gtao) gtao.setSize(w * DPR, h * DPR);
  drawFrame();
}
addEventListener('resize', resize);
```

## Opening — the cover timeline
One function, called by "Untie & open", the bow, or `colophon & credits` before the book is open (which then opens the colophon as
the cover clears). The class timeline and its CSS: `opening` at 0 ms (the bow flies up 30 px, turns −30° and shrinks to .6 over
.55 s on a back-in curve and fades; the ribbon halves slide ±105% over .7 s; the tag, the foot and the triangles fade out over .3
s); `swing` at 420 ms (the boards turn ±100° about their outer edges over 1.5 s on `cubic-bezier(.66,0,.22,1)` while their shades
rise to .55); the camera's intro clock starts at 350 ms; `open` at 1900 ms (the cover is removed, the chrome fades in over .8 s
after .2 s, input is enabled and the canvas takes focus).
```js
/* ================================================================ open */
window.__fwOpen = function () {
  if (html.classList.contains('opening')) return;
  html.classList.add('opening');
  setTimeout(() => html.classList.add('swing'), 420);
  state.introT = now() + 0.35;
  setTimeout(() => { html.classList.add('open'); state.open = true; canvas.focus({ preventScroll: true }); if (state.wantColo) openColo(); }, 1900);
};
```

## The loop
One rAF loop, `dt` capped at 50 ms. **The turn**: inertia (velocity × .9 a frame) while it lasts; after .9 s with no input and
almost no velocity, the snap chooses a page once (a nudge under .035 returns to the page it left, anything more turns at least one
page that way, rounding larger moves) and eases the target there at 3.2/s; `cur` follows `target` at 4.6/s. **The intro**: `ie` is
a cubic in-out of the 2.4 s intro clock (0 before opening). Before opening the book idles at an offset of `.55 + .32 sin(.32 t)`
pages and blends to `cur` as `ie` rises. **The window camera**: the camera stands 22 units from the look point, 18° up; its lens
is chosen so that 7.6 units (the book's width) span 1.75 window radii, and `setViewOffset` shifts the image so the book's centre
sits at the window's centre; position, lens and the fog (pushed 15 units further out) all blend to the open view with `ie`, which
is the dolly-zoom. **The open camera**: the zoom eases at 5/s, the look point drops .35 × (1 − zoom), the cursor leans the camera
.35 across and .18 down (not on phones, eased at 3/s), and on screens narrower than 1.6 : 1 the lens widens to keep the book's
width (to at most 62°; phone portrait keeps 47°). **Hangers**: a pendulum per hanging thing (stiffness 26, damping 2.2) driven by
the book's angular acceleration × .012 × its radius over its length, clamped to ±.6 rad, plus small idle sines. **Wiggles**: an
angle spring (160, 9) shown as `rotation.z × .09` with a slight stretch, and a hop spring (120, 10) that lifts the art and
squashes it on landing; a spring leaves the list once all four values are under .001. Swayers sway on sines and Odile breathes .6%
in height; hover is re-picked only when something moved, never on phones.
```js
/* ================================================================ loop */
const look = new THREE.Vector3(), tmp = new THREE.Vector3();
let lastT = now(), prevCur = 0, angVel = 0;
function frameLoop() {
  const t = now(), dt = Math.min(0.05, t - lastT); lastT = t;
  tickPct();
  // turning
  if (!state.drag && Math.abs(state.vel) > 1e-4) { state.target += state.vel; state.vel *= 0.9; }
  // after a pause, settle on a page: a nudge of more than a few percent turns to the next one in that direction
  if (!state.drag && t - state.lastInput > 0.9 && Math.abs(state.vel) < 0.002) {
    if (state.snap == null) { const dl = state.target - state.rest; state.snap = Math.abs(dl) < 0.035 ? state.rest : state.rest + Math.sign(dl) * Math.max(1, Math.round(Math.abs(dl))); state.rest = state.snap; }
    state.target += (state.snap - state.target) * (1 - Math.exp(-dt * 3.2));
  } else state.snap = null;
  state.cur += (state.target - state.cur) * (1 - Math.exp(-dt * 4.6));
  // intro: the book swings round to chapter one while the camera settles
  let ip = 1;
  if (state.introT > 0) ip = Math.min(1, Math.max(0, (t - state.introT) / 2.4));
  else if (!state.open) ip = 0;
  const ie = ip < 0.5 ? 4 * ip * ip * ip : 1 - Math.pow(-2 * ip + 2, 3) / 2;
  const sway = 0.55 + 0.32 * Math.sin(t * 0.32);
  book.rotation.y = -(state.cur - sway * (1 - ie)) * 60 * D2R;
  const w = (state.cur - prevCur) / Math.max(dt, 1e-3); const acc = (w - angVel) / Math.max(dt, 1e-3); angVel = w; prevCur = state.cur;
  // camera
  zoomF += (ZOOMS[zoomI] - zoomF) * (1 - Math.exp(-dt * 5));
  const par = state.mx >= 0 && !PHONE ? [(state.mx / innerWidth - 0.5), (state.my / innerHeight - 0.5)] : [0, 0];
  state.px += (par[0] - state.px) * (1 - Math.exp(-dt * 3)); state.py += (par[1] - state.py) * (1 - Math.exp(-dt * 3));
  // before opening, the camera stands far back and the view is offset so the whole book turns inside the cover's window
  const W = innerWidth, Hh = innerHeight, { wr, wy } = win;
  const vw = 7.6 * W / (1.75 * wr), vh = vw / (W / Hh), dPre = 22;
  const fovPre = 2 * Math.atan(vh / (2 * dPre)) / D2R;
  look.copy(CAM.look); look.y -= (1 - zoomF) * 0.35 * ie;
  tmp.set(0, Math.sin(18 * D2R), Math.cos(18 * D2R)).multiplyScalar(dPre).add(CAM.look);
  camera.position.lerpVectors(tmp, CAM.pos, ie);
  camera.position.x += state.px * 0.35 * ie; camera.position.y -= state.py * 0.18 * ie;
  const baseFov = PHONE && PORTRAIT ? CAM.fov : Math.min(62, 2 * Math.atan(Math.tan(CAM.fov * D2R / 2) * Math.max(1, 1.6 / (W / Hh))) / D2R);
  camera.fov = THREE.MathUtils.lerp(fovPre, baseFov * zoomF, ie);
  if (ie < 1) camera.setViewOffset(W, Hh, 0, (0.5 - wy) * Hh * (1 - ie), W, Hh); else if (camera.view) camera.clearViewOffset();
  camera.updateProjectionMatrix();
  camera.lookAt(look);
  scene.fog.near = 13 + (1 - ie) * 15; scene.fog.far = 30 + (1 - ie) * 15;
  // hanging things swing with the turn
  for (const h of hangers) {
    h.v += (-26 * h.a - 2.2 * h.v + acc * 0.012 * h.r / h.len) * dt; h.a += h.v * dt;
    h.vb += (-20 * h.b - 2.0 * h.vb - w * 0.0) * dt; h.b += h.vb * dt;
    h.piv.rotation.x = Math.max(-0.6, Math.min(0.6, h.a)) + Math.sin(t * 0.9 + h.ph) * 0.02;
    h.piv.rotation.z = Math.sin(t * 0.7 + h.ph * 1.3) * 0.025;
  }
  // wiggles
  for (let i = springs.length - 1; i >= 0; i--) {
    const p = springs[i], s = p.userData.s;
    s.v += (-160 * s.a - 9 * s.v) * dt; s.a += s.v * dt;
    s.vy += (-120 * s.y - 10 * s.vy) * dt; s.y += s.vy * dt;
    p.rotation.z = s.a * 0.09 + (p.userData.sa ? Math.sin(t * 1.1 + p.userData.sw) * p.userData.sa : 0); p.children[0].scale.y = p.userData.h * (1 + s.a * 0.015 - Math.max(0, -s.y) * 0.4);
    p.children[0].position.y = Math.max(0, s.y) * 0.18;
    if (Math.abs(s.a) + Math.abs(s.v) + Math.abs(s.y) + Math.abs(s.vy) < 1e-3) { s.a = s.v = s.y = s.vy = 0; p.rotation.z = 0; p.children[0].scale.y = p.userData.h; p.children[0].position.y = 0; springs.splice(i, 1); }
  }
  for (const p of swayers) if (!springs.includes(p)) { p.rotation.z = Math.sin(t * 1.1 + p.userData.sw) * p.userData.sa; if (p.userData.name.startsWith('odile')) p.children[0].scale.y = p.userData.h * (1 + Math.sin(t * 2.1 + p.userData.sw) * 0.006); }
  for (const f of anims) f(t, dt);
  // hover
  if (Math.abs(state.target - state.cur) > 0.002 || springs.length) state.moved = true;
  if (state.open && !PHONE && state.moved && !state.drag && !state.card && !state.colo) { state.moved = false; setHover(state.mx >= 0 ? pick(state.mx, state.my) : null); }
  if (state.hover) { tip.style.left = state.mx + 'px'; tip.style.top = state.my + 'px'; }
  updateChrome();
  grade.uniforms.uTime.value = t;
  composer.render(dt);
  requestAnimationFrame(frameLoop);
}
```

## Boot
The count starts ticking at once. The module waits for `props.json`, then for the fonts and the textures (each capped by
`PATIENCE`) and for the rag paper image, then builds the backdrop, the table, the dust, the book and the composer, compiles every
material and renders one frame before reaching 100, so nothing compiles during the opening. 650 ms later it sets `__ready` and
`ready` (the tag appears). If the watchdog took over while the files were slow, it stops there without starting a hidden render
loop; any build error hands over to the still. `window.__fw` exposes test hooks (set a page, open, zoom, open a card by prop name,
open or close the colophon).
```js
/* ================================================================ boot */
(function pctLoop() { tickPct(); if (!window.__ready) requestAnimationFrame(pctLoop); })();
(async () => {
  try {
    drawFrame();
    META = await metaP;
    await patient(fontsP);
    await patient(loadedP);
    if (!ragImg.complete) await new Promise(r => { ragImg.onload = ragImg.onerror = r; });
    setPct(88);
    buildBackdrop();
    buildTable();
    buildDust();
    buildBook();
    buildPost();
    setPct(94);
    renderer.compile(scene, camera);
    composer.render(0);
    setPct(100);
    window.__fw = { state, setP: p => { state.target = state.cur = p; state.rest = Math.round(p); state.snap = null; }, camera, CH, open: () => window.__fwOpen(), zoom: setZoom, card: n => { const m = interactive.find(m => m.userData.pivot.userData.name === n); if (m) openCard(m.userData.pivot); }, colo: openColo, closeColo, closeCard };
    setTimeout(() => { window.__ready = window.__booted = true; html.classList.add('ready'); }, 650);
    if (html.classList.contains('nogl')) return; // the still took over while assets were slow: no hidden render loop
    requestAnimationFrame(frameLoop);
  } catch (e) { console.error(e); window.__fwFail && window.__fwFail('build: ' + e.message); }
})();
```

## Copy
Every static string is in the markup above; set them exactly, including the title `Foldworld · the carousel book of Odile
Penhallow`, the meta description and the canvas label. The dynamic strings live in the module: the chapter names and the six signs
in `CH`, the 19 card stories in `CARDS` (17 reachable), the hover names in `LABELS` with the card cue `open ↗`, the count `FOLDING
000`–`FOLDING 100` (or `READY` on the fallback), the chapter line `chapter one` … `chapter six` above the chapter name, the card
kicker `chapter four · Market Street` (uppercase by CSS), the tab labels I–VI with `Chapter one: The Workbench` and so on as their
accessible names, and the base band lettering. Odile Penhallow, Mouse the cat, Professor the owl, Studio 3, Rope Walk Yard,
Foldworld and `hello@foldworld.studio` are fictional; the colophon says so.

## Phone (390px) and tablet
- **The scene** (`PHONE`: a coarse pointer or a short side under 560 px; `PORTRAIT`: width ÷ height under .9): in phone portrait
  the camera comes closer and lower with a 47° lens and zoom steps of 1, .86 and .74; every sign is 1.5 wide and hangs in the
  middle of its thread, and the things that shared the middle move aside (the gulls to −.95 and 1.0, the night lantern to .95,
  the hanging dove to .9). Phones drop GTAO, use a 1024 shadow map, cap DPR at 1.6, light the lantern at 1.4 instead of 2.2, and
  draw 26 fireflies and 40 dust motes. There is no hover and no cursor lean: a tap is a click (it hops the prop and opens its
  card), and a touch drag turns the book with either axis.
- **≤ 760 px wide** (the phone CSS): the wordmark goes to 19 px; the colophon tag sits 16 px in; the tabs (26 px wide) stack
  above the chapter name at bottom left; the zoom pill keeps − and + and hides its dots; the hint moves to the top, 76 px down,
  at 15 px. The cover window is 92 px in radius at 27% of the height, the label 204 px tall, and the ribbon, bow (at .85) and
  tag move up to match. The frame's mat is 7 px. In the colophon the stage shrinks to .46, tipped −2°, toward the top
  (`translate(0, 60px − 27vh)`), and the text sits across the bottom with a 30 px heading and 15.5 px paragraphs.
- **Short screens**: phones under 760 px tall move the window up to `min(27%, 100% − 411px − --wr)` and shrink the colophon
  stage to .4; wider screens under 900 px tall use the rule in the stylesheet notes above; both hide the cover's hint line and
  keep only `colophon & credits`.
- **761–1199 px** (tablets and small laptops): the hint sits 88 px off the bottom so it clears the chapter name and the zoom
  pill.

## Failure, and the motion floor
- **No WebGL**: the watchdog's context test fails at once, so `nogl` and `ready` go on `<html>` before the module even loads.
  The canvas, tabs, zoom and hint hide and the designed still of chapter one fills the stage (`center/cover`) with a cream
  caption card 118 px off the bottom: `This book turns with WebGL. Here's a photo of the first chapter.` The cover shows `READY`
  at once with the bow and the tag; "Untie & open" plays the same CSS opening; the colophon opens and closes (the still shrinks
  onto the page, without the photo corners) and Escape closes it. The module, if it loads, stops right after its imports.
- **three.js fails to download** (or an addon): the inline module's `onerror` calls `__fwFail('module failed to load')`; and if
  the module never runs at all, the watchdog's 10 s timer lifts the cover onto the still with `module did not boot`. A renderer
  that cannot be created calls `__fwFail('renderer')`; any error while building calls it with the message.
- **The loader failsafe**: the fonts and the textures are each waited on for at most 5 s (`PATIENCE`), so a stalled file never
  blocks the build; if the whole boot has not set `__ready` within 10 s, the watchdog shows the still (`assets slow`) and the
  module, when it finishes, does not start its render loop behind it. A `props.json` that fails to parse lands in the build's
  catch and shows the still.
- **Reduced motion** is CSS only: every transition is cut to .01 s and the keyframe swings (the colophon tag, the bow, the tag)
  are off, so the cover, the card and the colophon switch almost instantly. The scene itself does not change: the 2.4 s camera
  flight, the turning inertia, the sea, the boat, the tram, the planes, the fireflies, the dust and the swaying still play.
- **No JavaScript**: nothing can lift the cover, so the page stays on the closed book.

## Assets (hosted, public, CORS-open — load them by these URLs)
Fifteen files. The textures, the atlases and `props.json` are fetched cross-origin by the module (three's `TextureLoader` with
`crossOrigin = 'anonymous'`, a `fetch`, and the rag paper as an `Image` with `crossOrigin = 'anonymous'` because it is drawn into
canvases that become textures); the CSS backgrounds (the still, the cloth, the rag paper on the cover, card and colophon, and the
card's atlas art) need no CORS.
- `https://www.vividsites.app/media/flagship/foldworld/main.js` — 71.6 KB, 984 lines: a hosted copy of the module quoted above,
  for checking against only. Do not load it; the module is inlined.
- `https://www.vividsites.app/media/flagship/foldworld/props/props.json` — 226 KB JSON: the traced outlines of 120 cut-outs in
  six chapter keys (`work` 30 with Odile's twelve poses, and 18 each in `tide`, `night`, `market`, `glass` and `post`), each `{
  uv: [u0, v0, u1, v1], aspect, shapes: [{ o: [[x, y], …], h: [[[x, y], …], …] }] }` with coordinates 0–1 across and 0–1 up.
- The six prop atlases, each 2048 × 2048 WebP with alpha (about 600–750 KB), illustrated paper-craft cut-outs packed on
  transparent with colour bled past the edges, loaded as `PROPS + c.id + '.webp'` (and shown in the card as a CSS background
  from the same base):
  `https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/flagship/foldworld/props/work.webp` (Odile, a girl
with a brown bob, round glasses, a mustard cardigan and teal trousers, in twelve poses: with a lantern, cutting paper, waving,
posting a letter, kneeling with a watering can, rowing; and the arm lamps, the ginger cat, cacti, pencil pots, paper cranes,
scissors, book stacks, pink thread spools and floral teacups),
  `https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/flagship/foldworld/props/tide.webp` (lighthouses,
sailboats, beach huts, buoys, whales, gulls, starfish, crabs, rowing boats),
  `https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/flagship/foldworld/props/night.webp` (lanterns, apple
trees, poplars, rabbits, owls, toadstools, moons, foxes, hedgehogs),
  `https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/flagship/foldworld/props/market.webp` (townhouses,
bakeries, trams, street lamps, flower carts, bicycles, dogs, fruit stalls, pigeons),
  `https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/flagship/foldworld/props/glass.webp` (ferns,
monsteras, tall cacti, sunflowers, watering cans, toadstools, butterflies, wheelbarrows, snails),
  `https://zxdefgavgwfxastwmmjm.supabase.co/storage/v1/object/public/assets/flagship/foldworld/props/post.webp` (potted plants,
letter boxes, letter desks with a typewriter, doves, satchels, letters, parcels, paper planes, envelopes).
- `https://www.vividsites.app/media/flagship/foldworld/still.jpg` — 1600 × 1000 JPEG (376 KB): the designed still of chapter
  one, The Workbench, its sign `Hello, I'm Odile!`, Odile, Mouse, the desk and lamp, the pegboard and bunting, framed as the
  open camera sees it. The `#still` background under `nogl`.
- `https://www.vividsites.app/media/flagship/foldworld/tex/cloth.jpg` — 1024 × 1024 tileable teal bookcloth macro (419 KB). The
  cover boards' background at 420 px (the right board offset −210 px so the weave continues across the seam).
- `https://www.vividsites.app/media/flagship/foldworld/tex/rag.jpg` — 1024 × 1024 tileable cream rag-paper macro (317 KB). The
  cover's corners (300 px), ring (300 px) and label (360 px), the card halves (360 px), the colophon page (420 px), and the sign
  canvases' pattern.
- `https://www.vividsites.app/media/flagship/foldworld/tex/paper_detail.jpg` — 1024 × 1024 tileable pale grey cardstock macro
  (418 KB). The `map` on every built paper material, loaded with no colour space.
- `https://www.vividsites.app/media/flagship/foldworld/tex/paper_normal.jpg` — 1024 × 1024 tangent-space normal map of the
  cardstock (615 KB). The paper materials' normal map; a clone tiled 9× is the props' normal map.
- `https://www.vividsites.app/media/flagship/foldworld/tex/rag_normal.jpg` — 1024 × 1024 normal map of the rag paper (541 KB).
  The signs' face, the spine, the base band and the thread on the giant spool.
- `https://www.vividsites.app/media/flagship/foldworld/tex/wood.jpg` — 2048 × 2048 tileable pale birch table top (671 KB),
  repeated 5× on the table disc.

Everything else (every wall, layer and cut-out shape, the canvas floors, signs and band, the table tools, the dome, the particles,
the grade, the frame and the whole cover) is written in the file. The only other requests are Pixelify Sans and Gaegu from Google
Fonts and three.js with its addons from jsDelivr.

## Verify
- The cover: two teal cloth boards with cream corners, the round window showing the 3D book turning slowly on its table, the
  split cream label reading `a carousel book in six chapters` / `Fold·world` / `by Odile Penhallow, paper engineer`, and
  `FOLDING 000` counting up while six coloured triangles stand up in the window; at 100 the triangles fade and the `Untie &
  open` tag appears under the bow.
- "Untie & open" (or the bow): the bow flies off, the ribbon halves slide away, the boards swing open like doors, and the camera
  flies from the window view down into The Workbench as the book swings round; the chrome fades in after about 1.9 s; the hint
  shows until the first turn.
- A single wheel notch (about .06 of a page), a short drag or a swipe nudges the book and, once it rests, it settles one whole
  page on in that direction; arrows, Page keys and Space step whole pages; it loops past VI back to I; the tabs, the chapter
  name and the active tab follow; hanging gulls, signs, flags and the lantern swing as it turns and settle.
- Hovering a prop wiggles it and shows its name tag; a prop hidden behind a wall or sign is never picked; clicking Odile in The
  Workbench hops her and unfolds the card `Odile Penhallow` with the art from the atlas and `CHAPTER ONE · THE WORKBENCH`; ✕,
  the scrim and Escape close it.
- Each chapter is alive: the sea rocks, the boat bobs and the whale rises; the night bay's lantern flickers and lights the fox
  and trees, with fireflies; the tram rolls; the butterflies flap; two paper planes loop round chapter six; dust floats
  everywhere.
- Zoom + and − step through three levels with the pink dot following; the Colophon tag shrinks the live scene onto the rag page
  as a tilted mounted photograph with black corners and fades in the text; Escape or `Close the colophon` returns.
- At 1440 × 720 and 1280 × 800 the window rides up and the bow, ribbon and tag clear the foot, which shows only `colophon &
  credits`; the book inside the window stays centred in the hole.
- At 390 × 844: the cover fits with the smaller window, the book opens to a centred sign, a swipe turns pages, a tap opens a
  card, the colophon stacks the photo above the text, no horizontal overflow, no console errors.
- The textures, atlases and `props.json` load cross-origin with no tainted-canvas or CORS errors, and the signs show the
  rag-paper fibre.
- With WebGL disabled the cover reads `READY` at once, opens onto the still of chapter one with its caption, and the colophon
  still works; with three.js blocked the cover falls back the same way.
