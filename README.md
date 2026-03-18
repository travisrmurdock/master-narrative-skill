# Master Narrative Skill

A reusable skill that guides Claude through building a complete B2B product or company launch messaging hierarchy — from raw source materials to an approved, structured document and formatted Word deliverable.

---

## What's in this folder

| File | What it is |
|------|-----------|
| `launch-messaging.skill` | The installable skill file. Install this in Cowork to make the skill available. |
| `README.md` | This file. |

---

## What the skill does

Builds a complete messaging hierarchy for any B2B product or company launch:
- Positioning foundation (best-fit customer, market category, competitive alternatives, differentiated capabilities, one-line positioning)
- Galvanizing narrative ("the big idea")
- 3 messaging pillars with proof points
- Proof point bank (with named customer approval tracking)
- Persona-specific angles
- Competitive frame + objection handling
- Asset mapping (press release, website, deck, email)
- Elevator pitches (15s, 30s, 2min)

Creates a persistent project folder for each engagement, so the work can be resumed across sessions.

---

## How to install

**Option 1 — Drag and drop**: Drag `launch-messaging.skill` into the Cowork plugins area.

**Option 2 — GitHub repo**: Install directly from this repo:
```
claude plugins add travisrmurdock/master-narrative-skill
```

---

## How to trigger

Once installed, Claude uses this skill automatically when someone says things like:
- "Help me build launch messaging for [product]"
- "I need to nail our positioning"
- "Create a messaging hierarchy for our launch"
- "Build our messaging framework"
- "Help me write our go-to-market messaging"

---

## Editing the skill

The `launch-messaging/` directory contains the unpacked source files. The `.skill` file is a zip archive. To edit:

1. Modify files in `launch-messaging/`
2. Repackage: `zip -r launch-messaging.skill launch-messaging/`
