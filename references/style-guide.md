# scenepad style guide

## Philosophy

Editorial minimalism. Every line earns its place.
Think New Yorker spot illustration meets technical sketchpad —
clean, immediate, no decoration. The scene should feel handcrafted
not generated.

## Page wrapper (HTML shell)

Every output file uses this shell. No exceptions.

  body background:  #f0ede8  (warm off-white, never pure white)
  scene card:       background #ffffff, border-radius 16px, padding 40px
                    box-shadow: 0 2px 0 #d4d0c8, 0 0 0 1px #e0ddd6
  max-width:        720px, centered
  header bar:       flex row, space-between, border-bottom 1px #efefef, margin-bottom 32px
                    left: "scenepad" 11px monospace #bbb letter-spacing 1.5px uppercase
                    right: the /scenepad command 11px monospace #ddd

## Palette

| Token   | Hex     | Use                                          |
|---------|---------|----------------------------------------------|
| paper   | #ffffff | Scene card background                        |
| warm-bg | #f0ede8 | Page background                              |
| ink     | #1a1a1a | All strokes, text, figures                   |
| muted   | #aaaaaa | Actor labels, panel numbers, timestamps      |
| subtle  | #666666 | Secondary bubble text, annotations          |
| surface | #f5f5f5 | Thought bubbles, code blocks, terminal bg   |
| border  | #e8e8e8 | Panel borders, dividers                      |
| invert  | #1a1a1a | Peak-moment bubble fill (white text inside)  |

One accent rule: inverted black bubble = the single most important
line in the whole scene. Use at most once per output.

## Stroke weights

| Element                    | Weight          |
|----------------------------|-----------------|
| Figure head and limbs      | 2px             |
| Panel border               | 1px             |
| Speech bubble outline      | 1.5px           |
| Connector / escalation     | 1.2px dashed    |
| Terminal / code box border | 1px #e0e0e0     |
| Annotation leader          | 0.5px dashed    |

## Typography

Font stack: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif
Monospace stack: 'SF Mono', 'Fira Code', 'Consolas', monospace
No external fonts. No Google Fonts. No CDN.

| Element            | Size  | Weight | Color   |
|--------------------|-------|--------|---------|
| Panel number       | 9px   | 400    | #ccc    |
| Bubble line 1      | 11.5px| 500    | ink     |
| Bubble line 2      | 10.5px| 400    | #666    |
| Inverted bubble L1 | 11.5px| 500    | #ffffff |
| Inverted bubble L2 | 10.5px| 400    | #aaaaaa |
| Actor label        | 10px  | 400    | #aaaaaa |
| Terminal text      | 9.5px | 400    | monospace|
| Success text       | 9.5px | 400    | #28c840 |
| Annotation         | 9.5px | 400    | #aaaaaa |

## Spacing (4px grid)

- Panel gap (vertical, between stacked panels): 40px
- Figure cy (head center) from panel top: 130px minimum
- Bubble bottom to head top gap: 8px exactly
- Bubble text padding: 14px horizontal, 10px vertical per line
- Actor label: 8px below feet
- Terminal box margin from figure: 40px minimum

## ViewBox

Width always 640. Height = (panels × 260) - 40.

  1 panel:  0 0 640 220
  2 panels: 0 0 640 480
  3 panels: 0 0 640 740

Each panel occupies a 640 × 220 rect with rx=12.
Panel y positions: panel N starts at (N-1) × 260.

## What never appears

- Drop shadows on figures
- Gradients on figures or backgrounds
- Color fills anywhere except terminal success green #28c840
- Decorative flourishes or borders
- Emoji in SVG
- External images or fonts
- Blob or rounded character shapes