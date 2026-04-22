---
name: scenepad
description: >
  Turn any story, flow, or scenario into a clean SVG scene.
  Stick figures, speech bubbles, panels, inline visuals.
  Works in Claude Code, Cursor, Gemini CLI.
  No Figma, no design skills, no dependencies.
  Triggers on /scenepad or phrases like "draw a scene",
  "visualize this story", "show who talks to who",
  "sketch this flow", "make a comic panel".
version: 1.0.0
triggers:
  - /scenepad
  - draw.*scene
  - visualize.*story
  - show.*who.*talk
  - sketch.*flow
  - comic.*panel
  - scene.*diagram
---

# scenepad

Parse any story into actors, beats, and interactions.
Output: a single self-contained HTML file.
White card on warm background. Black ink figures. Panels stacked vertically.
Opens in any browser. No dependencies. Screenshot-ready.

## Step-by-step

1. Parse — identify actors, beats, what each does/says/shows
2. Classify scene type — see table below
3. Load references:
     always:    references/style-guide.md
                references/figures.md
                references/bubbles.md
     narrative: references/layout-panels.md
     technical: references/layout-sequence.md
4. Choose inline visuals — when an actor is coding, deploying, ideating,
   or demoing, use the right visual block instead of just text
5. Build the HTML — single file, no external deps
6. Save to scenepad-out/<slug>.html
7. Print: ✓ scenepad-out/name.html — N actors, N panels

## Scene type classifier

| Story contains...                          | Type       | Layout ref             |
|--------------------------------------------|------------|------------------------|
| People talking, negotiating, escalating    | narrative  | layout-panels.md       |
| Services, APIs, databases, HTTP calls      | technical  | layout-sequence.md     |
| Brainstorming, ideation, proposals         | narrative  | layout-panels.md       |
| User interacting with a product/UI         | narrative  | layout-panels.md       |
| Deployment, code review, debugging         | mixed      | panels + code blocks   |
| Decision, conflict, resolution             | narrative  | layout-panels.md       |
| Announcement, demo, presentation           | narrative  | layout-panels.md       |

## Inline visual selection guide

Do NOT use a text bubble when the actor is doing something visual.
Use the matching block from bubbles.md instead (or alongside):

| Actor is...                  | Use instead of text bubble    |
|------------------------------|-------------------------------|
| Writing or reviewing code    | code snippet block            |
| Running commands / deploying | terminal block                |
| Brainstorming / proposing    | sticky note block             |
| Sketching / presenting       | whiteboard block              |
| Showing a message thread     | chat block                    |
| Reporting a number / metric  | data / metric block           |
| Thinking out loud            | thought bubble                |

Combine: an actor can have a speech bubble AND a code block.
The speech bubble says what they mean. The code block shows the actual thing.

## Story parsing rules

Extract from natural language:
- Actor names or roles (Customer, PM, Auth Service, etc.)
- What they say → bubble text (max 2 lines, distill to essence)
- What they do → pose, expression, accessory
- What they show → inline visual block type

Map roles to accessories:
  support agent     → headset
  engineer / ops    → hard hat
  executive / CEO   → crown
  analyst           → glasses
  developer         → laptop pose
  customer / user   → no accessory, worried or neutral

## Output rules

- One HTML file per story
- HTML shell from style-guide.md exactly
- SVG viewBox width always 640
- Panels stacked vertically, never side by side
- File saved to scenepad-out/<slug>.html in cwd
- Slug = first 4 words of story, lowercase, hyphens

## Example invocations

Narrative:
  /scenepad "customer calls support, support escalates to engineer, engineer deploys fix"
  /scenepad "PM wants feature by Friday, engineer says 3 weeks, they compromise on Tuesday"
  /scenepad "founder pitches investor, investor asks hard questions, founder nails the answers"
  /scenepad "designer shows mockup, dev says it's impossible, they find a simpler solution"

Technical:
  /scenepad "service A requests token, auth returns 401, A retries with refresh, auth returns 200"
  /scenepad "browser requests page, CDN misses, origin fetches DB, CDN caches, browser renders"
  /scenepad "webhook fires, queue receives it, worker picks up, DB write succeeds, callback sent"

Mixed (use panels + inline visuals):
  /scenepad "dev opens PR, reviewer leaves 3 comments on the auth function, dev pushes fix, reviewer approves"
  /scenepad "PM shares metrics showing 40% drop, team brainstorms 5 ideas on stickies, they vote on one"
  /scenepad "designer demos prototype in Figma, stakeholder says change the color, designer updates live"