# [Product Name] — Checklist

**Rule: this checklist is updated before the project moves to the next step, every time.** Whoever starts a step reads this file first. Update it when a step opens, when a step closes, and when the owner rules on a question. Dates are DD Month YYYY (e.g. 02 September 2026).

**Legend:** `[x]` done · `[ ]` open · `[~]` in progress · `[!]` waiting on the owner

Every ruling the owner gives, at any stage, is written into `DECISIONS.md` the moment it is given — numbered sequentially, dated, in the owner's own words where possible. This file tracks *what stage things are in*; `DECISIONS.md` tracks *what was decided and why*. Neither file substitutes for the other.

---

## Stage 0 — Setup
- [ ] Project folder created, `LAUNCH.md` filled in
- [ ] Source materials gathered (from-scratch mode) or prior approved hierarchy located (refresh mode)
- [ ] `DECISIONS.md` started — every owner ruling goes there the moment it's given
- [ ] Mode confirmed in `state.json`: `from_scratch` or `quarterly_refresh`

*(From-scratch mode: skip to Stage 1' below. Quarterly refresh mode: run Stages 1–4 in order.)*

## Stage 1' — Phrase library (from-scratch mode only)
- [ ] Every source material read, phrases extracted → `research/language-lexicon.md`
- [ ] Gaps and strongest existing language summarized to the owner

## Stage 1 — The current website (refresh mode, primary source)
- [ ] Website read, every page, every claim logged with a source
- [ ] Every claim marked carry / change / drop
- [ ] Owner approved every drop
- [ ] Questions to the owner answered, logged in `DECISIONS.md`

## Stage 2 — What shipped since the last version
- [ ] Blog posts, release notes, and social posts (company + founder) read
- [ ] Every item classified: positioning / pillar / proof point / omit
- [ ] Questions to the owner answered, logged in `DECISIONS.md`

## Stage 3 — Outside signals
- [ ] Outside voices, partners, and competitors surveyed for how they describe the category today
- [ ] Category-name candidates listed
- [ ] Questions to the owner answered, logged in `DECISIONS.md`

## Stage 4 — Inside knowledge
- [ ] Current numbers gathered, each with a source and a date
- [ ] Customer list verified against the CRM or system of record
- [ ] Positioning owner's accumulated knowledge captured — validated beliefs and open hypotheses kept separate
- [ ] Questions to the owner answered, logged in `DECISIONS.md`

## Stage 5 — Hard rules (skill Phase 2)
- [ ] Hard rules drafted, including: language constraints; named-customer rule with verification source and date; numbers rule with source/date per figure and a mark for any figure resting on a ruling rather than a source; product-name/language-ban reconciliation; must-have-capabilities rule
- [ ] Owner approved the hard rules
- [ ] Hard rules saved as FINAL — nothing is written into the hierarchy until this stage is closed

## Stage 6 — Fill the hierarchy (skill Phase 3, 11 steps in dependency order)
Each step: draft → review against `DECISIONS.md` and this checklist → owner approves → saved to `deliverables/messaging-hierarchy-template.md` → `state.json` updated.
- [ ] 1. Best-fit customer (1d)
- [ ] 2. Market category (1e)
- [ ] 3. Competitive alternatives (1a)
- [ ] 4. Differentiated capabilities and value (1b, 1c)
- [ ] 5. One-line positioning (1f) — three options presented
- [ ] 6. Galvanizing narrative (2a–2d) — public and sales versions
- [ ] 7. Messaging pillars (3)
- [ ] 8. Proof point bank (4)
- [ ] 9. Persona angles (5)
- [ ] 10. Competitive frame and objections (6)
- [ ] 11. Asset mapping and elevator pitches (7, appendix)

## Stage 7 — Deliverables (skill Phases 4 and 5)
- [ ] Voice scrub complete (skill VOICE SCRUB section), two passes: mechanical patterns (em dashes) first, then a sampled re-read for sentence-shape patterns (reveals, negative litanies, arrow labels)
- [ ] Word document generated from the approved markdown, built from the organization's own brand guide, rendered to PDF and looked at page by page before delivery
- [ ] Deliverable copy filed wherever the owner keeps launch documents; link recorded in `LAUNCH.md`
- [ ] Departures from the primary source listed in one section of the document, each with its reason, plus the summary table
- [ ] `LAUNCH.md`, `CHECKLIST.md`, and `state.json` updated for the next refresh

## Stage 8 — Owner review cycle (skill Phase 6, runs whenever a reviewed copy comes back)

Each task below maps to one comment or edit in the review extraction; the exact task names, owners, and count depend on what the review contains. This is the standing shape, not a fixed list.

- [ ] **T1 — Bring in the reviewed copy and extract.** Copy the owner's marked-up file into a dated `review-[date]/` folder. Run (or write, if this is the first cycle) the comment-and-tracked-change extraction script; save a copy of the script in the project. Produce a verbatim extraction document — no interpretation added yet.
- [ ] **T2 — Log every ruling.** Every comment and edit becomes a numbered, dated entry in `DECISIONS.md`, in the owner's own words where possible, before any editing starts.
- [ ] **T3 — Build the review checklist.** One row per comment/edit: what the owner said, the decision number, the task that resolves it, and who owns that task.
- [ ] **T4 — Content-meaning changes.** Whatever task(s) the checklist assigns to changes in what the document claims or argues. Runs first — everything after this depends on the meaning being settled.
- [ ] **T5 — Reader-facing cleanup.** Remove asides, justification blocks, decision/rule numbers, and file paths from the body per "The document speaks to its reader" (skill PHASE 3). Runs after T4 closes.
- [ ] **T6 — Voice scrub.** Both passes, per the skill's VOICE SCRUB section. Runs after T5 closes.
- [ ] **T7 — Document build.** Rebuild the Word document from the scrubbed markdown (skill PHASE 4); render to PDF and check the pages. Runs after T6 closes.
- [ ] **T8 — Independent verification.** An agent or reviewer who did none of T4–T7's work checks every item in the review checklist against the actual rebuilt document, pass/fail with evidence, not against the tasks' own change logs.
- [ ] **Fix batch.** Every fail from T8 gets fixed, then only the failed checks are re-run — not the full list — unless a fix could plausibly have touched something else.
- [ ] **Overwrite in place.** The rebuilt files replace the prior version in the shared folder (skill PHASE 5) by overwriting the existing file path, not deleting and re-uploading, so an existing link keeps working.
- [ ] **Status and version reset.** Header status returns to DRAFT (whatever it was before this cycle) and the version number increments; the new version, status, and date all appear in the file name. The document stays DRAFT until the owner says otherwise.

---

## Standing rules for every step
- The primary source (the live website, or whatever the hard rules name) is authoritative; any deviation is flagged with its reason. The hierarchy informs how everyone discusses the product; it never dictates changes to the website or any other asset.
- Named customers appear in public copy only if verified against the system of record today.
- Every number cites its source and date, and every source/date lives once, in the end-of-document Sources section — never in a proof-point table itself.
- Nothing is written into the hierarchy until the discovery stages and the hard rules stage are closed.
- Agents do not edit this checklist. A worker marks its own task's row done in its own brief or change log and tells the coordinator; only the coordinator opens, closes, or resets a row here.
