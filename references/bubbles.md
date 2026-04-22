# scenepad speech bubble primitives

## Rules

- Bubbles sit ABOVE the speaker's head by default
- Bubble width: min 80px, max 160px, sized to content
- Text: 11px, line-height 1.4, max 2 lines per bubble
- Tail points DOWN toward the speaker's head
- One bubble per actor per panel, no stacking

## Speech bubble (standard, white fill)

Speaker at cx. Bubble bottom at: figure ty - 10px.
Width W sized to text. Height H = 36px (1 line) or 52px (2 lines).

  rect: x=cx-W/2, y=bubble_bottom-H, width=W, height=H, rx=8
        fill=#ffffff stroke=#1a1a1a stroke-width=1.5
  tail: small triangle below bubble center pointing down to head
        triangle tip = cy of head top - 4px
  text: centered inside rect, 11px, fill=#1a1a1a

## Thought bubble (surface fill, dotted tail)

Same as speech bubble but:
  fill: #f5f5f5
  tail: three decreasing circles instead of triangle
        circles: r=4 r=3 r=2 descending toward head

## Shout bubble (jagged edges, peak moment)

Use sparingly, once per scene maximum.
  shape: polygon with 12-16 jagged points radiating from center
  fill: #ffffff stroke: #1a1a1a stroke-width=2

## Inverted bubble (black fill, white text, peak moment)

Use at most once per scene for the most important line.
  rect: fill=#1a1a1a stroke=none rx=8
  text: fill=#ffffff
  tail: filled triangle, fill=#1a1a1a

## Bubble with label (system/service actors)

For non-human actors (APIs, services, databases):
  replace rounded rect with a rect rx=4 (squarer)
  add a small monospace label inside top: 9px muted
  example: "POST /auth" or "500 error" or "retry"

## Tail geometry

Standard tail for bubble centered at bx, bottom at by, pointing to head at (cx, hy):
  triangle points:
    (bx - 7, by)    left base
    (bx + 7, by)    right base
    (cx, hy - 4)    tip near head
  fill=white, stroke=#1a1a1a stroke-width=1.5
  overdraw base with white line to hide bubble bottom stroke
