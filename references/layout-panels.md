# scenepad panel layout

Use for: people talking, narrative scenes, team interactions, user flows.

## Single panel (680 x 280)

One scene, one moment. Use when the story has one key interaction.

  viewBox: 0 0 680 280
  panel rect: x=20 y=20 width=640 height=240 rx=6
  panel number: x=340 y=40 text-anchor=middle 10px monospace muted
  figures: centered inside panel, ty=60
  caption: x=340 y=268 text-anchor=middle 13px medium ink

## Two panels (680 x 280, split horizontal)

Two moments side by side. Most common layout.

  viewBox: 0 0 680 280
  panel 1: x=20  y=20 width=314 height=240 rx=6
  panel 2: x=346 y=20 width=314 height=240 rx=6
  gap: 12px between panels
  figures inside each panel: use panel-local coordinates
  caption: x=340 y=268 text-anchor=middle 13px medium ink

## Three panels (680 x 280, split horizontal)

Three moments. Classic comic strip.

  viewBox: 0 0 680 280
  panel 1: x=20  y=20 width=198 height=240 rx=6
  panel 2: x=230 y=20 width=198 height=240 rx=6
  panel 3: x=440 y=20 width=220 height=240 rx=6
  gap: 12px between panels

## Four panels (680 x 560, 2x2 grid)

Two rows of two. For longer stories.

  viewBox: 0 0 680 560
  panel 1: x=20  y=20  width=314 height=240 rx=6
  panel 2: x=346 y=20  width=314 height=240 rx=6
  panel 3: x=20  y=292 width=314 height=240 rx=6
  panel 4: x=346 y=292 width=314 height=240 rx=6
  caption: x=340 y=548 text-anchor=middle 13px medium ink

## Panel number placement

Always top-center inside panel, 8px from panel top.
Format: zero-padded two digits: 01, 02, 03
Style: 10px monospace fill=muted letter-spacing=1

## Arrows between panels

When story flows left to right, add a small arrow between panels:
  line from right edge of panel N to left edge of panel N+1
  y = panel vertical center
  stroke=#1a1a1a stroke-width=1 marker-end arrow
  keep short: 8px line max, just a visual nudge

## Actor labels

Centered below each figure, 8px below feet.
10px sans-serif fill=muted.
Keep short: one word or a short role name.
  Customer, Support, Engineer, PM, CEO, Service A, Auth API
