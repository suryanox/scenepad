# scenepad figure primitives

All figures: stroke only, never filled. Stroke 2px, ink #1a1a1a.
Position by head CENTER X (cx) and head CENTER Y (cy).
Head radius = 17px. Chin y = cy + 17. Feet y = cy + 112.

## Base figure (cx, cy)

  head:       circle cx=cx cy=cy r=17 fill=none stroke=#1a1a1a stroke-width=2
  body:       line (cx, cy+17) → (cx, cy+65)
  left arm:   line (cx, cy+32) → (cx-28, cy+52)
  right arm:  line (cx, cy+32) → (cx+28, cy+52)
  left leg:   line (cx, cy+65) → (cx-18, cy+95)
  right leg:  line (cx, cy+65) → (cx+18, cy+95)

Actor label: text cx, cy+112  text-anchor=middle font-size=10 fill=#aaaaaa

## Expressions

All eye positions: left=(cx-6, cy-4) right=(cx+6, cy-4) r=2.2 fill=#1a1a1a

neutral:
  mouth: line (cx-6, cy+8) → (cx+6, cy+8) stroke-width=1.8

happy:
  mouth: path M cx-7 cy+7 Q cx cy+14 cx+7 cy+7
         fill=none stroke=#1a1a1a stroke-width=1.8 stroke-linecap=round

worried:
  brows:  path M cx-9 cy-9 Q cx-6 cy-11 cx-3 cy-9  (left, angled in)
          path M cx+3 cy-9 Q cx+6 cy-11 cx+9 cy-9  (right, angled in)
          fill=none stroke=#1a1a1a stroke-width=1.3 stroke-linecap=round
  mouth: path M cx-6 cy+9 Q cx cy+6 cx+6 cy+9
         fill=none stroke=#1a1a1a stroke-width=1.5 stroke-linecap=round

surprised:
  eyes: r=2.8 (slightly larger)
  mouth: ellipse cx=cx cy=cy+9 rx=4 ry=5
         fill=none stroke=#1a1a1a stroke-width=1.5

determined:
  brows: line (cx-9, cy-9) → (cx-3, cy-11)  (left, angled down-in)
         line (cx+3, cy-11) → (cx+9, cy-9)  (right, angled down-in)
         stroke-width=1.5 stroke-linecap=round
  mouth: line (cx-7, cy+8) → (cx+7, cy+8) stroke-width=2.2

celebrating:
  eyes: same as happy
  mouth: same as happy but wider Q cx cy+16

## Poses (arm overrides)

default — arms angled down:
  left:  (cx, cy+32) → (cx-28, cy+52)
  right: (cx, cy+32) → (cx+28, cy+52)

pointing right:
  right: (cx, cy+32) → (cx+36, cy+18)

pointing left:
  left:  (cx, cy+32) → (cx-36, cy+18)

arms out / explaining / shrugging:
  left:  (cx, cy+32) → (cx-36, cy+30)
  right: (cx, cy+32) → (cx+36, cy+30)

arm raised / celebrating:
  right: (cx, cy+32) → (cx+28, cy+10)

typing at laptop:
  left:  (cx, cy+32) → (cx-22, cy+52)
  right: (cx, cy+32) → (cx+22, cy+52)
  laptop rect: x=cx-28 y=cy+52 w=56 h=32 rx=4 fill=none stroke=#1a1a1a stroke-width=1.5
  base line:   (cx-32, cy+84) → (cx+32, cy+84)
  screen text: optional 8px monospace centered in laptop

on phone (right hand to ear):
  left:  (cx, cy+32) → (cx-28, cy+52)
  right: (cx, cy+32) → (cx+18, cy+14)
  phone rect: x=cx+16 y=cy+4 w=10 h=18 rx=2 fill=none stroke=#1a1a1a stroke-width=1.5

## Accessories (role identifiers, drawn above head)

headset (support / customer service):
  arc:  path M cx-18 cy Q cx-18 cy-20 cx cy-20 Q cx+18 cy-20 cx+18 cy
        fill=none stroke=#1a1a1a stroke-width=1.8
  left pad:  rect x=cx-22 y=cy-4 w=7 h=10 rx=3 fill=none stroke=#1a1a1a stroke-width=1.8
  right pad: rect x=cx+15 y=cy-4 w=7 h=10 rx=3 fill=none stroke=#1a1a1a stroke-width=1.8

hard hat (engineer / ops / builder):
  dome: path M cx-20 cy Q cx-18 cy-20 cx cy-20 Q cx+18 cy-20 cx+20 cy
        fill=#1a1a1a stroke=none
  brim: line (cx-23, cy) → (cx+23, cy) stroke=#1a1a1a stroke-width=2.5

crown (executive / decision-maker / CEO):
  path: M cx-16 cy-2 L cx-16 cy-14 L cx-8 cy-8 L cx cy-14
        L cx+8 cy-8 L cx+16 cy-14 L cx+16 cy-2 Z
  fill=none stroke=#1a1a1a stroke-width=1.5

glasses (analyst / researcher):
  left lens:  circle cx=cx-7 cy=cy r=6 fill=none stroke=#1a1a1a stroke-width=1.2
  right lens: circle cx=cx+7 cy=cy r=6 fill=none stroke=#1a1a1a stroke-width=1.2
  bridge:     line (cx-1, cy) → (cx+1, cy) stroke-width=1.2
  left arm:   line (cx-13, cy) → (cx-20, cy+2) stroke-width=1.2
  right arm:  line (cx+13, cy) → (cx+20, cy+2) stroke-width=1.2

## Horizontal positioning by actor count (panel width = 640)

| Actors | cx values                        |
|--------|----------------------------------|
| 1      | 320                              |
| 2      | 160, 480                         |
| 3      | 110, 320, 530                    |
| 4      | 90, 250, 390, 550                |

cy (head center) = panel_top + 130 always.
This leaves ~110px above for bubbles and ~110px below for legs + label.