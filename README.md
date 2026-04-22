# scenepad

Turn any story, flow, or scenario into a clean SVG scene — stick figures, speech bubbles, panels. Works in Claude Code, Cursor, Gemini CLI. No Figma, no design skills, no dependencies.

```
/scenepad "customer calls support, support escalates to engineer, engineer deploys fix"
```

→ outputs a self-contained HTML file you can screenshot, embed, or share.

---

## What it generates

- White background, black ink, no color
- Stick figures with expressions and role accessories
- Speech bubbles (standard, thought, inverted/peak moment)
- Panel layouts for stories, sequence diagrams for technical flows
- Single file, opens in any browser, no build step

---

## Install

**Claude Code**
```bash
git clone https://github.com/suryanox/scenepad ~/.claude/skills/scenepad
```
Restart Claude Code. Type `/scenepad` to trigger.

## Usage

```
/scenepad "your story here"
```
---

## Output

Every run creates one file:

```
scenepad-out/
└── your-story-slug.html    ← self-contained, no dependencies
```

Screenshot it, embed it in a doc, drop it in a Notion page, share the file directly.

---

## How it works

scenepad is a Claude Code skill — a markdown file that gives Claude a strict visual system and SVG primitive library. When you type `/scenepad`, Claude:

1. Parses your story into actors and interactions
2. Chooses panel or sequence layout
3. Draws each figure from the primitive library
4. Applies the style guide (stroke weights, spacing, typography)
5. Outputs a single self-contained HTML file

No API calls. No external services. Runs entirely inside your AI coding assistant.

---

## License

MIT
