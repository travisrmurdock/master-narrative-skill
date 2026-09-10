---
name: launch-messaging
description: >
  Build or refresh a complete B2B product or company launch messaging hierarchy — positioning framework, galvanizing narrative, messaging pillars, proof points, persona angles, competitive frame, and elevator pitches. Has two modes: FROM SCRATCH (no prior hierarchy exists) and QUARTERLY REFRESH (a prior approved hierarchy exists and needs updating against what changed). Creates a persistent, resumable project folder with a running CHECKLIST.md and a dated DECISIONS.md decision log, and delivers a formatted Word document. Also handles the owner review cycle: fold in review comments after the owner marks up the delivered document, running an owner review that turns each comment into a tracked task and closes with independent verification. Use this skill whenever someone wants to: develop launch copy or positioning for a product, create or refresh a messaging framework or messaging hierarchy, work on go-to-market (GTM) messaging, write positioning for a new product or feature, build out value props and pillars, nail down their company narrative, create a press release foundation, develop sales messaging, run a periodic refresh of an existing messaging hierarchy, or fold owner review comments and tracked changes into the next draft. Also trigger this skill for "what's our big idea", "how do we talk about X", "positioning statement", "elevator pitch", "quarterly messaging refresh", "update our narrative", "owner review", "review cycle", "fold in review comments", or any request to work through how a company or product should communicate its value. Works for any B2B product — SaaS, infrastructure, developer tools, AI products, enterprise software.
---

# Launch Messaging Skill

**Version 2.2 — 10September2026.** Adds PHASE 7, building a short derived asset (a spoken sales messaging guide, a one-pager, a battlecard) from an approved hierarchy. Adds an audience QA step, where a reviewer who did not draft the document reads it as each named reader and gives a pass or fail per section. Adds owner-review-cycle rules for a reviewer who is not the owner, for a comment that belongs in the hierarchy as well as the asset, for a Google Docs round trip that can drop typed text, and for keeping a shared-drive link stable through an overwrite and a rename. Adds two orchestration rules: an instruction to a worker lives in that worker's brief file, and a script recount settles any disagreement between a worker's report and the file itself. See CHANGELOG at the bottom.

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

Read every page of the current live website. For every claim, headline, and proof point found, mark it **carry** (still true, keep as-is), **change** (needs updating — note why and to what), or **drop** (no longer true or no longer wanted). Build this into a checklist document (one row per claim) and get the owner to approve each **drop** explicitly — items marked carry, and routine wording changes, don't need a ruling, but nothing gets removed from the record of what the company has claimed without the owner signing off.

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
- **A one-feature-one-name rule.** Every feature keeps exactly one name everywhere it appears in the hierarchy and every downstream asset. A feature never gets a second name in parentheses next to the first, even when an internal team or an old document used a different name for the same thing — pick one and write out the rule that names which one and why.
- **Owner rulings on a number are final and go in the same day, everywhere.** When the owner rules on a number ("the total is X," "use this count, not that one"), write it into the hard rules file the moment it's given, and update every place in the hierarchy that already states that number — not only the one row or sentence the ruling was about. A ruled number silently left standing somewhere else in the document contradicts the rule the owner just gave.

---

## PHASE 3: FILL THE TEMPLATE — DEPENDENCY ORDER

Fill the messaging hierarchy one section at a time. Never skip ahead, and never let the owner see more than one section at a time — draft several sections in one working pass if that's faster for you, but present them to the owner **one at a time, in dependency order**, with approval on each before the next is shown. A batch of un-reviewed sections dropped on the owner at once defeats the point of sequential approval — early sections change the sections that depend on them.

**Critical**: Fill in dependency order, NOT by section number alone — though in this template the section letters (1a through 1f) already run in that order, because you can't identify true alternatives without first knowing WHO the buyer is. **The section labels always match the reading and fill order** — never letter a template section to match an older version's order or a prior template's layout; if a refresh reorders which question comes first, relabel the sections to match, and update every cross-reference to the old letter in the same pass. Use this order:

### The 11-Step Fill Order

| Step | Section | Why this order |
|------|---------|----------------|
| 1 | **Best-fit customer** (1a) | Everything filters through WHO. Alternatives, capabilities, and value all depend on who you're speaking to. |
| 2 | **Market category** (1b) | The buyer needs a mental shelf. Category determines how they evaluate alternatives. |
| 3 | **Competitive alternatives** (1c) | Now that you know WHO and what CATEGORY, identify true alternatives (not just named competitors — include "do nothing" and "build it themselves"). |
| 4 | **Differentiated capabilities + value** (1d + 1e) | Capabilities are only meaningful relative to the alternatives you just named. Value ties capabilities to outcomes the best-fit customer cares about. |
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

