---
name: launch-messaging
description: >
  Build a complete B2B product or company launch messaging hierarchy from scratch — positioning framework, galvanizing narrative, messaging pillars, proof points, persona angles, competitive frame, and elevator pitches. Creates a persistent project folder (resumable across sessions) and a formatted Word document deliverable. Use this skill whenever someone wants to: develop launch copy or positioning for a product, create a messaging framework or messaging hierarchy, work on go-to-market (GTM) messaging, write positioning for a new product or feature, build out value props and pillars, nail down their company narrative, create a press release foundation, or develop sales messaging. Also trigger this skill for "what's our big idea", "how do we talk about X", "positioning statement", "elevator pitch", or any request to work through how a company or product should communicate its value. Works for any B2B product — SaaS, infrastructure, developer tools, AI products, enterprise software.
---

# Launch Messaging Skill

You are helping someone build a complete, approved messaging hierarchy for a product or company launch. The output is a structured document that becomes the single source of truth for a press release, website, sales deck, and all other launch materials.

This is a multi-session project. Your job is to:
1. Set up a persistent project folder they can return to
2. Process their source materials into a phrase library
3. Fill the messaging hierarchy template section by section with explicit approval at each step
4. Deliver a formatted Word document

---

## PHASE 0: PROJECT SETUP

### Before writing a single line of copy

Ask the user three things (in one message):
1. **Product/company name** — what are you launching?
2. **Source materials** — what existing documents do you have? (pitch deck, one-pager, existing website, sales scripts, internal brainstorms, investor docs, etc.). Ask them to share or upload what they have.
3. **Where to save this** — confirm the project folder location (default: inside their Claude/Dropbox-synced folder, in a new subfolder named after the product).

Then create the project folder:

```
[project-name]-launch-messaging/
├── LAUNCH.md              ← project brain (you'll write this)
├── state.json             ← progress tracker + decisions log
├── research/
│   └── language-lexicon.md ← phrase library from source materials
└── deliverables/
    └── messaging-hierarchy-template.md ← the main output
```

Write `LAUNCH.md` as the project brain (see template in references/launch-md-template.md). Write `state.json` with initial structure (see template in references/state-json-template.json).

---

## PHASE 1: BUILD THE PHRASE LIBRARY

Before filling the template, read every source material the user shares. For each document:
- Extract exact phrases, headlines, value props, stats, and customer proof points
- Note the source and whether it's canonical (approved for external use) or non-canonical (internal/investor-facing)

Save everything to `research/language-lexicon.md` organized by theme:
1. Identity & positioning statements
2. Product/feature language
3. Technical architecture language
4. Proof points and stats (flag which are verified vs. unverified)
5. Customer language and quotes
6. Competitive/market language
7. Messaging themes to develop

Tell the user: "I've read your source materials and built a phrase library. Here's what I found..." — summarize the strongest existing language and any gaps.

---

## PHASE 2: ESTABLISH HARD RULES

Before writing anything, surface the decisions that affect ALL downstream content. Ask the user (in one message):

1. **Language constraints**: Any words or phrases to always avoid or always use? (Examples: competitors avoid "cloud," enterprise companies avoid "AI-powered," etc.)
2. **Named customer rules**: Which customer names are approved for public use (web, press release) vs. internal/sales-only?
3. **Lead differentiator**: Of all the things you do, what's the ONE thing customers hit first — the #1 reason they pay you?
4. **The big vision**: In one sentence, what's the tectonic shift happening in the world that makes your product necessary?

Document the answers as a "Hard Rules" section in `LAUNCH.md`. These apply to every section of the template — enforce them when writing.

---

## PHASE 3: FILL THE TEMPLATE — DEPENDENCY ORDER

Fill the messaging hierarchy one section at a time. Present your draft, get approval, then move on. Never skip ahead.

**Critical**: Fill in dependency order, NOT top-to-bottom. The template's Section 1 lists competitive alternatives before best-fit customer — but you can't identify true alternatives without first knowing WHO the buyer is. Use this order:

### The 11-Step Fill Order

| Step | Section | Why this order |
|------|---------|----------------|
| 1 | **Best-fit customer** (1d) | Everything filters through WHO. Alternatives, capabilities, and value all depend on who you're speaking to. |
| 2 | **Market category** (1e) | The buyer needs a mental shelf. Category determines how they evaluate alternatives. |
| 3 | **Competitive alternatives** (1a) | Now that you know WHO and what CATEGORY, identify true alternatives (not just named competitors — include "do nothing" and "build it themselves"). |
| 4 | **Differentiated capabilities + value** (1b + 1c) | Capabilities are only meaningful relative to the alternatives you just named. Value ties capabilities to outcomes the best-fit customer cares about. |
| 5 | **One-line positioning** (1f) | Assembles steps 1-4 into one sentence. The strategic anchor. |
| 6 | **Galvanizing narrative** (2a-2d) | The creative expression of the positioning. The #1 deliverable. Needs positioning as input. |
| 7 | **Messaging pillars** (Section 3) | Structural supports for the narrative. 3 is ideal. Each must be independently compelling. |
| 8 | **Proof point bank** (Section 4) | Evidence that makes pillars credible. Verify sources before writing. |
| 9 | **Persona-specific angles** (Section 5) | Restate the message in each buyer's language. Needs pillars defined first. |
| 10 | **Competitive frame** (Section 6) | Landscape, ranked differentiators, objection handling. Builds on everything above. |
| 11 | **Asset mapping + elevator pitches** (Section 7 + Appendix) | Maps hierarchy to deliverables. Pitches synthesize everything into verbal formats. |

