---
name: problem-focus
description: Use when narrowing a shortlist of candidate problems to the 2–3 to pursue now, with an explicit not-now list and revisit triggers ('which of these should we work on next quarter?', 'help me choose between P-001, P-005 and P-007'), including when asked to rank them or name the single most important one (it declines that and picks 2–3). Not for a go/no-go write-up on a single new product or market bet — use opportunity-assessment.
---

# problem-focus

Narrows the shortlist to at most 3 problems to pursue now (usually 2 or 3) and records the rest as not-now, each with a reason and a revisit trigger. It never names "the most important problem": Cagan calls that question fruitless and unanswerable. Leaders pick a few problems through strategy and insight without an exhaustive search for the best one (this plugin's reading of Moore & Cagan, an inference, and how the 2–3 cap and the no-re-gating rule fit together; `guardrails.md`). The choice is a two-way door and is written down as one.

## When to use

- Choosing from a shortlist: "which of these should we work on next quarter?", "narrow the shortlist to two or three", "help me choose between P-001, P-005 and P-007", "pick what we should pursue".
- A changed mind or new information on an earlier choice: a new decision, written as a new block (Step 6).

## When not to use

- A go/no-go write-up for one new product or market bet: opportunity-assessment.
- Comparing sizes (opportunity-sizing), grading evidence (problem-evidence), adding, merging, shortlisting or parking cards one at a time (opportunity-backlog).
- Re-opening a problem leadership has already assigned: `chosen`, `assessed`, `framed` and `assigned` cards are not compared again here.

## Inputs

- The candidates: the IDs the request names, else every `shortlisted` card (say which). A named `candidate` card is included (the user's naming is the shortlist, say so). A `not-now` card is never included unless named, and then it is a revisit (opportunity-backlog) first.
- `context.md` (the latest `context*.md`; at least a light context), each candidate's card, the latest `sizing/quick-*` file, `backlog.md` and `workspace.md`.
- Anything the user states: which problems they favour, a reason or a trigger for one that waits.

## Steps

### 1. Locate the workspace (problem-workspace → Locate)

Follow Locate in problem-workspace. No workspace and the user declines one, or says not to save anything: **chat-only**. The first output line is `> **Chat-only mode:** nothing is being saved.` Work from what the user pasted or said (the same Step 2 stop applies to the objective), give the comparison and the decision block in the conversation, write no file anywhere, and stay chat-only until the user asks to save or to create a workspace (Locate step 3).

### 2. Stop if there is nothing to choose with

- **No `context.md`** (no `context*.md` at all, or in chat-only mode no objective or focus stated): **stop**. Write nothing and change no card. Say that choosing without a strategy is scoring against nothing, and route to strategic-context (light context is enough). Next step is strategic-context. A context that says "no product strategy" is a context: go on and carry its flag (Step 3).
- **Fewer than 2 candidates**: there is nothing to choose between. Write nothing; name the one card and make the next step problem-statement for it (or opportunity-backlog to shortlist more).

### 3. Compare on the five dimensions, side by side

Read each candidate before judging. Use its Observations and evidence fields, never its problem line alone (a problem line can overstate what the observations show). Build one table in ID order, one row each, with these columns and no total, score or rank:

- **Strategic fit:** against `context.md`'s objectives, focus areas and constraints. Outside the stated focus is a reason, not a ban. A context with the no-strategy flag: fit is `[unknown: flagged]` unless the user states the team's objective; repeat the flag `> **Flag:** No product strategy provided — Cagan calls this 'no strategy'.` in the reply.
- **Size band:** read from the latest sizing file (its band, range and `basis` label as written; the card's `quick_size` if no file). Unsized: `[unknown: flagged]` and say opportunity-sizing would fill it; never a reason to stop. No new number, no revenue, effort, Ease or duration; no total across rows with different units. Carry the sizing's "which number could change the pick" line into the reply in exactly this form, one line per unknown figure: `Open question: <the unknown figure>; who can answer: <role>`. The line names no problem and never says which way an answer would tip the choice.
- **Evidence:** the card's `evidence_grade`, `confidence` and `distinct_sources` (confidence belongs to problem-evidence; do not edit it). Thin evidence is a flag and a learn-next, not a veto.
- **Urgency:** the card's and the sizing's urgency; `[unknown: flagged]` if neither.
- **Can the team move it:** a judgment of ownership and reach from the context and the card: does the team own or influence the system where the problem occurs, or does it sit behind another team, a customer's own process or a constraint? Say which. Not an estimate of effort, difficulty or duration.

Also read each card's `## Viability screen`, and **only its latest block**: the last `Screened` or `Re-screened` line and the lines under it, up to the next such line or the end of the section (no such line: the whole section is one block). Earlier blocks are history, and a yes a later block answers no is cleared. A card is **blocked** only by a deal-breaker, in any of the seven categories, answered **yes** in that block with its reach to this card established: the line says `reach: established`, or it gives no reach and nothing on the line marks its reach `[unknown: flagged]`. A yes whose reach is `[unknown: flagged]` does not block: it is a flag carried on the card into the rationale and the reply's flags, with who settles it. A blocked card is not chosen unless the user names it; then record it as chosen with the deal-breaker flagged. A delegated choice (Step 4) never overrides this gate: the user has not named a blocked card. `_Pending:` means unscreened, a flag and never a block. Cards already `chosen` or further along are listed in one plain line, "Already in play (not re-gated here): …", and counted in the reply's note of the team's total load.

### 4. Decide

Choose by judgment and show the reasoning: size to a threshold, not a rank; look only at what could change the pick (the sizing's swing number); compare siblings, never one problem alone (`sizing-methods.md` choosing rules). A request to pick, narrow or choose is the go-ahead to record: say it is recorded as the user's decision unless they change it. Only a request that says not to record ("just talk me through it") gets the comparison and a proposal with nothing written.

- 1–3 **chosen**, never more than 3. Every candidate not chosen is **not-now**: no candidate is left shortlisted, and no problem is dropped. When every candidate is chosen, the Not now list holds exactly one line, `- none: every candidate was chosen`.
- The caller (the router under Keep going) says the user delegated the choice: treat the IDs it names as the shortlist (say so), choose 2–3 yourself and record them as proposed; a blocked card (Step 3) goes to not-now with `reason: proposed: deal-breaker <category> answered yes with established reach; consult <role>` and `revisit when: proposed: <role> clears it` (the user can name it later), and you never answer a delegated choice by asking which to choose. A card with only an unknown-reach yes is not blocked: it may be chosen, with the flag. Follow this even when the gate leaves only cards with weaker evidence: record the choice from the rest, and name in one line the parked cards the user can choose instead. If only one card is unblocked, choose that one alone and flag in the reply that the choice is short of 2–3 and why (the others are blocked by deal-breakers the user can clear by naming them). If no card is unblocked, that is a real question: ask the user which blocked cards to name, write nothing, and end with the next-step line. Otherwise the decision is reversible, so a choice you think is weak gets a flag, never a stop.
- The user said which to pursue: those are chosen as stated, all of them when they named every candidate (more than 3: ask which 3). Else you choose, and the reply names which dimensions decided it.
- **Asked to rank, to give "the single most important one", or for an order** ("rank them 1 to 5"): open the reply with the Standard response from `${CLAUDE_PLUGIN_ROOT}/references/guardrails.md` ("Asked which problem is 'the most important problem'"), word for word, then still do the decision. List chosen and not-now in ID order and say no order of merit is implied. Never put a number, "first", "top" or "most important" on any problem. No overall ordering between problems, in the reply or the block ("outweighs", "leads", "more important", "the weaker of the two", "the strongest"). A dimension-level fact that names the fact is fine ("has the most sources", "the only one with medium confidence"). A chosen problem with thin evidence gets its own flag and learn-next ("P-007's evidence is low: …"), not an apology set against the others; a not-now reason names the fact ("outside the stated focus", "one source"), never "less important".
- **Not-now reasons and triggers.** The user's own words win. Without them, write the reason from the comparison: the dimension(s) on which it stands behind the chosen ones, with the fact (the band, the evidence rung, the screen answer, the missing owner) quoted as the sizing or card states it, never a sum or recount of your own and never "less important". Write the revisit trigger as something that can be seen happening (an event or a date): the sizing's swing number being answered, evidence reaching a higher rung, the objective changing, a stated planning date. Never an invented date or figure. When the words are not the user's, the value itself begins `proposed: ` in the block and on the card: `reason: proposed: <why>` and `revisit when: proposed: <trigger>`; the labels stay exactly `reason:` and `revisit when:`. The user's own words carry no prefix. Say in the reply that proposed values are for the user to correct; a correction is a new decision block (Step 6).

### 5. Write the decision into `backlog.md`

Append a block below `## Focus decisions` (create the heading if missing). The example comment there is never edited, uncommented or moved; a `_Pending: no focus decision recorded yet._` line may be replaced by the block. The section is append-only: a second decision, even the same day, is a new block below the earlier ones, and the later block governs. Exactly this shape (the heading, then the labels):

```
### Focus decision — YYYY-MM-DD

Already in play (not re-gated here): P-00X (<its status on the card>), …   <- only if there are such cards; plain text, no bullet
Not compared (shortlisted, not named): P-00Y, …   <- only if the request named fewer cards than were shortlisted; plain text, no bullet; these cards stay shortlisted

**Chosen**
- P-NNN — <problem, as on the card> — why: fit: …; size: …; evidence: …; urgency: …; can the team move it: …

**Not now**
- P-NNN — <problem> — reason: <why>; revisit when: <trigger>

**Two-way door**
- This choice is reversible. <What would make us reopen it: the swing number, new evidence, a changed objective.>
```

Items in ID order, one bullet each, the date today; a Not now list with nothing to park holds the single line `- none: every candidate was chosen`. Each Chosen rationale covers all five dimensions, using `[unknown: flagged]` where one is not known.

### 6. Update the cards, the backlog table, the log and the manifest

Cards are append-only: change front-matter, append to History, replace no other line.

- Chosen: `status: chosen`, `updated`, `not_now` values empty; History `- YYYY-MM-DD chosen by problem-focus (Focus decision YYYY-MM-DD)`.
- Not-now: `status: not-now`, `not_now: { reason, revisit_when }` (the block's words, `proposed: ` prefix included), `updated`; History `- YYYY-MM-DD not-now by problem-focus: <reason>; revisit when: <trigger>`.
- A card changed by a later decision (chosen → not-now or back): the same fields, History says "changed by problem-focus (Focus decision <date>, was: <status>)". Do not edit the earlier block.
- `backlog.md` table: each row's Status; Next step for chosen = the step after this (Output); for not-now `Revisit when: <trigger>`. Edit only those cells.
- `workspace.md`: append at the end of `## Decision log` one line per decided card, chosen first then not-now, ID order: `- YYYY-MM-DD — chosen — P-001 — <one clause: why>` and `- YYYY-MM-DD — not-now — P-007 — <reason>; revisit when <trigger>`. Set `checkpoints_since_decision: 0` and `updated`; move `stage` to `choose` only if it is `foundation` or `identify` (never backwards); put this reply's next step in the next-step line. Never edit a past log line. Nothing is deleted.

## Output

- Workspace mode: the new block in `backlog.md`, the changed cards and rows, `workspace.md`. Chat-only: the table and the block in the conversation.
- Reply, in this order: the guardrail decline if one was needed; the five-dimension table; the decision (chosen with their rationale, not-now with reason and trigger marked proposed); the flags (no strategy, unsized, unscreened, a deal-breaker and whether it blocks, thin evidence, the team's total load with problems already in play); the `Open question:` line(s) for the number that could change the pick; the two-way-door note and how to change the choice.
- Every response ends with a line `**Next suggested step:** <skill or action>`, one step only. For the chosen cards, in ID order, the first that applies: a new product or market bet (opportunity-assessment, for P-NNN); evidence below `medium` (problem-evidence on P-NNN); viability screen still pending (viability-constraints, screen mode, on P-NNN); else problem-statement for P-NNN. Stopped at Step 2: strategic-context, or opportunity-backlog. Never "Next step", never a closing question.

## References

- `${CLAUDE_PLUGIN_ROOT}/references/sizing-methods.md`: the choosing rules (threshold not rank, only what could change the choice, 2–3 with explicit not-now, two-way door, without a strategy don't score). Non-Cagan.
- `${CLAUDE_PLUGIN_ROOT}/references/cagan-principles.md`: strategy is focus, and focus is "one, or a very few, pivotal objectives"; problems come from strategy.
- `${CLAUDE_PLUGIN_ROOT}/references/guardrails.md`: the Standard response for the most-important question.

## Guardrails

- Frame fast, never gatekeep: decide with thin evidence or no size and flag it; do not re-gate problems already chosen or assigned.
- Problems, not solutions: no solution term in a rationale; `candidate_solutions` are not an input.
- Flag, don't invent: no figure, date, reason or owner no source or user gave; unknowns are `[unknown: flagged]`, proposals are marked proposed.
- Label provenance: sizing bands are non-Cagan; the two-way-door idea is Bezos (non-Cagan); keep the derived-template line in every file.
- Never declare "the most important problem": no ranking, no order of merit, no composite score.
- Size the problem, not the payoff: no revenue, effort, Ease or duration, and "can the team move it" is reach, not effort.
- Judgment over process: the table informs and the decision is argued; the user can change it.
- Never write to the plugin's install directory. `## Focus decisions` and `## Decision log` are append-only, existing card lines are never overwritten, and no file is deleted.