**Best-fit customer**: Be specific. Not "enterprise companies" but "mid-to-large enterprise (500+ employees) with existing [X] initiatives that have hit the wall between prototype and production." Include the exact buying trigger — the moment that sends them looking. **If the product has a free or open-source tier, name two buyers at two different moments**: the evaluator, before the first call or the proof of concept, and the buying committee, after the evaluator is interested. The evaluator wants something they cannot do on their own, or something that removes the unfun, undifferentiated work; the buying committee wants assurance that the foundation is right — compliance, risk, data residency — and that they are not paying for something the free tier already gives away. Give the evaluator the business language they need to carry the case to the committee. This split feeds directly into Section 1e (the paid-vs-free capability table) and the "why pay for free" row in Section 6c.

**Market category**: Name the category, then explain the category story. Add a "discovery hook" — the more familiar language the buyer searches for that leads them to you. This preserves existing brand awareness while broadening.

**Competitive alternatives**: Include all five types: (1) do nothing, (2) build it themselves, (3) direct competitors, (4) adjacent tools that partially solve it, (5) legacy/incumbent approaches. Most buyers don't "not buy" — they buy something else.

**Differentiated capabilities**: Mark the LEAD differentiator with ⭐. This should be the capability that (a) only you have, (b) solves the problem buyers hit first, and (c) is the primary conversion trigger. Reference the "Hard Rules" from Phase 2. **One feature, one name** — check every capability row against the hard rules' one-feature-one-name list; never give a feature a second name in parentheses next to the first, even if an older document or a different team calls it something else.

**Differentiated value**: Tie each capability to a concrete business outcome. **If the product has a free or open-source tier**, add the table naming exactly what the paid product does that the free tier cannot, with one column for each buyer named in the best-fit-customer section — what it means for the evaluator, and what risk or compliance question it answers for the buying committee. This table is what Section 6c's "why pay for what's free" objection points back to, so build it before drafting that objection row.

**One-line positioning**: Draft three distinct options, not one. A typical split: a full master line (for internal use and as the source the rest of the document assembles from), a short form (for a website hero or one-pager), and an opener suited to a sales conversation with a buyer who already knows the product. Present all three together and let the owner pick — or approve more than one for different uses.

**Galvanizing narrative**: This is the big idea. It has three parts:
- The Shift: What's changing in the world that makes this product necessary and urgent?
- The Problem: What breaks, fails, or gets stuck under the current approach?
- The Unlock: How does this product change the game?

The opening line should be vision-level — a declaration about the world, not a product pitch. If the user has a "big idea" phrase, it opens here. **Write two versions**: a public version (for the website, press release, and any external audience) and a sales version (for a seller talking to a live prospect, which can be more direct and can assume more context than a stranger has).

**Messaging pillars**: 3 is ideal. Each pillar: one-liner (outcome, not feature), explanation (2-3 sentences), proof points (feature → outcome → evidence → competitive angle). Lead with the outcome, not the feature.

**Proof point bank**: Split into categories: adoption stats, ecosystem proof, product facts, named customers. For named customers, ALWAYS document who is approved for public (web, PR) use vs. internal/sales-only, and the verification source. This prevents costly mistakes. **No proof table has its own Source or Date column.** Every row is numbered once; the number stays fixed for the life of the document; the source and date for every numbered row live in one "Sources" section at the end (see `references/messaging-hierarchy-template.md`). This keeps the bank itself readable while still making every claim traceable.

**Persona angles**: For each persona: what they own, their primary pain in their own words, the primary message for them, their top 2 pillars, and the objection to pre-empt.

