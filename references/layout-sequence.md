# scenepad sequence layout

Use for: API calls, service chains, auth flows, database queries,
webhook pipelines, retry loops — any story where the actors are
systems not people, and time order matters more than emotion.

## Structure

Actors as vertical swimlanes. Time flows top to bottom.
Messages are horizontal arrows between lanes.
Width always 640. Lane count determines spacing.

## ViewBox height

  base:          120px (headers + top padding)
  per message:   60px
  bottom:        40px

  total = 120 + (message_count × 60) + 40

## Lane positions (cx) for N actors

| N | cx values                              |
|---|----------------------------------------|
| 2 | 160, 480                               |
| 3 | 120, 320, 520                          |
| 4 | 100, 240, 400, 540                     |

## Actor header boxes

  rect: width=110 height=36 rx=6 centered on lane cx, y=30
        fill=#ffffff stroke=#1a1a1a stroke-width=1.5
  text: actor name 11px font-weight=500 fill=#1a1a1a centered in rect

  lifeline: dashed line from rect bottom to scene bottom
            x=cx stroke=#cccccc stroke-width=1 stroke-dasharray=4 3

## Messages

First message y = 110. Each subsequent message y += 60.

Request arrow (left to right or right to left):
  line x1=sender_cx y1=msg_y x2=receiver_cx y2=msg_y
  stroke=#1a1a1a stroke-width=1.5 marker-end=arrow

Response arrow (dashed, return direction):
  same but stroke-dasharray=5 3

Message label (above line):
  text x=midpoint_x y=msg_y-8 text-anchor=middle font-size=10 fill=#1a1a1a

Subtext (below line, e.g. payload or status):
  text x=midpoint_x y=msg_y+16 text-anchor=middle font-size=9 fill=#888888

## Activation bar (shows actor is processing)

When an actor is doing work between receiving and responding:
  rect: width=8 centered on cx
        y from receive_y to respond_y
        fill=#f5f5f5 stroke=#e0e0e0 stroke-width=1

## Annotation notes

For error states, retries, timeouts, conditions:
  rect: rx=4 fill=#f5f5f5 stroke=#cccccc stroke-width=0.5 stroke-dasharray=3 2
        width ~120px positioned to the right of the relevant arrow
  text: 9.5px fill=#888888

## Self-message (retry, internal loop)

  path: M cx msg_y Q cx+50 msg_y cx+50 msg_y+30 Q cx+50 msg_y+60 cx msg_y+60
        fill=none stroke=#1a1a1a stroke-width=1.5 marker-end=arrow
  label: to the right of the loop, 9.5px fill=#888888

## Inline visual blocks in sequence scenes

Code / payload block (attached to a message):
  same code block from bubbles.md but placed below the message line
  connected with a short vertical dashed leader from message midpoint
  width 200px max, float to side that has more space

Status badge (for HTTP status, success/fail):
  pill shape: rect rx=10 height=18 width=auto
  2xx: fill=#e8f5e9 stroke=#28c840 stroke-width=0.5 text fill=#1a7a1a
  4xx: fill=#fff3e0 stroke=#febc2e stroke-width=0.5 text fill=#7a4f00
  5xx: fill=#ffebee stroke=#ff5f57 stroke-width=0.5 text fill=#7a0000
  text: 9px font-family=monospace centered in pill

## Caption

  x=320 y=viewBox_height-14 text-anchor=middle
  font-size=13 font-weight=500 fill=#1a1a1a