### How to present each section

For each step:
1. Write a complete draft
2. Show it to the user with: "Here's my draft for [section]. Take a look — what would you change?"
3. Incorporate feedback
4. Get explicit approval ("Approved" / "Looks good" / "Next") before moving on
5. After approval, save to the template file and update `state.json`

If the user says "looks great, next" — move on. Don't re-ask or re-explain.

### What makes each section good

**Best-fit customer**: Be specific. Not "enterprise companies" but "mid-to-large enterprise (500+ employees) with existing [X] initiatives that have hit the wall between prototype and production." Include the exact buying trigger — the moment that sends them looking.

**Market category**: Name the category, then explain the category story. Add a "discovery hook" — the more familiar language the buyer searches for that leads them to you. This preserves existing brand awareness while broadening.

**Competitive alternatives**: Include all five types: (1) do nothing, (2) build it themselves, (3) direct competitors, (4) adjacent tools that partially solve it, (5) legacy/incumbent approaches. Most buyers don't "not buy" — they buy something else.

**Differentiated capabilities**: Mark the LEAD differentiator with ⭐. This should be the capability that (a) only you have, (b) solves the problem buyers hit first, and (c) is the primary conversion trigger. Reference the "Hard Rules" from Phase 2.

**Galvanizing narrative**: This is the big idea. It has three parts:
- The Shift: What's changing in the world that makes this product necessary and urgent?
- The Problem: What breaks, fails, or gets stuck under the current approach?
- The Unlock: How does this product change the game?

The opening line should be vision-level — a declaration about the world, not a product pitch. If the user has a "big idea" phrase (like "All UI will be AI"), it opens here.

**Messaging pillars**: 3 is ideal. Each pillar: one-liner (outcome, not feature), explanation (2-3 sentences), proof points (feature → outcome → evidence → competitive angle). Lead with the outcome, not the feature.

**Proof point bank**: Split into categories: adoption stats, ecosystem proof, product facts, named customers. For named customers, ALWAYS document who is approved for public (web, PR) use vs. internal/sales-only, and the verification source. This prevents costly mistakes.

**Persona angles**: For each persona: what they own, their primary pain in their own words, the primary message for them, their top 2 pillars, and the objection to pre-empt.

**Competitive frame**: A landscape table (approach, limitation, how you're different), then ranked differentiators (1-3 max), then objection handling for the 4-6 most common objections.

**Elevator pitches**: 15 seconds (one breath), 30 seconds (elevator ride), 2 minutes (meeting opener). These are verbal — conversational, not written copy.

---

## PHASE 4: GENERATE THE WORD DOCUMENT

After the template is fully approved, generate a formatted Word document.

Read the docx skill at `/sessions/*/mnt/.skills/skills/docx/SKILL.md` for the exact generation approach.

Key styling decisions to make with the user:
- Brand accent color (hex code)
- Font preference (default: Arial or Calibri)
- Company/product name for header

The Word document should have:
- Cover page with product name, date, and "CONFIDENTIAL — Internal Use Only"
- Branded header and footer on all pages
- Section headers with accent color underlines
- Tables for structured data (alternatives, proof points, persona angles) with alternating row shading
- Blockquote styling for narrative sections
- Callout boxes for hard rules and usage warnings (e.g., named customer rules)

Save the .docx to `deliverables/[ProductName]-Messaging-Hierarchy.docx`.

---

## PHASE 5: ESTABLISH RESUMABILITY

After completing the template and Word doc, update `LAUNCH.md` to reflect:
- What's done (template complete, docx generated)
- What's next (website copy, sales deck, press release, etc.)
- The editing workflow (edit the .md → note that docx needs regeneration)

Update `state.json` with all decisions made during the fill process.

Tell the user: "This project is set up so any future session can pick up where we left off. Just trigger it with '[product name] launch messaging' and I'll read the project files and resume."

---

## ONGOING: EDITING WORKFLOW

When Travis (or any user) returns to update the messaging, the workflow is:
1. Read `LAUNCH.md` (resume instructions, hard rules)
2. Read `deliverables/messaging-hierarchy-template.md` (source of truth)
3. Make the requested edit in the .md file
4. Offer to regenerate the Word document
5. Log the change in `state.json` decisions

---

## VOICE & TONE DEFAULTS

These apply unless the user specifies otherwise:
- **Confident but not hype-y** — enterprise buyers distrust buzzwords
- **Outcome-oriented** — lead with what it does for them, not features
- **Technically credible** — show you understand production reality, not just demos
- **Collaborative** — "your [product]" not "our product"
- Avoid: "revolutionary", "game-changing", "cutting-edge", "unlock", "supercharge", "leverage"
- Prefer: specific outcomes, production-grade language, the buyer's own words

---

## REFERENCE FILES

- `references/messaging-hierarchy-template.md` — The blank template with all 7 sections and the appendix. Copy this into the user's project folder to start.
- `references/launch-md-template.md` — The LAUNCH.md project brain template. Customize for each project.
- `references/state-json-template.json` — The state.json starting structure.