**Competitive frame**: A landscape table (approach, limitation, how you're different), then ranked differentiators (1-3 max), then objection handling for the 4-6 most common objections. State any must-have capability from the Phase 2 hard rules early and plainly — never instruct the reader to hold it back or treat it as a lesser point; it's what earns credibility before the ranked differentiators do their work. **If the product has a free or open-source tier**, one objection row must be "why pay for what's free" — answer it by pointing to the paid-vs-free table in the differentiated-value section, not by re-arguing the case in this row.

### Drafting rules that apply across every section

- **Flag every departure from the primary source at the point where it happens**, with its reason in plain language, not a decision or rule number. Then list every flagged departure in one table at the end of the document ("Where this document differs from the website" or equivalent — see `references/messaging-hierarchy-template.md`), section / old wording / new wording / reason, so the owner can review them together. The departure table is the one place this content lives in the final document — remove the inline flags once the summary table is built, so the body reads cleanly for the reader (see "The document speaks to its reader" below).
- **Treat "no competitor has this" as an absence claim, and soften it.** You can state that you found no competitor with a given capability; you cannot state that none exists. Write "no competitor we found has this" or name the specific competitors checked, never a flat "no competitor has this."
- **Never write "M-by-N to M-plus-N"** (or any version of that construction) to describe a many-to-many integration. Say what actually connects to what — name the two sides and describe the connection directly.
- **Avoid month-to-month comparisons that make the reader do date math** ("as good in June as it was in January"). State the fact directly instead of asking the reader to compare two points in time themselves.
- **Mark every hypothesis from internal research as a hypothesis**, distinct from a validated finding — state its confidence level and what evidence would validate or kill it. Never present a hypothesis with the same confidence as a sourced fact. If the owner rules that a hypothesis is directionally true, rewrite it as a stated fact and remove the confidence score, the caveat about its source quality, and the "validate before building on this" instruction — an owner ruling retires the hedge, it doesn't just append to it.

### The document speaks to its reader, never to the team that wrote it

The finished hierarchy is read by people who never sat in on its drafting — a seller, a new hire, a partner. Nothing in the body should require having been in the room. Before every section is considered final, check it against this list and move anything that fails to the decision log or the project's own tracking files, never into the document itself:

- **No justification blocks.** A "Why:" paragraph, a research-reasoning aside, or a comparison of draft options belongs in `DECISIONS.md` or the research folder, not in the delivered document. The reader needs the adopted line, not the argument for it.
- **No decision or rule numbers in the body.** "(Decision 14)" or "(hard rule 7)" means nothing to a reader outside the project. If a sentence needs the fact that decision pointed to, write the fact directly; the citation itself stays in the decision log.
- **No names of the owner or the drafting team.** An aside like "as Name set" or "per [team member]'s research" is addressed to the room the document was drafted in, not to the reader. State the fact and drop the attribution — the one exception is a reader-facing metadata field (a document's own "Owner:" line) that names a real, on-the-record person as part of what the field is for.
- **No file paths.** A path from the machine or drafting environment that produced the document is never reader-facing. If the reader needs to find something, name the file and where the team keeps it (a shared drive, a wiki) in the REFERENCE section, not as an inline path in the body.
- **No warning blocks aimed at the writer.** A "⚠️" callout should carry operational content the reader needs (a usage rule, a status marker) — never a note reminding the writing team to re-check something before the next draft.
- **No inline "[deviation from the source: ...]" brackets in the body.** Track every departure in the one summary table at the end (see the drafting rule above); the body reads as finished copy, not as a marked-up draft.

### Audience QA

Before the pre-build check below runs, a reviewer who did not draft the section reads it as each reader the document names, the persona or personas that section speaks to, and writes one line per section per reader: pass, or fail with the reason and a rewrite. Check any reader-facing instructional text (how-to-use lines, section intros) against the plain-language protocol in the same pass, as its own pass-or-fail line, separate from the messaging pass-or-fail lines.

Run this check as its own pass before Phase 4 (document generation) begins — a "pre-build check" against every section, not only against the sections a comment happened to touch.

---

## SCOPE OF THE DOCUMENT

The messaging hierarchy informs how everyone in the company talks about the product — sales conversations, the website, the deck, press materials. **It does not dictate the website or any other asset.** A logo or a claim that isn't on this document's approved list is simply not on the list — that is not an instruction to remove it from the website or anywhere else. The hierarchy is a reference for language and claims, never a change order for a different asset owned by a different team.

## VOICE

If the owner's organization uses a plain-language or simplified-English protocol for messages written *to* the owner, that protocol governs how the assistant talks to the owner during this project — status updates, questions, summaries. **It does not govern the hierarchy copy itself.** Positioning statements, narrative copy, and pillar language follow the VOICE & TONE DEFAULTS below, not a plain-language protocol built for internal status reporting.

**The one place a plain-language protocol does reach into the document itself is its own instructional text** — the "How to use this document" section and every short section intro that tells the reader how to use what follows, as opposed to the messaging content those sections introduce. Format that instructional text as short, numbered steps (one instruction per line, not a run-on paragraph) and keep every section intro to two to four short sentences. This is a formatting and plain-language pass on the document's own stage directions; it never touches a positioning line, a narrative paragraph, a pillar one-liner, or any other piece of the messaging itself.

## ORCHESTRATION

When this skill runs inside a multi-agent setup, the coordinating agent dispatches each research and drafting step — reading a website, pulling social posts, drafting a section — to a worker agent with a written brief and a specific output path, then reviews the worker's result before taking it to the owner. **The coordinator does not read whole websites, scroll through social feeds, or transcribe designs by hand** — that work goes to a worker agent so the coordinator's context stays free for judgment calls and owner conversation. Before driving any SaaS tool (a CRM, an analytics dashboard, a design tool, a docs site) by hand — clicking through a UI, screen-scraping a page — check whether an MCP server or API already exists for that tool and use it instead.

**Worker agents never edit the coordinator's own checklist.** A worker marks its own row done in its task brief or its own change log, but the running project checklist (`CHECKLIST.md`, or an owner-review checklist under PHASE 6) is the coordinator's bookkeeping — only the coordinator opens, closes, or resets a row in it. If a worker finds its own row already marked done by mistake, it flags that to the coordinator rather than editing the file itself.

**Every instruction to a worker is written into that worker's brief file before, or at the moment, it is sent.** A message that exists only in chat, with no matching line in the brief, can be refused as untrusted, since the worker has no record it was actually asked for. When an instruction changes mid-task, write the change into the brief first, then send the worker a message naming the change plainly: "re-read the section named [X] in your brief."

**When a worker's report disagrees with the file it describes** (a word count, a page count, a line count), the checker recounts by script against the file itself, and the file wins. A worker's own report is a claim about the file, not a substitute for reading it.

---

## VOICE SCRUB — TWO PASSES, BEFORE PHASE 4

Run this scrub on the fully drafted document, after every section is approved and before the Word document is built. It removes the writing patterns a reader recognizes as AI-generated, distinct from the drafting rules above (which remove content that shouldn't be in the document at all) and from the plain-language pass on instructional text (which is a formatting change, not a voice change).

**Ban list, checked across the whole document:**
- Zero em dashes. Replace with a period, a comma, a colon introducing a list, or parentheses, depending on what the sentence needs — never leave one standing.
- No set-up-and-reveal constructions ("it's not X, it's Y," "what matters isn't X — it's Y"). State the fact directly.
- No dramatic one-line reveals ("That is the moment they come looking," "This is the big idea"). Fold the fact into the sentence around it instead of pausing for effect.
- No negative-list rhythm repeated across the document ("no history, no audit trail, no...", used the same way in multiple places). Keep the list form in the one place it earns its keep (usually a single objection-handling row); write the same fact as ordinary prose everywhere else it would otherwise repeat.
- No arrow labels ("Feature → Outcome") or bold "so that" connectors used as a structural device across every proof point. State what the capability does and what the reader gets in one sentence.
- No asides about the drafting process itself ("this refresh," "we found," "found in our research"). State the fact; drop the narration of how it was discovered.
- Colons are for introducing a list or a quotation only — never used to join two clauses for a dramatic pause. If a colon is doing that job, split it into two sentences or rejoin the clauses with "so" or "because."
- Check every question mark. A question inside quotation marks representing a real person's or persona's own words is fine, and a document's own template convention (an italicized subtitle question repeated under every subsection) is fine. A rhetorical question inserted as a transition device is not — rewrite it as a direct statement.

**Run this as two passes, not one.** The first pass, run against the ban list above, reliably catches punctuation-level patterns (em dashes) but tends to miss the sentence-shape patterns (reveals, litanies, arrow labels) because they don't show up in a simple search. After the first pass, sample the output across several sections — not just the first page — and check specifically for the sentence-shape patterns the first pass is prone to miss. If any remain, send them back for a second pass with the exact line numbers and the pattern each one matches; do not assume a first pass caught everything just because the mechanical checks (em-dash count, banned-word grep) come back clean.

**Paragraphs the owner has already approved verbatim in an earlier review get punctuation-only changes in this scrub** — fix an em dash or a stray colon, but do not reword a sentence the owner signed off on word-for-word, even if it technically matches a banned pattern. Note any such paragraph and the punctuation-only treatment in the change log.

---

## PHASE 4: GENERATE THE WORD DOCUMENT

After the template is fully approved and has been through the voice scrub above, generate a formatted Word document.

Read the docx skill at `/sessions/*/mnt/.skills/skills/docx/SKILL.md` for the exact generation approach.

**Build from the brand, not from a generic default.** Read the organization's own brand guide (fonts, colors, spacing) before choosing any styling value — never fall back to a generic font pair or an invented color that isn't in the brand's own palette. If the guide doesn't name a value this document needs (for example, a specific heading-accent color among several brand colors), pick one from inside the approved palette and say plainly in the design report that it's a judgment call, not a confirmed brand rule.

Key styling decisions to make with the user, all sourced from the brand guide:
- Brand accent color (hex code) — used lightly: a heading-underline rule, a table-header tint, never a heavy fill
- Body font and a monospace or secondary font if the brand guide names one
- Company/product name for header

The Word document should have:
- **11pt minimum body text.** This is a floor, not a target — check it against the brand guide's own type scale if the guide sets one.
- **Wide margins and natural paragraph spacing** (roughly 1.15-1.2 line spacing, visible space after each paragraph) so the page reads as designed, not compressed to fit more per page.
- A compact title block at the top of page one (title, version/status, subtitle) rather than a separate, mostly-empty cover page — a lone centered title on its own page is one of the fastest ways a document reads as a generic template.
- Branded, page-numbered running header and footer on every page, including page one.
- Tables with a light accent-color tint on the header row only, thin hairline rules, and enough column-width logic that a long unbroken value (a URL, an identifier) doesn't force every other column in the same table to collapse.
- **Tables wider than five columns do not fit a normal page at body-text size.** If a table needs more than five columns, move a column out — sources and dates belong in the end-of-document Sources section (see the drafting rules above), not in a proof-point table — rather than shrinking the type below the 11pt floor to force it to fit.
- Blockquote styling for narrative sections.
- Callout boxes for hard rules and usage warnings (e.g., named customer rules), carrying only reader-facing operational content — no note addressed to the writing team (see "The document speaks to its reader" above).
- In refresh mode: the departures-from-the-source summary table, called out clearly as its own section near the end.

Save the .docx to `deliverables/[ProductName]-Messaging-Hierarchy.docx`.

**Before delivering, render the document to PDF and look at the actual pages** — not just the source markdown or the docx XML. Check at minimum: the title page, a page with a wide table, and any page a recent change touched. Confirm no table overflows the page width, no word wraps mid-token, and the page reads as designed rather than merely as "no error was thrown." A document that builds without an error and a document that looks right on the page are not the same check.

---

## PHASE 5: ESTABLISH RESUMABILITY

After completing the template and Word doc, update `LAUNCH.md`, `CHECKLIST.md`, and `state.json` to reflect:
- What's done (template complete, docx generated, checklist stages all closed)
- What's next (website copy, sales deck, press release, the next quarterly refresh, etc.)
- The editing workflow (edit the .md → note that docx needs regeneration)

Update `state.json` with all decisions made during the fill process, and confirm every decision logged there also appears in `DECISIONS.md`.

**If the team keeps a shared drive folder the wider organization can reach**, the deliverable and the files that support it live there too, laid out this way:
- The shared folder sits next to the document, with one sub-folder per version (for example, "Version 1.0" and "Version 2 - [current period]") — never one flat folder mixing every version's files together.
- A byte-for-byte mirror of the shared folder's contents lives in the project folder (the folder this skill's own files live in), so the project stays self-contained even if the shared drive is unreachable.
- Files internal to the drafting team only — briefs, scripts, raw research exports, `state.json`, `CHECKLIST.md` — stay out of the shared folder. Only what the wider organization needs to read or reference goes there: the hierarchy document itself, the hard rules, the decision log, and the source materials a reader might reasonably want to check.
- After any edit that changes a file already in the shared folder, overwrite that file in place (write new content into the existing file, never delete and re-create it) so a link someone already has to it keeps working.

Tell the user: "This project is set up so any future session can pick up where we left off. Just trigger it with '[product name] launch messaging' and I'll read the project files and resume."

---

## PHASE 6: OWNER REVIEW CYCLE

This phase runs whenever the owner has reviewed a delivered document and left comments or tracked changes in it — a normal part of getting a document approved, distinct from the quarterly refresh (which starts from what changed in the world) or an ad hoc edit request (which starts from a single instruction). Run it as its own phase, in its own dated folder, every time a reviewed copy comes back.

### 1. Bring the reviewed copy in

Copy the file the owner reviewed into a dated `review-[date]/` folder inside the project. Keep the original delivered version and the owner's reviewed copy both, so the extraction step below can diff them.

### 2. Extract every comment and edit verbatim

Word's `.docx` format is a zip archive. Write or reuse a small script (using only a zip/XML standard library, no special dependency) that:
- Unzips both the original and the reviewed file.
- Parses the reviewed file's `word/comments.xml` for every comment: id, author, date, full text.
- Parses `word/commentsExtended.xml` for thread linkage (a reply to another comment) and resolved/open state, where the format provides it.
- Walks `word/document.xml` to capture the anchored text for each comment and every tracked-change insertion or deletion, in document order.
- Separately diffs the finalized (post-tracked-change) plain text of every paragraph in both files, independent of Word's own tracked-change markup — a reviewer sometimes edits text without leaving Word's tracked-change layer engaged, and a diff catches what tracked-change parsing alone would miss.
- Assigns each comment and edit to the nearest section heading, so later steps can group work by document section.

Save this script inside the project (not only run once and discarded) so the next review cycle can reuse it. State plainly anything the script could not resolve (an ambiguous thread link, an unmatched heading) rather than guessing silently.

Produce one extraction document listing every comment and every edit, verbatim, with no interpretation or ranking added at this stage — the next step turns them into decisions and tasks, but the extraction itself is a faithful record of what the owner wrote.

**A file reviewed in Google Docs and downloaded back as a `.docx` keeps every comment but can drop typed text the reviewer added directly in the body.** When a reviewer says they added a passage and the extraction finds no new body text, check the comments before concluding nothing was added: the addition is usually written inside a comment instead. Treat that comment as the request itself, and say plainly in the decision log that the addition came from a comment, not from a tracked change in the body.

### 3. Record every ruling before any editing starts

Before a single word of the document changes, turn every comment into a numbered, dated decision in `DECISIONS.md`, in the reviewer's own words where possible. This is the same discipline PHASE 0 and PHASE 2 already require for every other ruling — a review comment is a ruling like any other, and nothing downstream should require the reviewer to repeat what they already said in the file.

**A review can come from someone other than the project's owner:** a CTO, a sales leader, another named reviewer the owner asked to weigh in. Every comment from that reviewer still becomes its own numbered decision, quoted verbatim, with that reviewer's name attached, so a reader of the decision log can tell whose ruling it was. Before any of that reviewer's comments become tasks, log the owner's own instruction for how to treat them (adopt every one, treat them as input to weigh against the owner's own view, and so on) as the first decision of the cycle.

### 4. When the reviewed document is a derived asset, check the hierarchy too

A comment on a derived asset (see PHASE 7) can raise a message the asset states but the hierarchy has never captured. For every such comment, search the hierarchy for the concept the comment raises, not for the comment's exact words, because the hierarchy may already hold the same idea in different wording. If the concept is genuinely absent, add the same message to the hierarchy, in the sections a seller or a marketer would look for it, as a new DRAFT version of the hierarchy, in this same review cycle rather than a separate one.

### 5. Build a review checklist that maps comment to task to owner

One row per comment or edit: what the reviewer said (short form), which decision number it became, which task will resolve it, and which agent or person owns that task. If several comments point at the same underlying issue (for example, three separate comments that all bear on one paragraph's wording), it is fine for one task to resolve all of them — say so in the row rather than duplicating the task.

If the project runs as a multi-agent setup and the owner asks for the standing orchestration reminder ("the coordinator dispatches, it does not do the work itself"), put that sentence at both the top and the bottom of the checklist, so it is visible whichever end of the list is read first.

### 6. Run the tasks in dependency order

Content-meaning changes first (anything that changes what a sentence claims or argues), then reader-facing cleanup (removing asides, justification, and internal citations per "The document speaks to its reader" above), then the voice scrub (both passes, per the VOICE SCRUB section above), then the document build (PHASE 4), then audience QA (see PHASE 3's audience QA step, run against the rebuilt document, one pass-or-fail line per section per named reader), then independent verification (step 7 below), then a fix batch for whatever verification finds, then re-verification of just the fixed items. Running cleanup before the meaning changes settle, or the voice scrub before cleanup, means redoing work once the earlier step lands.

### 7. Verify independently, against every comment

Assign this check to whoever did none of the drafting or cleanup work on this cycle. For every comment and edit in the extraction, the reviewer confirms pass or fail against the actual current document, with the exact evidence (a line number, a grep result, a rendered page) — never a restatement of what the task's own change log claims was done. A reviewer who only reads the change logs is auditing the work's own self-report, not the work.

Report the result as one line per item: pass, fail, or a judgment call flagged for a ruling, each with its evidence. Route every fail to a fix batch, apply the fixes, then re-run only the checks that failed — not the whole list again, unless the fix could plausibly have touched something else.

### 8. Overwrite in place; stay DRAFT until told otherwise

When the fixed document replaces a copy that already lives in a shared folder (per PHASE 5), overwrite that file in place rather than deleting and re-uploading it, so a link the owner or the team already has to it keeps working. Overwrite first, then rename the file to its new version name, in that order, so the file id, and the link built on it, never changes. Confirm the file id through the shared-drive connector after the rename rather than assume a desktop sync attribute proves the file is current. That attribute is not always present. Tell the owner plainly that the reviewers' links did not change.

**The delivered version number is the reviewed version number plus one.** Internal draft numbers used between passes while the cycle is still running are never printed on the delivered document; only the version the reviewer saw, and the version now delivered, are reader-facing numbers.

**The document's status line returns to DRAFT the moment a review cycle opens, and its version number increments, whatever the status was before the review.** A document that was APPROVED going into a review cycle is not APPROVED again until the owner explicitly says so for this new version — an owner's comments on a document do not carry its old approval forward. Reflect the new version and status in the file name as well as the header (version, status word, and date all in the file name), so a reader can tell which state a copy is in without opening it.

---

## PHASE 7: DERIVED ASSETS

This phase runs when a short asset needs to be built from an already-approved hierarchy: a spoken sales messaging guide, a one-pager, a battlecard. Run it after PHASE 5 closes. A derived asset is built from an approved hierarchy, never from one still in draft.

### 1. The hierarchy is the only source of numbers and names

The asset cites nothing the hierarchy does not already hold. When the asset needs a fact the hierarchy does not have (a services offer, a proof-of-concept motion, support terms), research it first, from contracts and internal playbooks, and write down that fact's source and date alongside it. Take that research to the owner only for what the files do not answer. Do not ask the owner to confirm something already sourced.

### 2. Composable blocks

Every block in the asset stands alone and can be spoken in any order; no block depends on another being read first. Time every block for speech at 150 words a minute and print that time on the block. Open each block with a line the seller says out loud. Close every block, except the one block described below, with one line stating why a free or open-source tier alone cannot do this, without naming the paid product. Name the paid product in exactly one block: the answer to a direct question about it.

### 3. Reader instructions follow plain language; the messaging itself does not

Anything in the asset that tells the reader how to use it, a "how to use this" line, a heading, a footer, follows the plain-language protocol: short sentences, one instruction per line, every acronym spelled out once, nothing left for the reader to decode. The messaging lines the seller speaks keep the hierarchy's own voice and are not bound by that protocol.

### 4. Set the page budget in lines, before drafting

Decide the page budget in printed lines, not words, before the first draft starts. Report "lines over" on every build once that limit is set. When a build runs over, work in this order, before cutting any spoken content: shorten table cells so every row prints on one line, set list items to one printed line each, merge short bullet lists into a paragraph, and put the running footer on one line. Cut spoken content last, and never cut the lines that do the asset's job: the ask for the next meeting, a fact the owner ruled on, or an addition a reviewer asked for.

### 5. Check page fit before the voice scrub and the audience QA

Check page fit right after the first draft, before the voice scrub (see the VOICE SCRUB section above) and the audience QA below run. Checking fit last means both the scrub and the QA run twice: once on text that does not fit, and again after it is cut down to fit.

### 6. Word counts come from a script, not a hand count

Produce every word count in a draft with a script, never by typing a count by hand. A hand-typed count can drift from the true count and cost a fact-check round redone for nothing.

### 7. Audience QA

A reviewer who did not draft the asset reads it as each named reader in turn. For a sales asset, that means the buyer, the technical person beside them on the call, and the seller who has to say it out loud. The reviewer writes one line per section per reader: pass, or fail with the reason and a rewrite. Give the asset's reader instructions their own plain-language pass or fail, one line per instruction, separate from the messaging pass-or-fail lines.

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

- **2.2 — 10September2026**: Added PHASE 7, building a short derived asset (a spoken sales messaging guide, a one-pager, a battlecard) from an approved hierarchy: the hierarchy as the only source of numbers and names, with any missing fact researched and sourced before it reaches the owner; composable blocks timed for speech, each closing with an unnamed moat line except the one block that names the paid product; reader instructions in plain language while the messaging itself keeps the hierarchy's voice; a page budget set in lines before drafting, with a fixed cutting order that protects spoken content last; page-fit checked before the voice scrub and the audience QA; and word counts produced by script rather than typed by hand. Added an audience QA step (a reviewer who did not draft the document reads it as each named reader and gives a pass or fail per section, with reader instructions checked separately against the plain-language protocol) to PHASE 3 before the pre-build check, to PHASE 6's dependency order after the document build, and to PHASE 7. Added to PHASE 6: a rule that a review can come from someone other than the owner, with the owner's own instruction for weighing that reviewer's comments logged first; a step checking whether a comment on a derived asset belongs in the hierarchy too, searched by concept rather than by exact wording; a caveat that a Google Docs round trip through `.docx` can drop typed text while keeping every comment, so an addition with no matching body text is usually sitting inside a comment instead; and a Drive-overwrite order (overwrite in place, then rename, then confirm the file id through the connector) that keeps a reviewer's link stable, plus a rule that the delivered version number is the reviewed number plus one. Added two ORCHESTRATION rules: every instruction to a worker is written into that worker's brief before or when it is sent, and a script recount against the file settles any disagreement between a worker's report and the file itself. Added a Stage 9 (derived asset) block to `checklist-template.md` and a note on Stage 8 that a reviewer other than the owner runs through the same shape.
- **2.1 — 08September2026**: Added PHASE 6, the owner review cycle (extract every comment and tracked change verbatim with a reusable script, log each as a decision before editing, build a comment-to-task-to-owner checklist, run fixes in dependency order, verify independently against every comment, overwrite the shared copy in place, reset status to DRAFT and increment the version on every cycle). Added "The document speaks to its reader, never to the team that wrote it" drafting rules and a pre-Phase-4 check for justification blocks, decision/rule numbers, drafter names, file paths, writer-facing warnings, and inline deviation brackets. Sharpened VOICE to name the one instructional-text exception to the messaging/plain-language split, with numbered steps and two-to-four-sentence section intros. Added a two-pass VOICE SCRUB phase (em dashes, set-up-and-reveal, dramatic reveals, repeated negative lists, arrow labels, drafting-process asides, colon reveals, question marks) with a punctuation-only carve-out for paragraphs already approved verbatim. Rewrote PHASE 4 to build from the organization's own brand guide first, with an 11pt body floor, natural spacing, a light single accent color, a five-column table limit, and a mandatory rendered-PDF check before delivery. Renumbered the messaging hierarchy template's Section 1 into reading order (best-fit customer, market category, alternatives, capabilities, value, positioning statement) and updated PHASE 3's fill order to match. Added a two-buyer pattern (an evaluator before the first call, a buying committee after) for products with a free or open-source tier, with a paid-vs-free capability table and a matching objection row. Added a one-feature-one-name hard rule and a same-day, everywhere-the-number-appears rule for owner-ruled figures. Moved proof-point sources and dates out of every table into one end-of-document Sources section. Added a shared-folder layout to PHASE 5 (one sub-folder per version, a byte-for-byte project-folder mirror, internal-only files excluded, overwrite in place). Added a rule to ORCHESTRATION that a worker agent never edits the coordinator's own checklist. Added a "reviews" entry shape to `state-json-template.json` and a Stage 8 (owner review cycle) block to `checklist-template.md`.
- **2.0 — 02September2026**: Added the quarterly refresh mode (four discovery stages, each ending in owner questions, replacing Phase 1 when a prior approved hierarchy exists). Added `CHECKLIST.md` and `DECISIONS.md` as standing project files, and the `references/checklist-template.md` reference. Expanded Phase 2 hard rules with product-name/language-ban reconciliation, a sourced numbers rule, a named-customer verification rule, and a must-have-capabilities rule. Expanded Phase 3 with three-option positioning statements, public/sales narrative versions, inline+tabled departure tracking, absence-claim softening, a ban on the "M-by-N to M-plus-N" construction, a ban on month-to-month reader-math comparisons, and hypothesis confidence marking. Added SCOPE OF THE DOCUMENT, VOICE, and ORCHESTRATION notes.
- **1.0**: Initial release — from-scratch messaging hierarchy build, 11-step dependency-ordered fill, Word document generation.
