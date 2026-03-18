# [Product Name] — Launch Messaging Project

## Quick Reference
- **Owner**: [Name, Title @ Company]
- **Product**: [Product Name]
- **Single source of truth**: `deliverables/messaging-hierarchy-template.md`
- **Formatted deliverable**: `deliverables/[ProductName]-Messaging-Hierarchy.docx`

---

## HOW TO RESUME THIS PROJECT

1. **Read this file** — project context, rules, and workflow
2. **Read the source of truth** — `deliverables/messaging-hierarchy-template.md` (complete + approved content)
3. **Check what [Owner] wants**:
   - Editing messaging? → Follow "Editing Workflow" below
   - Creating a downstream asset? → Pull from the template, see "Phase Plan"
   - Adding new source material? → Extract to `research/language-lexicon.md`, then update template
   - Updating named customers? → Re-verify before any public-facing changes

4. **Read additional files only as needed**:
   - `research/language-lexicon.md` — exact phrases from source docs
   - `state.json` — decision log and rationale
   - `deliverables/FILL-ORDER.md` — HISTORICAL ONLY

---

## HARD RULES

*[Fill these in during Phase 2 of the skill. These are the constraints that apply to ALL content.]*

### 1. [Language constraint 1]
[Description + what's allowed / forbidden + rationale]

### 2. [Lead differentiator]
[What to lead with and why]

### 3. Named Customer Usage Rules
- **Web / PR / Public**: [List of approved companies — verified in CRM]
- **Sales / NDA**: All named companies
- **Before any new public asset**: Re-verify in CRM

### 4. [Key stat]
Use [specific number]. Not [other versions]. [Who corrected this and when.]

### 5. [Vision statement]
**"[The galvanizing phrase]"** — Use as the opening line for storytelling: press release hero, website hero, pitch deck, meeting openers.

### 6. Voice & Tone
- [Characteristic 1]
- [Characteristic 2]
- Avoid: [word list]
- Prefer: [word list]

---

## EDITING WORKFLOW

1. Edit `deliverables/messaging-hierarchy-template.md` first — it's the source of truth
2. Regenerate the Word document (see docx generation script in `scripts/`)
3. Log the change in `state.json` decisions
4. Validate the docx

---

## FILE MAP

```
[project-name]-launch-messaging/
├── LAUNCH.md                           ← YOU ARE HERE
├── state.json                          ← Decisions + progress
├── scripts/                            ← Docx generation
├── research/
│   ├── language-lexicon.md             ← Phrase library
│   └── source-*.md                     ← Raw source extractions
└── deliverables/
    ├── messaging-hierarchy-template.md ← SOURCE OF TRUTH
    └── [ProductName]-Messaging-Hierarchy.docx
```

### File Roles
| File | When to read |
|------|-------------|
| `LAUNCH.md` | ALWAYS — first on every resume |
| `messaging-hierarchy-template.md` | ALWAYS — before any content work |
| `state.json` | When you need rationale for past decisions |
| `language-lexicon.md` | When drafting new copy |

---

## CURRENT STATE

### What's Done
- [List of completed sections / template status]
- [Word doc status]

### What's Next
| Phase | Output | Status |
|-------|--------|--------|
| Website Copy | `deliverables/website-copy.md` | Not started |
| Sales Enablement | `deliverables/sales-enablement/` | Not started |
| Launch Content | `deliverables/launch-content/` | Not started |
| Press Release | `deliverables/press-release.md` | Not started |

---

## KEY DECISIONS LOG

[The full decision log lives in `state.json`. Most important ones for quick reference:]

1. [Decision 1 — one line]
2. [Decision 2]
3. [Decision 3]

---

## PRODUCT SUMMARY

[2-3 sentences: what the product is, what problem it solves, and who it's for.]
