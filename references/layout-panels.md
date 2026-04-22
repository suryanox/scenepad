# scenepad panel layout

## Panel geometry

Each panel is a stacked row. Width always 640. Height 220. rx=12.
Panel N top y = (N-1) × 260.   (220px tall + 40px gap)

  panel rect: x=0 y=panel_top width=640 height=220 rx=12
              fill=#fafafa stroke=#e8e8e8 stroke-width=1

  panel number: x=320 y=panel_top+18 text-anchor=middle
                font-size=9 font-family=monospace fill=#cccccc letter-spacing=2

Figure head center: cy = panel_top + 130

ViewBox height = (n_panels × 260) - 40   (no trailing gap)
  1 panel  → 220
  2 panels → 480
  3 panels → 740
  4 panels → 1000

## Connectors between panels

Vertical connector between panel N and panel N+1:
  dashed line x=320 from panel_N_bottom+4 to panel_N+1_top-4
  stroke=#cccccc stroke-width=1 stroke-dasharray=3 2

Escalation / handoff arrow (horizontal within a panel):
  dashed line between two actors at cy level
  stroke=#1a1a1a stroke-width=1.2 stroke-dasharray=5 3
  marker-end arrow
  label above line: 9.5px fill=#aaaaaa text-anchor=middle

## Scene types and how to render each

### Conversation (2 actors talking back and forth)
Layout: 2–3 panels, each showing one exchange.
Actors face each other (left actor arm points right, right actor arm points left).
Bubble alternates: panel 1 left actor speaks, panel 2 right actor responds.
Use standard white bubbles. Inverted bubble for THE climax line only (max one per entire scene).

### Escalation / handoff (3+ actors, thing passes along chain)
Layout: 3 panels, each panel shows the handoff to the next person.
In panel N: actor N speaks (bubble), points toward actor N+1.
Dashed escalation arrow between them labeled with what is passed.
Actor N+1 receives (neutral or determined face).

### Conflict → resolution (disagreement then agreement)
Layout: 3 panels.
Panel 1: both actors with conflicting bubbles (worried + determined faces)
Panel 2: tension — one actor with arms out (explaining), other with arms crossed
         Arms crossed pose: both arms diagonal crossing body centerline
         left arm: (cx, cy+32) → (cx+20, cy+52)
         right arm: (cx, cy+32) → (cx-20, cy+52)
Panel 3: resolution — both actors happy, use inverted bubble ONLY if this is
         the single most important moment in the entire scene
         Optional handshake: arrows pointing toward each other between actors

### Ideation / brainstorming (one or more people generating ideas)
Layout: 1–2 panels.
Replace or supplement speech bubbles with sticky note blocks (see bubbles.md).
Multiple stickies can float above/around an actor — max 3 per actor.
Stagger heights: first sticky standard position, second 10px higher and offset 20px right.
Actor pose: arms out / explaining or arm raised.
Use thought bubbles for uncertain ideas, stickies for concrete proposals.

### Presentation / demo (one actor shows something to others)
Layout: 2 panels.
Panel 1: presenter actor on left with whiteboard/diagram block beside them.
         Other actors on right facing left (arms slightly toward presenter).
Panel 2: reaction — audience actors with speech or thought bubbles responding.
Whiteboard block: rect fill=#fafafa stroke=#e0e0e0 rx=6, width=180, height=120
                  contains simplified SVG sketch of what is being shown.

### User flow (person interacts with a system/product)
Layout: 3–4 panels showing sequential states.
Left actor = human user. Right side = system represented as a terminal or UI block.
Each panel shows: user action → system response.
System "actor" has no figure — just a labeled box with rx=8.
System box label: product name or "System" 11px font-weight=500 centered.

### Code review / technical handoff
Layout: 2–3 panels.
Actors at laptops (typing pose).
Replace or supplement bubbles with code snippet blocks (see bubbles.md).
Code block floats to the side or above the actor, connected with a dashed leader line.
Leader line: 0.5px dashed stroke=#cccccc from actor arm tip to code block edge.

### Announcement / broadcast (one to many)
Layout: 1–2 panels.
Single actor centered or left, 2–3 receiver actors right.
Sender bubble: use inverted ONLY if this announcement is the peak moment of the entire scene.
Receivers have reaction bubbles or expressions only (no bubbles = silent reaction).

## What determines panel count

| Story beats | Panels | How to handle                               |
|-------------|--------|---------------------------------------------|
| 1           | 1      | Single panel                                |
| 2–3         | 2      | One beat per panel or combine               |
| 3–5         | 3      | Condense similar beats                      |
| 5–7         | 4      | Max 4 panels, combine beats aggressively    |
| 7+          | 4      | Truncate to key beats: setup, conflict, climax, resolution |

Always prefer fewer panels. Combine beats that happen simultaneously.
For 7+ beat stories, identify the 4 most critical beats and focus on those.
Do NOT create multiple files — consolidate into one compelling 4-panel scene.