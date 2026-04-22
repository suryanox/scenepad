# scenepad style guide

## Philosophy

Editorial minimalism. Every line earns its place.
Reads like a New Yorker spot illustration: immediate, clean, no decoration.

## Palette

| Token   | Hex     | Use                                     |
|---------|---------|-----------------------------------------|
| paper   | #ffffff | Background, always                      |
| ink     | #1a1a1a | All strokes, text, figures              |
| muted   | #888888 | Panel numbers, actor labels, timestamps |
| surface | #f5f5f5 | Thought bubbles, inactive panels        |
| invert  | #1a1a1a | Filled bubble bg, peak moment only      |

One accent rule: filled black bubble = emotional or narrative peak. Use at most once per output.

## Stroke weights

| Element               | Weight     |
|-----------------------|------------|
| Figure (head, limbs)  | 2px        |
| Panel border          | 1.5px      |
| Speech bubble outline | 1.5px      |
| Arrow / connector     | 1.5px      |
| Dashed annotation     | 0.5px dash |
| Dividers              | 0.5px      |

## Typography

Font stack: -apple-system, BlinkMacSystemFont, Segoe UI, sans-serif
No external fonts. No Google Fonts. No CDN.

| Element       | Size | Weight | Color |
|---------------|------|--------|-------|
| Panel number  | 10px | 400    | muted |
| Bubble text   | 11px | 400    | ink   |
| Actor label   | 10px | 400    | muted |
| Scene caption | 13px | 500    | ink   |
| Step label    | 9px  | 400    | muted |

## Spacing (4px grid)

- Panel internal padding: 20px
- Gap between panels: 12px
- Figure head to bubble gap: 10px
- Bubble text padding: 10px 14px
- Actor label margin-top: 8px
- Scene caption margin-top: 16px

## ViewBox dimensions

| Layout       | ViewBox      |
|--------------|--------------|
| Single panel | 0 0 680 280  |
| Two panels   | 0 0 680 280  |
| Three panels | 0 0 680 280  |
| Four panels  | 0 0 680 300  |
| Sequence     | 0 0 680 auto |

Always width="100%" with explicit viewBox. Never hardcode pixel width.

## What never appears

- Drop shadows
- Gradients
- Color fills on figures
- Decorative backgrounds
- Icons or emoji
- External images
- Rounded blob-style characters
