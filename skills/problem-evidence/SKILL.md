---
name: problem-evidence
description: Use when asking how solid the evidence is behind a candidate problem or statement, what evidence is missing, or what the cheapest next evidence would be ('how solid is the evidence behind P-003?', 'what are we missing for P-001?'). Not for finding new problems in raw material — use problem-discovery.
---

# problem-evidence

Grades the evidence behind a card on the evidence ladder (non-Cagan), sets its confidence, finds the gaps and names the cheapest next piece of evidence. It answers one question: is the evidence good enough to frame this problem now, or must the framing carry flagged assumptions? It never asks whether the problem is worth solving, and it never blocks the user from moving on (frame fast, never gatekeep).

## When to use

- A card (or several) needs its evidence graded: "how solid is the evidence behind P-003?", "grade the evidence on our shortlisted problems", "what evidence are we missing for P-001?".
- A statement is about to be written or reviewed and the user wants to know how well the problem behind it is supported.
- Discovery has left the card's `evidence_grade` marked `(provisional)` and its Evidence section `_Pending_`.

## When not to use

- Looking for problems nobody has named in notes, tickets or data: use problem-discovery. Evidence in `inputs/` that a card does not cite is not added here; name it as a gap and point to discovery's incremental mode.
- Judging a problem statement's wording (problem-review), choosing what to pursue (problem-focus) or sizing (opportunity-sizing). This skill never ranks, sizes or says a problem is worth solving.
- Testing a solution, a prototype or an assumption about one. That is solution discovery, outside this plugin.

## Inputs

- The card or cards: IDs named in the request ("P-003"), "the shortlisted problems" (every card with `status: shortlisted`), or "all" (every card). A statement `statements/P-NNN.md` means its card `P-NNN`. A request that names nothing: grade every card whose Evidence section is still `_Pending_`, and say which.
- Each card's Observations table is the evidence. Open a cited input file only to check a quote or to count distinct sources the card leaves unclear. `context.md`, when it exists, is business context.
- Do not stop to ask for missing evidence: it becomes a gap and a verdict, not a stop.

## Steps

### 1. Locate the workspace (problem-workspace → Locate)

Follow Locate in problem-workspace. No workspace and the user declines one, or says not to save anything: **chat-only**. The first output line is `> **Chat-only mode:** nothing is being saved.` Give the same content in the conversation, write no file or folder anywhere, and stay chat-only until the user asks to save or to create a workspace (Locate step 3). A card the user pastes is graded the same way.

### 2. Read the card, not its problem line

Read the whole card. **The problem line, the Interpretation and the front-matter are claims, not proof**: discovery sometimes words the problem line more broadly than its observations. Grade what the Observations rows show. Check each element of the problem line against them: who (a group, or one person), the situation, any quantity, any cause. Count distinct sources, not mentions or rows, and only sources whose rows show the claim being counted (a source silent on it, or showing the opposite, is not one): one account filing many tickets is one source; a second-hand mention ("my neighbour gave up") is weaker than a first-hand one. Look for a counter-case (a row where the same thing did not happen). Do not trust the card's `distinct_sources`, `evidence_grade` or `confidence`; recompute them.

### 3. Build the Evidence table, seeded from Observations

One row per claim the card makes, in this form (the header is exactly this):

```
| Claim | Evidence | Insight type | Ladder rung |
|---|---|---|---|
```

- **Claim:** a statement the card relies on: who has the problem, the situation, the unmet need, and any reach, frequency, severity or cause it asserts. Take them from the problem line, then from Interpretation and `quick_size`.
- **Evidence:** the Observations that show it, by Source and Location, with at most a short fragment copied exactly from the Verbatim cell. Every Observations row appears in some row's Evidence. A claim no row shows gets no table row: it goes under **Gaps** (see *A claim with no evidence* below); never invent a quote, a count or a figure. Any count, share or comparison in a cell is either read off a row or input (name the file and location) or derived with its arithmetic and inputs shown inline ("3 of 5 interviews: B, C, E"), and is re-checked against the input before it is written. A quantity the card does not support stays `[unknown: flagged]`.
- **Insight type:** one of `customer`, `data`, `business` or `market`: the four kinds of deep knowledge (`insight-sources.md`). First-hand or reported experience of the people affected is customer; counts, analytics and exports are data; stakeholder, strategy, constraint or economics views are business; competitors, trends and analysts are market.
- **Ladder rung:** one rung per row, copied exactly from the ladder table in `${CLAUDE_PLUGIN_ROOT}/references/evidence-ladder.md`. Grade the type of evidence, not how loud it is. A stakeholder or executive statement, and a feature request, is `others' opinions`, whatever its seniority or repetition. The author's belief, or a claim with no evidence, is `self-conviction`. A user's own estimate is `estimates and plans`. A few quotes or tickets, from fewer than three distinct sources, is `anecdotal evidence`; several distinct people, or a systematic sample or data that shows the problem, is `user/customer evidence` (a plugin judgement: say the count). Competitor or analyst facts are `market data`. Never claim `test results` or `launch data` at problem stage unless the card cites a real experiment or release.
- **A claim with no evidence** has no table row, so no rung is invented for it (never `none yet` or `—`); write it under **Gaps** as `**Assumption:** …` with what would confirm it, and let the rows that do have evidence set the grade.
- **An Observations table with no rows** (a hand-made card, or one whose rows were removed): write the table header with no rows, list every claim of the problem line under **Gaps** as `**Assumption:** …`, set `evidence_grade: self-conviction`, `confidence: very-low`, and give the verdict `frame with flagged assumptions`. Say in the reply that the card cites nothing and that the cheapest next evidence is the first observation to add.

### 4. Set the grade and confidence

