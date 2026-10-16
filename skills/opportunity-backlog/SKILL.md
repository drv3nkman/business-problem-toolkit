---
name: opportunity-backlog
description: Use when adding to, merging, shortlisting, parking ('not now'), updating, importing or viewing the list of candidate problems (backlog.md), and for recording that a fix or solution for a problem failed or did not move the numbers (the problem stays on the list). Not for comparing sizes — use opportunity-sizing; not for picking the final 2–3 — use problem-focus.
---

# opportunity-backlog

Keeps the list of candidate problems: `backlog.md` and the status of each card. It is a list, not a ranking: it records what is a candidate, what the user shortlisted, what was parked and why, and what failed and came back. It never says which problem matters most. Problems come from strategy, not from stakeholder requests (`cagan-principles.md`), so a request that reaches the list is kept as a candidate solution, never as the problem.

## When to use

- **Add** a problem to the list ("add: new reps learn the desk by trial and error").
- **Merge** one card under another ("merge P-004 into P-001").
- **Shortlist** candidates ("shortlist P-001, P-004 and P-005").
- **Park** a problem as not-now, **revisit** a parked one ("the ERP upgrade shipped, bring P-003 back").
- **Solution failed**: a team's fix did not work ("our fix for P-005 didn't work, put it back on the list").
- **Import** a pasted or filed list of problems or asks. **View** the backlog ("show me the backlog", "what's parked?").

## When not to use

- Comparing sizes, bands or urgency: use opportunity-sizing. This skill never sizes, never fills Quick size or Urgency, and never uses a size to order anything.
- Choosing the final 2–3 problems, or recording a focus decision: use problem-focus. The `## Focus decisions` section of `backlog.md` is never touched here.
- Grading evidence (problem-evidence), turning one solution-shaped request into a problem (reframe-request) or finding new problems in notes (problem-discovery).
- Setting `chosen`, `assessed`, `framed` or `assigned`: those belong to problem-focus, opportunity-assessment, problem-statement and team-objectives. Only the moves below are made here.

## Inputs

- The IDs or the text the request names. A request that names no ID for a move ("park the credit one") is matched against the cards' problem lines; if two could fit, ask which. Do not stop for anything the request already gives.
- The cards' front-matter and `## Viability screen`, `backlog.md` and `workspace.md`'s `## Decision log`.
- For Import: a list pasted in the request, or a file named in it or sitting in `inputs/`. Read it; never edit `inputs/`.

## Steps

### 1. Locate the workspace (problem-workspace → Locate)

Follow Locate in problem-workspace. No workspace and the user declines one, or says not to save anything: **chat-only**. The first output line is `> **Chat-only mode:** nothing is being saved.` Do the same work on the list the user pasted or described, show the resulting table in the conversation, write no file or folder anywhere, and stay chat-only until the user asks to save or to create a workspace (Locate step 3).

### 2. Read, then sync

Read the front-matter of every `cards/P-*.md`, `backlog.md` and the decision log. **The cards are the source of truth** for status and front-matter; the backlog table follows them. A card that does not parse is reported and left alone, with its row.

- No `backlog.md`: create it from `_templates/backlog.md` (fall back to `${CLAUDE_PLUGIN_ROOT}/templates/backlog.md`), the initiative name in the title, one row per card, and add `- [Backlog](backlog.md)` under `## Artifacts` in `workspace.md`.
- A row whose status differs from its card, or a card with no row: fix the row (Status cell, or add the row) before the move below and say so. A row with no card, or a duplicate row, is reported, never removed.
- Table columns are the template's: ID, Problem, Who, Origin (first origin kind only), Confidence, Quick size, Urgency, Status, Next step. Blanks are `—`. Edit only the cells that change.

### 3. Add

