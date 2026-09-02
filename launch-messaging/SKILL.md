---
name: launch-messaging
description: >
  Build or refresh a complete B2B product or company launch messaging hierarchy — positioning framework, galvanizing narrative, messaging pillars, proof points, persona angles, competitive frame, and elevator pitches. Has two modes: FROM SCRATCH (no prior hierarchy exists) and QUARTERLY REFRESH (a prior approved hierarchy exists and needs updating against what changed). Creates a persistent, resumable project folder with a running CHECKLIST.md and a dated DECISIONS.md decision log, and delivers a formatted Word document. Use this skill whenever someone wants to: develop launch copy or positioning for a product, create or refresh a messaging framework or messaging hierarchy, work on go-to-market (GTM) messaging, write positioning for a new product or feature, build out value props and pillars, nail down their company narrative, create a press release foundation, develop sales messaging, or run a periodic refresh of an existing messaging hierarchy. Also trigger this skill for "what's our big idea", "how do we talk about X", "positioning statement", "elevator pitch", "quarterly messaging refresh", "update our narrative", or any request to work through how a company or product should communicate its value. Works for any B2B product — SaaS, infrastructure, developer tools, AI products, enterprise software.
---

# Launch Messaging Skill

**Version 2.0 — 02September2026.** Adds the quarterly refresh mode, the CHECKLIST.md / DECISIONS.md tracking pair, expanded hard rules, and sharper drafting rules for Phase 3. See CHANGELOG at the bottom.

You are helping someone build or refresh a complete, approved messaging hierarchy for a product or company. The output is a structured document that becomes the single source of truth for a press release, website, sales deck, and all other launch materials.

This is a multi-session project. Your job is to:
1. Set up a persistent project folder they can return to, with a running checklist and decision log
2. Process source materials into a phrase library — from scratch, or against what changed since the last version
3. Establish hard rules that bind every downstream section
4. Fill the messaging hierarchy template section by section with explicit approval at each step
5. Deliver a formatted Word document

### Two modes

Ask which mode applies before doing anything else — or infer it: if the user has an existing, previously-approved messaging hierarchy document, this is a **QUARTERLY REFRESH**; if not, this is **FROM SCRATCH**.

- **FROM SCRATCH** — no prior hierarchy exists. Follow PHASE 1 as written: build a phrase library from whatever source materials the user has, then move to PHASE 2.
- **QUARTERLY REFRESH** — a prior approved hierarchy exists. Replace PHASE 1 with the four-stage discovery process below. The rest of the skill (PHASE 2 hard rules, PHASE 3 fill, PHASE 4 document, PHASE 5 resumability) applies to both modes unchanged.

---

## PHASE 0: PROJECT SETUP

### Before writing a single line of copy

Ask the user (in one message):
1. **Product/company name** — what are you building messaging for?
2. **Mode** — is there a prior approved messaging hierarchy to refresh, or is this from scratch? If refreshing, ask for the prior document and its approval date.
3. **Source materials** — what existing documents do you have? (pitch deck, one-pager, existing website, sales scripts, internal brainstorms, investor docs, etc.). Ask them to share or upload what they have.
4. **Where to save this** — confirm the project folder location (default: inside their Claude/Dropbox-synced folder, in a new subfolder named after the product).

Then create the project folder:

```
[project-name]-launch-messaging/
├── LAUNCH.md              ← project brain (you'll write this)
├── CHECKLIST.md           ← live progress tracker, updated before every step (see references/checklist-template.md)
├── DECISIONS.md           ← numbered, dated log of every owner ruling, written the moment it's given
├── state.json             ← machine-readable progress tracker + decisions log
├── research/
│   └── language-lexicon.md ← phrase library from source materials (from-scratch mode)
│                              or per-stage discovery files (refresh mode)
└── deliverables/
    └── messaging-hierarchy-template.md ← the main output
```

Write `LAUNCH.md` as the project brain (see template in `references/launch-md-template.md`). Write `CHECKLIST.md` from `references/checklist-template.md`. Write `state.json` with initial structure (see template in `references/state-json-template.json`), setting `"mode"` to `"from_scratch"` or `"quarterly_refresh"`.

**Update CHECKLIST.md before the team moves to the next step, every time** — when a step opens, when a step closes, and when the owner rules on a question. Whoever starts a step reads CHECKLIST.md first. Use the marks `[ ]` open, `[~]` in progress, `[!]` waiting on the owner, `[x]` done.

