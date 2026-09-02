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

Builds or refreshes a complete messaging hierarchy for any B2B product or company:
- Positioning foundation (best-fit customer, market category, competitive alternatives, differentiated capabilities, one-line positioning)
- Galvanizing narrative ("the big idea")
- 3 messaging pillars with proof points
- Proof point bank (with named customer approval tracking)
- Persona-specific angles
- Competitive frame + objection handling
- Asset mapping (press release, website, deck, email)
- Elevator pitches (15s, 30s, 2min)

Creates a persistent project folder for each engagement, with a live `CHECKLIST.md` and a dated `DECISIONS.md` decision log, so the work can be resumed across sessions.

### Two modes

- **From scratch** — no prior messaging hierarchy exists. The skill builds a phrase library from whatever source materials exist (pitch deck, one-pager, website, sales scripts, etc.) and fills the hierarchy from there.
- **Quarterly refresh** — a prior approved hierarchy exists and needs updating against what changed. The skill runs four discovery stages in order — the current website (carry / change / drop each claim), what shipped since the last version, outside signals (category and competitors), and inside knowledge (numbers, verified customer list, the positioning owner's accumulated knowledge) — each stage ending with questions to the owner before the next stage starts. Only after all four stages close does it move on to hard rules and the fill.

---

## How to install

**Option 1 — Drag and drop**: Drag `launch-messaging.skill` into the Cowork plugins area.

**Option 2 — GitHub repo**: Put this in a GitHub repo and teammates install with:
```
claude plugins add <your-org>/<your-repo>
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

## What this is NOT

This folder is **completely separate** from any specific company's launch messaging project. A project folder created by running this skill (its own `LAUNCH.md`, `CHECKLIST.md`, `DECISIONS.md`, `state.json`, and messaging hierarchy template) belongs to that engagement and should never be modified based on anything in this skill folder.

This skill is *built from* lessons learned running real messaging projects, generalized into a tool for any product — it is not a continuation of, or a replacement for, any one company's project.

---

## Source files (for editing the skill)

The editable skill source lives in `launch-messaging/` next to this README (`SKILL.md` plus `references/`). Edit those files directly, then repackage using:
```bash
python -m scripts.package_skill launch-messaging/ "Master Narrative Skill/"
```