1. **Existing cards first** (reframe-request's rule). Same who and same need as a card: attach to it, make no duplicate: one History line (`- YYYY-MM-DD raised again via opportunity-backlog: "<their words>" (<source>)`), set `updated`, and say which card. Partial overlap: a new card whose Notes say `Related: P-NNN (overlap: …)`. Never merge silently.
2. **Solution-shaped?** A named feature, product, technology or vendor ("build a chatbot", "add SSO") is a request, not a problem. Do not write it as a problem. Call the Skill tool for reframe-request with the ask: it reverses the ask, ties it to an existing card or writes the card and the backlog row, and keeps the original in `candidate_solutions`. Do not do its work inline, and never write "by reframe-request" in a History line unless it ran. If it cannot be invoked, say which items are solution-shaped and name reframe-request as the next step.
3. **A problem the user states**: write one card. ID = highest `P-NNN` ever used plus one, counting card file names and every ID in the Decision log (a merged-away ID is still used); never fill a gap. Start from `_templates/card.md`, name it `cards/P-NNN-<slug>.md`, fill every front-matter key (only `parent` may be left out), double-quote strings, remove the template comments, keep every H2.
   - `problem`: the user's own sentence, solution-free, and nothing else: no extra clause, no named group, no consequence, cause, reach, frequency or severity ("so people have already planned around it", "for the people waiting on them"). Do not pad it into a longer sentence. When they named no who, put the likeliest group in `who` and the line as `<their sentence>. **Assumption:** the people affected are <group>.` (the `who` field and Who cell then hold that group); every other reading goes in Interpretation, never in the problem line, and each sentence there that goes past their words begins **Assumption:** (including "others may be affected"); otherwise Interpretation says `Nothing beyond the user's words yet.`
   - `origin`: one entry `kind: stakeholder` (a problem someone asserted with nothing behind it) with `ref` the exact words and `[conversation]` or the file; use the user's own kind and ref if they supply evidence.
   - `evidence_grade: "others' opinions (provisional)"` (`self-conviction (provisional)` when the user states it as their own belief), `confidence: very-low`, `distinct_sources: 1`, `status: candidate`, `discovered_in:` and every `quick_size` key empty. No size, no figure the user did not give.
   - Body: Problem; Observations (one row, the exact words, `stakeholder assertion`); Interpretation with the assumptions; what we'd need to learn next (who, how often `[unknown: flagged]`, cheapest evidence); `Not yet examined.` under Where it does / doesn't occur; the two `_Pending:` lines; History `- YYYY-MM-DD candidate added by opportunity-backlog`.
4. Add a row (Origin `stakeholder`, Confidence `very-low`, Quick size and Urgency `—`, Next step `Gather evidence (problem-evidence)`) and an Artifacts link `- [Card P-NNN](cards/P-NNN-<slug>.md)`. Adding is not a decision: no Decision log line.

### 4. Import

For each item in a list: a stated problem goes through Add (step 3); every solution-shaped item is collected and then handed over in one Skill call to reframe-request with the whole subset (it clusters them). Every item gets exactly one outcome: attached to a card, a new card, reframed, or a question. Source IDs and columns in the list are not kept as IDs; new cards get new IDs and the source label goes in the origin `ref`. Report one line per item, in the list's order. Do not rank the items, and do not drop one.

### 5. Merge

"Merge X into Y": Y is the parent. Do it as asked, then say what it means; never refuse because the cards look different, but if their needs are not the same, say so in one line (a partial overlap is the user's call, and clearing `parent` undoes it). Stop and ask only when X is Y, Y is X's child or X already has a different parent.

- X: set `parent: Y`, `updated`, History `- YYYY-MM-DD merged under Y by opportunity-backlog: <reason>`. Y: add X to `children`, `updated`, the same History line. Both files stay, with their own status and row. X's row Next step: `Merged into Y`. X keeps its own children.
- Decision log: `- YYYY-MM-DD — merged — X into Y — <one-clause reason, the user's if given, else "merged at the user's request">`. The log and History are append-only: a reason the user gives later is added as a new line, never swapped into the old one.

### 6. Shortlist

The user chooses what to shortlist; never pick for them ("shortlist the best ones": show the candidates in ID order and ask which). Only `candidate` cards move. A card already shortlisted or further along stays as it is (say so).

1. For each card, read `## Viability screen`, and **only its latest block**: the last `Screened YYYY-MM-DD` or `Re-screened YYYY-MM-DD` heading line and the lines under it, up to the next such heading or the end of the section (no such line: the whole section is one block). Earlier blocks stay on the card (append-only) but are history: a **yes** in an earlier block that a later block answers **no** is cleared, never suggest not-now for it, and ignore a `Changed since` line. A card **failed the screen** only when a deal-breaker, in any of the seven categories, is answered **yes** in the latest block with its reach to this card established: the line says `reach: established`, or it gives no reach and nothing on the line marks its reach `[unknown: flagged]`. Then say which deal-breaker and who to consult, and **suggest not-now** for that card. A card the user named is still shortlisted, as asked, and the suggestion goes in the reply; a card only swept in by a group request ("shortlist all candidates") is held back until the user answers. A yes whose reach is `[unknown: flagged]` is a flag, not a failed screen: name it and who settles it in the reply, shortlist the card as asked (named or swept in) and suggest nothing. Park only through Park (step 7), never by yourself. `_Pending:` means unscreened: shortlist, and name viability-constraints (screen mode) in the reply.
2. Set `status: shortlisted` and `updated` on each card; History `- YYYY-MM-DD shortlisted by opportunity-backlog`; the row's Status cell and Next step (`Quick sizing (opportunity-sizing)` if unsized).
3. One Decision log line: `- YYYY-MM-DD — shortlisted — P-004, P-007 — <the user's reason, else "shortlisted at the user's request">`.

### 7. Park (not-now)

**Parking needs a reason and a revisit trigger, and never proceeds silently.** Either missing: do not park that card yet; ask for both in one short question and write nothing for it. Never write a reason or a trigger the user did not give (you may offer an example for them to react to, but nothing is saved until they answer), and never park because a size, a screen or thin evidence says to. A reason of "not now" or a trigger of "later" is not enough: ask for a reason that says why and a trigger that can be seen happening (an event or a date). Other cards in the same request proceed. A `not_now` value that begins `proposed:` was written by problem-focus from its comparison; this skill never writes a `proposed:` value itself, and when the user supplies the real reason or trigger for such a card, Park records a new not-now decision with the user's words (status unchanged, `not_now` values replaced, History and Decision log lines added).

With both: `status: not-now`, `not_now: { reason: "<their words>", revisit_when: "<their words>" }`, `updated`, History `- YYYY-MM-DD parked by opportunity-backlog: <reason>; revisit when: <trigger>`; the row's Status and Next step `Revisit when: <trigger>`; Decision log `- YYYY-MM-DD — not-now — P-003 — <reason>; revisit when <trigger>`. Park `candidate` or `shortlisted` cards. For `chosen`, `assessed`, `framed` or `assigned` (a focus decision or a team's work stands on it) confirm first, and say that the focus record under `## Focus decisions` is not edited here: a changed focus is a new decision for problem-focus. The card stays on the list.

