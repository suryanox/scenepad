---
name: scenepad
description: >
  Turn any story, flow, or scenario into a clean SVG scene.
  Generates stick figures, speech bubbles, and panels.
  Triggers on /scenepad or phrases like "draw a scene", "visualize this story",
  "show who talks to who", "make a comic panel", "sketch this flow".
version: 1.0.0
triggers:
  - /scenepad
  - draw.*scene
  - visualize.*story
  - show.*who.*talk
  - comic.*panel
  - sketch.*flow
  - scene.*diagram
---

# scenepad

Convert any story or scenario into a self-contained HTML+SVG scene file.
Output: white background, black ink, stick figures, speech bubbles, panels.
Always a single file. No dependencies. Opens in any browser.

## Execution steps

1. Parse — extract actors, sequence of interactions, what each says/does
2. Pick layout — see table below
3. Load references — always load style-guide.md + figures.md + bubbles.md
4. Load layout ref — layout-panels.md (people) or layout-sequence.md (systems)
5. Generate — single self-contained HTML file
6. Save — write to scenepad-out/<slug>.html
7. Confirm — print: scenepad-out/name.html — N actors, N panels

## Layout selection

| Scenario                 | Layout                       |
|--------------------------|------------------------------|
| 2-4 people talking       | panels, side by side         |
| Linear story with steps  | panels, horizontal strip     |
| API / service call chain | sequence, timeline swimlane  |
| Team meeting / group     | panels, grid                 |
| Single moment            | single panel                 |

## Reference files

| File                          | Load when                 |
|-------------------------------|---------------------------|
| references/style-guide.md     | always                    |
| references/figures.md         | always                    |
| references/bubbles.md         | always                    |
| references/layout-panels.md   | people / narrative scenes |
| references/layout-sequence.md | technical / system flows  |

## Output rules

- Single self-contained HTML, no external CSS, no JS libraries, no fonts
- Palette: #ffffff background, #1a1a1a ink, #888888 muted labels
- File saved to scenepad-out/ in current working directory
- Filename derived from story slug, lowercase, hyphens

## Examples

  /scenepad "customer calls support, support escalates to engineer, engineer deploys fix"
  /scenepad "service A requests token, auth returns 401, A retries, auth returns 200"
  /scenepad "PM wants feature by Friday, engineer says 3 weeks, they agree on Tuesday"
  /scenepad "user submits form, validation fails, user fixes it, form submits OK"
  /scenepad "founder pitches investor, investor asks hard questions, founder nails it"