Take the highest rung present in the table. Front-matter `evidence_grade` is that rung's name, copied exactly, **without** `(provisional)`. `confidence` is that rung's band from the ladder, no higher: it must equal the band of the highest Ladder rung in the table. A rung only counts when a row shows it. Low confidence is a flag, not a stop.

### 5. Find the gaps across the four kinds

Always name one gap line per kind, even when the kind is well covered (then say what is still missing, or "nothing material"):

- **Customer:** who is missing (non-users, people who left, other segments), the pains and how they decide, where it does not occur.
- **Data:** how often, how many accounts or people, trend: written `[unknown: flagged]`, never estimated.
- **Business:** the objective or focus it serves (`context.md`), the stakeholders, constraints, economics and legal limits.
- **Market:** how competitors or the industry handle it, trends, analysts.

### 6. Name the cheapest next evidence

One source or step, the one that would most change the grade or the verdict: who to ask, which data to pull, which people to reach. It is a way to get evidence about the problem, not a prototype or a test of a solution. Give a timebox as one whole number of days, written `timebox: 3 days` (a plugin default of 1 to 5 days; if the cheapest step takes longer, name a smaller first step). The card and the reply carry the same number: no range, no "up to" or "ceiling". State what would raise the band. Do not estimate effort, cost, revenue or the size of the problem.

### 7. Give the verdict

One line, exactly one of these (readiness to frame, never worth):

`Evidence verdict: ready to frame | frame with flagged assumptions`

- `ready to frame`: the claims that define the frame (who, the situation, the unmet need) each have a first-hand row at `anecdotal evidence` or above, at least one row is `user/customer evidence` or `market data`, and the business context (the objective or focus it serves) is known. Unknown reach, frequency or cost is a gap to list; on its own it does not block this verdict.
- `frame with flagged assumptions`: anything else, including a defining claim that rests only on an **Assumption:** under **Gaps** (no table row), `self-conviction` or `others' opinions`. List the assumptions that carry the frame, each labelled **Assumption:**. A stakeholder-origin card with no data always gets this verdict.

The verdict never says "not ready", never drops a card and never changes its `status`. A card with weak evidence stays on the backlog; it is not demoted, not marked not-now and not ranked below another. Grades are reported in ID order, never best first.

### 8. Write (workspace mode)

Cards are append-only: touch only the lines below. Use Edit with the exact line as `old_string`, not a rewrite of the file.

1. **Card body:** in `## Evidence`, replace the single line `_Pending: run problem-evidence._` with, in this order: the table; a `**Gaps**` list with the four kinds; one line `**Cheapest next evidence:** <step> (timebox: <N> days)`; the assumptions (if any); the verdict line last. Change no other body line. Never delete or edit the Observations.
2. **Front-matter:** `evidence_grade` (no `(provisional)`), `confidence`, `updated` (today). Correct `distinct_sources` only when Step 2's count differs, and say so in the History line. Never change `status`, `origin` or the problem.
3. **History:** append `- YYYY-MM-DD evidence graded by problem-evidence: <rung>, <band>, <verdict>`.
4. **Backlog:** update that card's Confidence cell to the new band when it changed (the table is living). Leave Status and every other cell.
5. **Manifest** (`workspace.md`): set `updated`, move `stage` to `identify` if it is `foundation`, add 1 to `checkpoints_since_decision`, and set the next-step line to this reply's suggested step. Grading is not a decision, so the Decision log gets no line.

A card whose Evidence section already holds a table was graded before. Do not rewrite it. Report its grade; if Observations rows were added since, append a `### Re-grade — YYYY-MM-DD` block under `## Evidence` with a new table for the new rows, the gaps, and a verdict line, and set the front-matter from the highest rung across both tables.

## Output

- Workspace mode: the edits above on each graded card, the backlog Confidence cell, the manifest. Chat-only: the same content in the conversation after the notice line; nothing written.
- Reply, per card (ID order): the grade and band, the Evidence table, the four gaps, the cheapest next evidence with its timebox in days, the assumptions and the verdict line. For several cards, add a roll-up table (ID, grade, confidence, verdict, cheapest next evidence), in ID order. Say which problem-line claims the observations do not support. No ranking, no "most important", no sizing, revenue or effort.
- The reply ends with `**Next suggested step:** problem-statement` (one card) or `problem-focus` (several), carrying the flagged assumptions forward; when the verdict is `frame with flagged assumptions` and the user would rather gather the evidence first, name the cheapest next evidence instead. Never a closing question after it.

## References

- `${CLAUDE_PLUGIN_ROOT}/references/evidence-ladder.md`: the ladder (non-Cagan), rung names, bands and the verdict line.
- `${CLAUDE_PLUGIN_ROOT}/references/insight-sources.md`: the four kinds of deep knowledge and where evidence comes from.

## Guardrails

- Frame fast, never gatekeep: weak evidence is a grade, a flag and a next step, not a refusal; the verdict is readiness to frame, never worth.
- Problems, not solutions: no feature, technology or vendor name in a claim; keep a requester's ask in `candidate_solutions`. The cheapest next evidence studies the problem, not a solution.
- Flag, don't invent: no quote you cannot find in the card, no number it does not give (`[unknown: flagged]`); user estimates stay labelled `estimates and plans`; inferences are **Assumption:**.
- Label provenance: the ladder is non-Cagan; say so when you explain a rung. Derived-template lines stay.
- Never declare "the most important problem"; never rank or demote cards by their evidence.
- Size the problem, not the payoff: no revenue, effort, Ease or duration estimates (the evidence timebox is the only duration).
- Judgment over process: the rung and the verdict are judgments you explain; the ladder does not decide for you.
- Never write to the plugin's install directory. Existing card lines are never overwritten, and no file is deleted.