### 8. Revisit

When the user says the trigger has happened or wants a parked card back: only a `not-now` card moves. `status: candidate`, both `not_now` values emptied, `updated`, History `- YYYY-MM-DD revisited by opportunity-backlog: back to candidate (was parked: <reason>; revisit when: <trigger>; now: <what happened>)`; report a `proposed:` reason or trigger as proposed by the plugin, not as the user's words, row Status and Next step `Gather evidence (problem-evidence)`, Decision log `- YYYY-MM-DD — revision — P-003 — back from not-now to candidate: <what happened>`. It does not go straight to shortlisted. Whether a trigger has been met is the user's call; do not declare it met.

### 9. Solution failed

A problem stays on the list, with its status, when its solution fails: the team iterates on the same problem. A failed solution never changes a card's status. Append to History `- YYYY-MM-DD solution attempt did not work: <only what the user said>`, set `updated`, and write no Decision log line (nothing was decided).

Record only what the user said. What the fix was and which numbers did not move: `[unknown: flagged]` unless given, and ask for them in the reply after writing. Do not guess the fix from `candidate_solutions`. Leave the problem line, `candidate_solutions`, the statement and the sizing alone: a failed fix is evidence about the solution, not proof the problem was wrong.

### 10. View

Read-only. Show the table in ID order (never by size, evidence or any score), a count for all seven statuses (zeros included), and for every `not-now` card its reason and revisit trigger (report a `proposed:` reason or trigger as proposed by the plugin). List flags in one line each: row and card disagree, unscreened cards, a card that will not parse. Offer to sync; write nothing. Filter by status when asked.

### 11. Record (workspace mode)

Cards are append-only: change front-matter, append History lines (Edit with the last History line as `old_string`), replace no other body line. The backlog table is living. In `workspace.md` append the Decision log line(s) at the end of `## Decision log`, never edit a past line, set `updated`, move `stage` to `identify` if it is `foundation`, add 1 to `checkpoints_since_decision` (set it to 0 instead when this run parked a card as not-now), and put this reply's next step in the next-step line. Existing files are never overwritten and nothing is deleted.

## Output

- Workspace mode: the changed cards, `backlog.md`, `workspace.md`, and for an Add or Import the new cards. Chat-only: the table and changes in the conversation after the notice line.
- Reply: what changed per card (ID, old status → new status), anything asked (a missing reason or trigger, the fix that failed), any viability suggestion, and the table of the cards touched. No ranking, no "most important", no sizing.
- Every response ends with a line `**Next suggested step:** <skill or action>`, one step only: after shortlisting, opportunity-sizing (quick) if two or more are shortlisted, else problem-evidence; after Add or Import, problem-evidence; after a failed solution, problem-evidence on what the attempt shows; when a question is open (a missing reason or trigger, the failed fix), the step is to answer it. Never "Next step" and never a closing question.

## References

- `${CLAUDE_PLUGIN_ROOT}/references/cagan-principles.md`: problems come from strategy, not requests; problems are assigned, and a failed solution means iterating on the same problem.

## Guardrails

- Frame fast, never gatekeep: a thin item is added at very-low confidence, with a flag; parking asks for what it needs and then proceeds.
- Problems, not solutions: no solution term in a problem; asks go to reframe-request or `candidate_solutions`.
- Flag, don't invent: no reason, trigger, who, number or fix the user did not give; unknowns are `[unknown: flagged]`, inferences **Assumption:**.
- Label provenance: keep the derived-template line in every card and in the backlog.
- Never declare "the most important problem"; the list is in ID order and nothing here ranks.
- Size the problem, not the payoff: no sizing, revenue, effort or duration here.
- Judgment over process: merging, shortlisting and parking are the user's decisions; you suggest, and explain the screen.
- Never write to the plugin's install directory. IDs are never reused, existing card lines are never overwritten, `## Decision log` and `## Focus decisions` are append-only, and no file is deleted.