**Write every owner ruling to DECISIONS.md the moment it is given** — numbered sequentially, dated, in the owner's own words where possible. Nothing later in the project should require the owner to repeat a ruling already logged here.

---

## PHASE 1: BUILD THE PHRASE LIBRARY (FROM SCRATCH MODE)

*Skip this phase in quarterly refresh mode — use the four-stage discovery process below instead.*

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

## PHASE 1 (QUARTERLY REFRESH MODE): FOUR-STAGE DISCOVERY

When a prior approved hierarchy exists, don't start from a blank phrase library — start from what changed. Run four discovery stages in order. **Each stage ends with questions to the owner before the next stage starts.** Log every answer in DECISIONS.md the moment it's given, and update CHECKLIST.md as each stage opens and closes. Don't touch the hierarchy template until all four stages are closed.

### Stage 1 — The current website (primary source)

Read every page of the current live website. For every claim, headline, and proof point found, mark it **carry** (still true, keep as-is), **change** (needs updating — note why and to what), or **drop** (no longer true or no longer wanted). Build this into a checklist document (one row per claim) and get the owner to approve each **drop** explicitly — carries and routine wording changes don't need a ruling, but nothing gets removed from the record of what the company has claimed without the owner signing off.

Questions to the owner at the end of Stage 1: which drops are approved; any claims that read ambiguously; any naming inconsistencies found on the site (file these as a separate follow-up, not as part of this refresh — the refreshed hierarchy becomes the reference the site gets reconciled against, not the other way around).

### Stage 2 — What shipped since the last version

Read everything the company published since the last approved hierarchy: blog posts, release notes, and social posts from the company account and from the founder/CEO's personal account. Classify every item as **positioning** (changes how the product is described), **pillar** (supports or adds a messaging pillar), **proof point** (a stat, customer, or fact worth citing), or **omit** (doesn't affect messaging).

Questions to the owner at the end of Stage 2: does the pillar list still hold, or does something need adding, dropping, or reordering; any shipped feature that should become a top-line message; any feature name that changed.

### Stage 3 — Outside signals

Look outward: how do outside voices — analysts, partners, competitors, and commentators — describe the category and the company today? Note category-name candidates the market is using, whether they match or differ from the company's own category name, and which named companies in the space are genuine competitors versus adjacent partners versus irrelevant.

Questions to the owner at the end of Stage 3: does the category name still hold; which outside players are true competitors versus partners worth explaining rather than fighting; any new competitive angle the owner wants reflected.

### Stage 4 — Inside knowledge

Gather what only the inside of the company knows: current numbers with their source and date (a dashboard, a board deck, a usage metric — never a guess), the customer list verified against the CRM or system of record (not memory, not the old hierarchy), and the accumulated positioning knowledge of whoever owns positioning day to day (a head of marketing, a growth lead, a long-tenured salesperson) — their validated beliefs and their open hypotheses, kept separate.

Questions to the owner at the end of Stage 4: which numbers to use when sources disagree; which customer names are approved for public use today (a name being publicly usable in the old hierarchy proves nothing about today); anything from the positioning owner's input that needs a ruling.

Once all four stages are closed and logged, proceed to PHASE 2.

---

## PHASE 2: ESTABLISH HARD RULES

Before writing anything, surface the decisions that affect ALL downstream content. Ask the user (in one message):

1. **Language constraints**: Any words or phrases to always avoid or always use? (Examples: competitors avoid "cloud," enterprise companies avoid "AI-powered," etc.)
2. **Named customer rules**: Which customer names are approved for public use (web, press release) vs. internal/sales-only?
3. **Lead differentiator**: Of all the things you do, what's the ONE thing customers hit first — the #1 reason they pay you?
4. **The big vision**: In one sentence, what's the tectonic shift happening in the world that makes your product necessary?

Document the answers as a "Hard Rules" section in `LAUNCH.md`. These apply to every section of the template — enforce them when writing. Write the rules file as its own reviewable artifact (draft, get it approved, mark it FINAL) before any hierarchy section is drafted — nothing gets written into the hierarchy until the hard rules are closed.

The hard rules file must also cover:

