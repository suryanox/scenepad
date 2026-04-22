# scenepad bubble primitives

## Core rules

- Every bubble sits ABOVE the speaker. Never beside or below.
- Tail tip lands 8px ABOVE the chin. Chin = head_cy + head_radius.
  tail_tip_y = head_cy + head_radius - 8
- Tail base is two points on the bubble bottom, 7px either side of speaker cx.
- Overdraw the bubble bottom stroke with a same-color line between the two base
  points so the tail looks seamlessly attached.
- One bubble per actor per panel. No stacking.
- Max 2 lines of text per bubble.
- Bubble width: size to text. Never let text approach within 14px of bubble edge.
  Estimate: line_chars × 7 + 28px padding. Min 100px. Max 220px.
- Bubble bottom y = head_cy - head_radius - 8  (8px gap above head top)
- Bubble height: 36px for 1 line, 52px for 2 lines.
- Bubble top y = bubble_bottom_y - bubble_height

## Standard bubble (white fill)

  rect:   x = cx - W/2
          y = bubble_top_y
          width = W, height = H, rx=10
          fill=#ffffff stroke=#1a1a1a stroke-width=1.5

  tail path (triangular, seamless):
          M cx-7 bubble_bottom_y
          L cx+7 bubble_bottom_y
          L cx   tail_tip_y
          Z
          fill=#ffffff stroke=#1a1a1a stroke-width=1.5 stroke-linejoin=round

  overdraw (hides bubble bottom between tail base points):
          line x1=cx-7 y1=bubble_bottom_y x2=cx+7 y2=bubble_bottom_y
          stroke=#ffffff stroke-width=2

  text line 1: x=cx y=bubble_top_y+22 text-anchor=middle
               font-size=11.5 font-weight=500 fill=#1a1a1a
  text line 2: x=cx y=bubble_top_y+38 text-anchor=middle
               font-size=10.5 fill=#666666

## Inverted bubble (black fill — peak moment, use once per scene)

  rect:   same position math, rx=10
          fill=#1a1a1a stroke=none

  tail path:
          same points, fill=#1a1a1a stroke=none

  overdraw: stroke=#1a1a1a stroke-width=2

  text line 1: fill=#ffffff font-weight=500 font-size=11.5
  text line 2: fill=#aaaaaa font-size=10.5

## Thought bubble (internal monologue, uncertainty)

  shape: rounded rect, fill=#f5f5f5 stroke=#cccccc stroke-width=1 rx=10
  tail:  three small circles descending toward head
         r=4 at bubble_bottom_y+6
         r=3 at bubble_bottom_y+14
         r=2 at tail_tip_y
         all fill=#cccccc stroke=none
  text:  fill=#888888 font-style=italic

## System bubble (API, service, database actors)

  shape: rect rx=6 (squarer than speech bubble)
         fill=#ffffff stroke=#1a1a1a stroke-width=1.5
  top label inside: method/status in 9px monospace fill=#aaaaaa
                    e.g. "POST /auth" or "500 Internal Error"
  main text: 11px fill=#1a1a1a
  tail: same geometry as standard bubble

## Inline visual blocks (use instead of text when content demands it)

Sometimes the most natural representation of what an actor is saying
or doing is NOT a text bubble. Use these inline blocks ATTACHED to
or NEAR the actor instead:

### Code snippet block
When actor is showing, writing, or reviewing code:
  rect: fill=#f5f5f5 stroke=#e0e0e0 stroke-width=1 rx=6
  header bar: fill=#ebebeb height=22 rx=6 (top only)
  traffic lights: circles r=4 at x+14 x+28 x+42 from left, y=header center
                  colors: #ff5f57 #febc2e #28c840
  code lines: 9.5px monospace fill=#444 x=rect_x+12 line-height=16px
  max 4 lines of code, keep lines short (under 35 chars)
  width: 200-260px, height: header(22) + lines×16 + 16px padding

### Terminal / deploy block
When actor is running commands or deploying:
  Same as code block but:
  success lines: fill=#28c840
  error lines:   fill=#ff5f57
  header label:  "bash" or "terminal" 9px #aaaaaa centered

### Sticky note / idea block
When actor is brainstorming, proposing, or ideating:
  rect: fill=#fffde7 stroke=#f0e060 stroke-width=1 rx=4
  slight rotation: transform="rotate(-1.5, cx, cy)"
  text: 11px fill=#5d4e00 line-height=16px, left-aligned with 12px padding
  max 3 short lines
  fold: small triangle at bottom-right corner
        path from (x+w-10,y+h) to (x+w,y+h-10) to (x+w,y+h)
        fill=#e8d800 stroke=none

### Whiteboard / diagram block
When actor is sketching, presenting, or explaining with visuals:
  outer rect: fill=#fafafa stroke=#e0e0e0 stroke-width=1 rx=6
  inner sketch: simple SVG shapes representing the diagram
                keep abstract — boxes, arrows, lines only
  label below: 9px muted, describes what is being sketched

### Chat / message bubble block
When showing a message thread or notification:
  outer rect: fill=#f5f5f5 stroke=none rx=8
  message rows: alternating left/right alignment
                left = received (fill=#ffffff stroke=#e8e8e8 rx=10)
                right = sent (fill=#1a1a1a rx=10 text fill=#fff)
  timestamp: 8px #aaaaaa between messages

### Data / metric block
When showing numbers, charts, or results:
  rect: fill=#ffffff stroke=#e8e8e8 stroke-width=1 rx=6
  big number: 24px font-weight=500 fill=#1a1a1a centered
  label: 10px fill=#aaaaaa below the number
  delta badge (optional): small pill, green fill for positive

## Bubble placement when panel has 2 actors

Left actor (cx ~160): bubble centered on cx, extends right
Right actor (cx ~480): bubble centered on cx, extends left
If bubbles would overlap in the middle (rare with 2-line bubbles):
  shift left actor bubble left by 20px
  shift right actor bubble right by 20px
  Never let bubble text overflow the panel rect boundary (x=8 to x=632)

## Bubble placement when panel has 3 actors

Left (cx ~110):   bubble x starts at 20, extends right, max width 160px
Center (cx ~320): bubble centered, max width 160px
Right (cx ~530):  bubble x ends at 620, extends left, max width 160px
Stagger heights if bubbles at similar y would overlap:
  outer actors at standard height, center actor bubble 20px higher