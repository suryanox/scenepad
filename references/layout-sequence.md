# scenepad sequence layout

Use for: API calls, service interactions, technical flows, system handshakes.

## Structure

Actors appear as vertical swimlanes.
Time flows top to bottom.
Messages are horizontal arrows between lanes.

## ViewBox

  width:  680 always
  height: (number of actors * 120) + (number of messages * 60) + 80
  minimum height: 300

## Swimlane columns

For N actors, divide the safe width (640px, x=20 to x=660) equally.

  lane center x for N actors:
    1 actor:  340
    2 actors: 187, 493
    3 actors: 140, 340, 540
    4 actors: 113, 264, 416, 567

## Actor headers (top of each lane)

  rect: width=100 height=36 rx=6 centered on lane x, y=30
        fill=#ffffff stroke=#1a1a1a stroke-width=1.5
  text: actor name, 11px medium, centered in rect
  lifeline: dashed vertical line from rect bottom to scene bottom
            x = lane center, stroke=#888888 stroke-width=1 stroke-dasharray=4 3

## Messages (horizontal arrows)

Each message between two actors:
  y position: starts at y=100, increments by 60 per message
  line: from sender lane x to receiver lane x at message y
        stroke=#1a1a1a stroke-width=1.5 marker-end=arrow
  label: 10px centered above the line, fill=#1a1a1a
  response arrow: same but dashed stroke-dasharray=5 3, label below line

## Activation bars (optional, shows processing time)

When an actor is actively doing something:
  narrow rect: width=8 centered on lifeline
               y from when message received to when response sent
               fill=#f5f5f5 stroke=#1a1a1a stroke-width=1

## Notes / annotations (optional)

Inline note for error states, retries, timeouts:
  rect: rx=4 fill=#f5f5f5 stroke=#888888 stroke-width=0.5 stroke-dasharray=3 2
  text: 10px muted, inside rect
  position: to the right of the relevant arrow

## Self-message (actor calls itself, retry loop)

  curved path from lane x, looping right and back
  label to the right of the loop
  use for: retry, internal processing, queue

## Caption

  x=340 y=(viewBox height - 14) text-anchor=middle 13px medium fill=#1a1a1a