- **Product-name / language-ban reconciliation.** A banned word can still appear inside an approved product name (for example, a general ban on a marketing word doesn't strip that word out of a proper-noun product name that happens to contain it). Write out every case where a product name and a language ban collide, and state which wins for that specific name. Don't leave the two rules to silently contradict each other.
- **A numbers rule.** List every figure the hierarchy is allowed to cite, each with its source and the date it was pulled. Mark any figure that rests on the owner's ruling (a judgment call, a rounding, a "use the better of these two documents") rather than on a document or dashboard — a sourced figure and a ruled figure are not the same kind of claim, and the reader of the rules file needs to see which is which.
- **A named-customer rule.** The exact list of customers approved for public use, plus the system used to verify each one (CRM, deal record, signed reference) and the date it was checked. A name is on the list because it was checked against that system today, not because it appeared in a prior version of the hierarchy.
- **A must-have capabilities rule.** If buyers raise a specific capability in most first conversations, that capability is stated early in every conversation about the product — even when competitors match it and it isn't a differentiator. A must-have earns the right to be in the room; the differentiators are what win the room once you're in it. The hard rules file must say this explicitly so it doesn't get buried or cut for sounding un-original.

---

## PHASE 3: FILL THE TEMPLATE — DEPENDENCY ORDER

Fill the messaging hierarchy one section at a time. Never skip ahead, and never let the owner see more than one section at a time — draft several sections in one working pass if that's faster for you, but present them to the owner **one at a time, in dependency order**, with approval on each before the next is shown. A batch of un-reviewed sections dropped on the owner at once defeats the point of sequential approval — early sections change the sections that depend on them.

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
5. After approval, save to the template file, log it in DECISIONS.md if the owner changed anything, and update `CHECKLIST.md` and `state.json`

If the user says "looks great, next" — move on. Don't re-ask or re-explain.

### What makes each section good

**Best-fit customer**: Be specific. Not "enterprise companies" but "mid-to-large enterprise (500+ employees) with existing [X] initiatives that have hit the wall between prototype and production." Include the exact buying trigger — the moment that sends them looking.

**Market category**: Name the category, then explain the category story. Add a "discovery hook" — the more familiar language the buyer searches for that leads them to you. This preserves existing brand awareness while broadening.

**Competitive alternatives**: Include all five types: (1) do nothing, (2) build it themselves, (3) direct competitors, (4) adjacent tools that partially solve it, (5) legacy/incumbent approaches. Most buyers don't "not buy" — they buy something else.

**Differentiated capabilities**: Mark the LEAD differentiator with ⭐. This should be the capability that (a) only you have, (b) solves the problem buyers hit first, and (c) is the primary conversion trigger. Reference the "Hard Rules" from Phase 2.

**One-line positioning**: Draft three distinct options, not one. A typical split: a full master line (for internal use and as the source the rest of the document assembles from), a short form (for a website hero or one-pager), and an opener suited to a sales conversation with a buyer who already knows the product. Present all three together and let the owner pick — or approve more than one for different uses.

**Galvanizing narrative**: This is the big idea. It has three parts:
- The Shift: What's changing in the world that makes this product necessary and urgent?
- The Problem: What breaks, fails, or gets stuck under the current approach?
- The Unlock: How does this product change the game?

The opening line should be vision-level — a declaration about the world, not a product pitch. If the user has a "big idea" phrase, it opens here. **Write two versions**: a public version (for the website, press release, and any external audience) and a sales version (for a seller talking to a live prospect, which can be more direct and can assume more context than a stranger has).

**Messaging pillars**: 3 is ideal. Each pillar: one-liner (outcome, not feature), explanation (2-3 sentences), proof points (feature → outcome → evidence → competitive angle). Lead with the outcome, not the feature.

**Proof point bank**: Split into categories: adoption stats, ecosystem proof, product facts, named customers. For named customers, ALWAYS document who is approved for public (web, PR) use vs. internal/sales-only, and the verification source. This prevents costly mistakes.

**Persona angles**: For each persona: what they own, their primary pain in their own words, the primary message for them, their top 2 pillars, and the objection to pre-empt.

**Competitive frame**: A landscape table (approach, limitation, how you're different), then ranked differentiators (1-3 max), then objection handling for the 4-6 most common objections. State any must-have capability from the Phase 2 hard rules early and plainly — never instruct the reader to hold it back or treat it as a lesser point; it's what earns credibility before the ranked differentiators do their work.

### Drafting rules that apply across every section

- **Flag every departure from the website inline, with its reason**, at the point in the document where the departure happens — not just in a single disclaimer at the top. Then summarize every flagged departure in one table at the end of the document (section, old wording, new wording, reason) so the owner can review them together.
- **Treat "no competitor has this" as an absence claim, and soften it.** You can state that you found no competitor with a given capability; you cannot state that none exists. Write "no competitor we found has this" or name the specific competitors checked, never a flat "no competitor has this."
- **Never write "M-by-N to M-plus-N"** (or any version of that construction) to describe a many-to-many integration. Say what actually connects to what — name the two sides and describe the connection directly.
- **Avoid month-to-month comparisons that make the reader do date math** ("as good in June as it was in January"). State the fact directly instead of asking the reader to compare two points in time themselves.
- **Mark every hypothesis from internal research as a hypothesis**, distinct from a validated finding — state its confidence level and what evidence would validate or kill it. Never present a hypothesis with the same confidence as a sourced fact.

---

## SCOPE OF THE DOCUMENT

The messaging hierarchy informs how everyone in the company talks about the product — sales conversations, the website, the deck, press materials. **It does not dictate the website or any other asset.** A logo or a claim that isn't on this document's approved list is simply not on the list — that is not an instruction to remove it from the website or anywhere else. The hierarchy is a reference for language and claims, never a change order for a different asset owned by a different team.

## VOICE

If the owner's organization uses a plain-language or simplified-English protocol for messages written *to* the owner, that protocol governs how the assistant talks to the owner during this project — status updates, questions, summaries. **It does not govern the hierarchy copy itself.** Positioning statements, narrative copy, and pillar language follow the VOICE & TONE DEFAULTS below, not a plain-language protocol built for internal status reporting.

## ORCHESTRATION

When this skill runs inside a multi-agent setup, the coordinating agent dispatches each research and drafting step — reading a website, pulling social posts, drafting a section — to a worker agent with a written brief and a specific output path, then reviews the worker's result before taking it to the owner. **The coordinator does not read whole websites, scroll through social feeds, or transcribe designs by hand** — that work goes to a worker agent so the coordinator's context stays free for judgment calls and owner conversation. Before driving any SaaS tool (a CRM, an analytics dashboard, a design tool, a docs site) by hand — clicking through a UI, screen-scraping a page — check whether an MCP server or API already exists for that tool and use it instead.

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
- In refresh mode: the departures-from-the-website summary table, called out clearly as its own appendix or section

Save the .docx to `deliverables/[ProductName]-Messaging-Hierarchy.docx`.

---

## PHASE 5: ESTABLISH RESUMABILITY

After completing the template and Word doc, update `LAUNCH.md`, `CHECKLIST.md`, and `state.json` to reflect:
- What's done (template complete, docx generated, checklist stages all closed)
- What's next (website copy, sales deck, press release, the next quarterly refresh, etc.)
- The editing workflow (edit the .md → note that docx needs regeneration)

Update `state.json` with all decisions made during the fill process, and confirm every decision logged there also appears in `DECISIONS.md`.

Tell the user: "This project is set up so any future session can pick up where we left off. Just trigger it with '[product name] launch messaging' and I'll read the project files and resume."

---

## ONGOING: EDITING WORKFLOW

When the owner (or any user) returns to update the messaging, the workflow is:
1. Read `LAUNCH.md` (resume instructions, hard rules) and `CHECKLIST.md` (where things stand)
2. Read `deliverables/messaging-hierarchy-template.md` (source of truth)
3. Make the requested edit in the .md file
4. Offer to regenerate the Word document
5. Log the change in `DECISIONS.md` and `state.json`

---

## VOICE & TONE DEFAULTS

These apply to hierarchy copy unless the user specifies otherwise (see the VOICE note above for the boundary between this and a plain-language protocol used for owner status updates):
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
- `references/checklist-template.md` — The CHECKLIST.md starting structure, with the stage/step marks and the DECISIONS.md log convention.

---

## CHANGELOG

- **2.0 — 02September2026**: Added the quarterly refresh mode (four discovery stages, each ending in owner questions, replacing Phase 1 when a prior approved hierarchy exists). Added `CHECKLIST.md` and `DECISIONS.md` as standing project files, and the `references/checklist-template.md` reference. Expanded Phase 2 hard rules with product-name/language-ban reconciliation, a sourced numbers rule, a named-customer verification rule, and a must-have-capabilities rule. Expanded Phase 3 with three-option positioning statements, public/sales narrative versions, inline+tabled departure tracking, absence-claim softening, a ban on the "M-by-N to M-plus-N" construction, a ban on month-to-month reader-math comparisons, and hypothesis confidence marking. Added SCOPE OF THE DOCUMENT, VOICE, and ORCHESTRATION notes.
- **1.0**: Initial release — from-scratch messaging hierarchy build, 11-step dependency-ordered fill, Word document generation.
