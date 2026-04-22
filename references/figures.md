# scenepad figure primitives

All figures: stroke only, never filled. Stroke 2px, color #1a1a1a.
Position figures by CENTER X (cx) and HEAD TOP Y (ty).
Head radius = 16px. Total figure height ~130px.

## Base figure

cx = center x, ty = top y of head circle

  head:       circle cx cy=ty+16 r=16
  body:       line (cx, ty+32) to (cx, ty+82)
  left arm:   line (cx, ty+46) to (cx-22, ty+66)
  right arm:  line (cx, ty+46) to (cx+22, ty+66)
  left leg:   line (cx, ty+82) to (cx-16, ty+115)
  right leg:  line (cx, ty+82) to (cx+16, ty+115)

## Face expressions

neutral:
  eyes: circles at (cx-6, ty+13) and (cx+6, ty+13) r=2 filled
  mouth: horizontal line (cx-5, ty+22) to (cx+5, ty+22)

happy:
  eyes: same as neutral
  mouth: arc up Q cx ty+27

worried:
  eyes: same as neutral
  mouth: arc down Q cx ty+20

surprised:
  eyes: circles r=2.5
  mouth: small ellipse rx=4 ry=5

determined:
  eyes: same as neutral
  mouth: bold line (cx-8, ty+21) to (cx+8, ty+21) stroke-width=2

## Pose variants

pointing (raise right arm):
  right arm: line (cx, ty+46) to (cx+30, ty+30)

explaining / shrugging (both arms out):
  left arm:  line (cx, ty+46) to (cx-30, ty+40)
  right arm: line (cx, ty+46) to (cx+30, ty+40)

typing / at laptop:
  left arm:  line (cx, ty+46) to (cx-18, ty+62)
  right arm: line (cx, ty+46) to (cx+18, ty+62)
  laptop:    rect x=cx-22 y=ty+62 w=44 h=28 rx=3
  base:      line (cx-26, ty+90) to (cx+26, ty+90)

on phone (right arm up to ear):
  left arm:  line (cx, ty+46) to (cx-22, ty+66)
  right arm: line (cx, ty+46) to (cx+16, ty+30)
  phone:     rect x=cx+14 y=ty+18 w=10 h=18 rx=2

## Accessories (role identifiers)

headset (support agent):
  arc over head from (cx-16, ty+14) through top to (cx+16, ty+14)
  ear pads: two small rects each side

hard hat (engineer / ops):
  filled path across top of head, flat brim line

crown (executive / decision maker):
  zigzag path above head, stroke only

## Positioning guide

| Actors | cx values (% of panel width W) |
|--------|--------------------------------|
| 1      | 0.50 W                         |
| 2      | 0.28 W, 0.72 W                 |
| 3      | 0.18 W, 0.50 W, 0.82 W         |
| 4      | 0.14 W, 0.38 W, 0.62 W, 0.86 W|

Always place figures at ty=50 from panel top to leave room for bubble above.
