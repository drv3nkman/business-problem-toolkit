---
name: problem-review
description: Use when reviewing, critiquing or checking an existing problem statement, objective or OKR ('is this a good problem statement?', 'critique this statement', 'review statements/P-005.md'). Not for drafting a new statement — use problem-statement.
---

# problem-review

Reviews a problem statement, objective or OKR that already exists, whether this plugin wrote it or someone else did. It rates the text against the seven statement criteria and scans it for Cagan's anti-patterns. Each finding gets a result (pass, flag or fail), the quoted text and a suggested rewrite, and the review ends in a verdict: ready, revise or reframe. It judges how well the statement is framed, never how important the problem is. The criteria are drawn from Cagan; the pass/flag/fail rating and the verdict rule are this plugin's (derived), and the ratings prompt judgment, they are not a score.

## When to use

- "Is this a good problem statement? ...", "critique our OKR: ...", "review statements/P-005.md", "check this objective before we hand it to the team".
- A statement or OKR from outside the plugin (pasted, or a file the user points to) or one the plugin wrote.

## When not to use

- Drafting a new statement from a card: problem-statement. A review only suggests rewrites of what is already written.
- A solution-shaped request that is not a statement ("the CEO wants SSO"): reframe-request. A review ends there only when its verdict is reframe.
- Grading the evidence behind a card (problem-evidence), writing key results (success-measures), or choosing among problems (problem-focus).

## Inputs

- **A statement in the workspace:** named by path, or by ID, which means the statement `links.statement` names (else the highest `statements/P-NNN-vN.md`, else `statements/P-NNN.md`); if the card's link is stale (it names `statements/P-NNN.md` while a `-vN` file exists), say so and use the latest file. Read the whole file, the card it links, and `context.md` when it exists.
- **Text to review:** a statement, an objective, an OKR (objective with key results) or a single key result, pasted or in a file outside the workspace.
- A card named instead of a statement: review its `problem` line as text, in chat. The card's problem line is a claim; read its Observations and `confidence` before you rate Customer-anchored or the evidence scan.
- Do not stop to ask for what is missing. A missing objective, key result, customer or trace is a finding.

## Steps

### 1. Locate the workspace (problem-workspace → Locate)

Follow Locate in problem-workspace. A bare `P-NNN` names that card's latest statement (Inputs) in the located workspace: look there (list `problem-work/*/statements/`), never search outside the project, and do not ask which file when it exists. **Chat-only** is the mode for pasted text and for a file outside `statements/` (Locate step 3), and whenever the user says not to save anything. The first output line is then `> **Chat-only mode:** nothing is being saved.` Give the whole review in the conversation, write no file or folder anywhere, and stay chat-only until the user asks to save or to create a workspace (Locate step 3).

### 2. Take the text

Workspace mode is only for a statement file under `statements/` that exists. Several named: review each, one table and verdict per statement. Pasted text is reviewed as pasted, even when the workspace has a similar statement: say which text you reviewed. Note what the text is (statement, objective, OKR or key result) and what it does not contain.

### 3. Rate the seven criteria

Rate all seven rows of the criteria table in `${CLAUDE_PLUGIN_ROOT}/references/good-vs-bad-criteria.md` (Statement criteria), always, in its order: Solution-free, Clear and meaningful, Outcome-linked, Customer-anchored, Strategy-traceable, Impactable, Not metric-driven. Never leave a row out, never merge rows. Judge each against the Good and Bad columns, using only what is on the page. For a statement, the Key results answer and, once written, `## Success measures` count as its key results; the Evidence and Strategic trace sections count as its trace.

- **pass**: the text meets the Good column. Quote the words that show it.
- **flag**: partly met, or the text does not show it either way (no customer named, no objective or team named, no key results given, a section still `_Pending:`). A flag for something absent is never a fail: frame fast, never gatekeep.
- **fail**: the text affirmatively matches the Bad column: it names a feature or deliverable, a key result is an output ("ship X"), the wording is vague, or a measure is chosen because it already exists.

Not metric-driven asks one thing: was the problem picked because a KPI already exists? Never word it, or any rewrite, as whether the problem "matters" or is "important" (importance is not judged here); ask whether the measure follows from the customer problem or the problem from the measure.

A pending section is not a defect. Say it is not written yet and leave the line alone. Which skill fills it is the next step, not a finding.

### 4. Scan for the anti-patterns

Run the seven scans in `${CLAUDE_PLUGIN_ROOT}/references/anti-patterns.md` (Review scans). A scan that hits is a finding in the table. Four pair with a criterion row, so record them in that row's first cell, e.g. `Solution-free (feature in disguise)`: feature in disguise with Solution-free, vague with Clear and meaningful, request with no why with Strategy-traceable, metric-driven with Not metric-driven. The other three get their own row only when they hit: `OKR theater` (deliverables as key results, solution dictated, objectives that dilute team objectives), `Gatekeeping language` (demands proof the problem is "worth solving", ranks it, calls it "the most important"), `Missing customer or business evidence` (names no customer evidence and no business context; for a workspace statement, check the Evidence section against the card's Observations, verdict and `confidence`). Name the scans that found nothing in one line under the table. A hit is a question to ask, not a verdict.

### 5. Write the rewrites

Every flag and fail gets a suggested rewrite of the quoted text, concrete enough to paste in. A pass gets a dash.

- Smallest change that fixes the finding. Form: verb + measurable thing + for whom (the reference's Form note). A key result states the outcome that moves, not the thing shipped.
- A feature, product or deliverable in the original is moved out of the statement, not deleted: say "(original kept as a candidate solution)" in the cell.
- Invent nothing: no customer, figure, baseline, target, team or objective that the text, the card or the inputs do not give. A fact a rewrite takes from the card, `context.md` or an input is cited in the cell (file and location); one you cannot cite is not in the rewrite. An ownership or dependency rewrite (who supplies, owns or does what, which team holds what data) asserts that only when the statement, the card or an input says so; otherwise write `[unknown: flagged]` plus an `Ask:` and never state it as fact. Where the rewrite needs one, write it `[unknown: flagged]` or ask for it (`Ask: ...`). Any rewrite that states a customer, need or outcome the text did not state (turning a launch into an outcome always does) carries `**Assumption:**` inside that table cell, offered as a starting hypothesis for reframe-request, never as the answer; an outcome you cannot ground at all is `[unknown: flagged]` plus an `Ask:`.
- Under a reframe verdict the problem is guessed once, in the Solution-free row, labelled `**Assumption:**`. Every other row's rewrite points to it ("see the Solution-free rewrite") or leaves what is missing `[unknown: flagged]` with an `Ask:`; no other row proposes its own customer, need or metric.
- For an absent-text flag, the rewrite is the clause to add, with the missing fact left `[unknown: flagged]`, and who could supply it.

### 6. Give the verdict

One line `Verdict: ready | revise | reframe — <one sentence why>` (pick one value; the line starts with it). Judgment, not a tally; never average the ratings.

- **reframe**: take the solution or output away and no who or unmet need is left in the text (the objective itself is a launch, a feature or a stakeholder request). Revising wording will not help; the problem has to be uncovered first. It hands off to reframe-request, with the original text as its input.
- **revise**: a problem is identifiable but at least one criterion fails or a flag changes what a team would do (an output key result, vague wording, no customer, a measure picked for being on a dashboard, ranking language, a premature statement). The rewrites are the fix.
- **ready**: no fail, and the flags are for things a later skill fills in (success measures or viability still pending) or are minor. It can be handed on as written. Ready says the statement is framed well, never that the problem is important or worth doing, and it is not an approval. In the reply, a ready verdict says so in a sentence: fit to hand on as written, not a judgement of importance.

### 7. Record (workspace mode)

Write only to the statement file you reviewed, the one Inputs resolved for the ID (append-only: replace only its `_Pending:` review line, or append at the end, as below). Never edit any other line of it, never apply a rewrite yourself, and write no other file: no card, backlog or `workspace.md` change and no decision-log line, because a review is not a decision.

- **First review**, when `## Review` holds the line `_Pending: run problem-review._`: replace that one line with `Reviewed YYYY-MM-DD.`, a blank line, the findings table, the scans line, and the `Verdict:` line. The `## Review` heading stays.
- **Any later review**, or a `## Review` that holds no pending line, or none: append `## Review — YYYY-MM-DD` at the end of the file with the same content. Take the last lines of the file as `old_string` for the Edit (enough to be unique) and repeat them unchanged ahead of the new block. A second review on the same day appends a second block. Earlier reviews are never edited.
- The findings table header is exactly `| Criterion or anti-pattern | Result (pass/flag/fail) | Quoted text | Suggested rewrite |`. Quoted text is one unbroken run of the text, copied word for word inside quotation marks, never with an ellipsis or a changed word (take the smallest phrase that shows the finding), or a dash when the finding is an absence. A `|` inside a cell is written `\|`. Keep cells to a line or two.

## Output

- Reply, in this order: in chat-only mode the `> **Chat-only mode:** nothing is being saved.` notice, always the very first line, before the verdict; the `Verdict:` line; the findings table (same as the file), whose header line is character for character `| Criterion or anti-pattern | Result (pass/flag/fail) | Quoted text | Suggested rewrite |` (never shortened, in chat as in the file); the scans line; what is not written yet (a pending section) or `[unknown: flagged]`, with who could supply it; what changed ("only <the statement file reviewed>" or "nothing was saved"). Say once that the criteria are drawn from Cagan and the rating and verdict are this plugin's derived rule.
- A reframe verdict also says in one line what the text asks for versus what problem might sit underneath, labelled `**Assumption:**`, and that reframe-request will uncover it.
- Every response ends with a line `**Next suggested step:** <skill or action>`, one step only, the first that applies: reframe: reframe-request on the reviewed text; revise: problem-statement to redraft P-NNN with these rewrites (in chat: apply the rewrites and send it back for another review), or problem-evidence for P-NNN when the evidence row is the only fail or flag; ready: success-measures when `## Success measures` is pending, then viability-constraints when its section is pending, otherwise team-objectives. Never "Next step", never a closing question.

## References

- `${CLAUDE_PLUGIN_ROOT}/references/good-vs-bad-criteria.md`: the seven statement criteria with Cagan's good and bad columns, the form of a statement, and the rule that a statement is premature without customer evidence and business context.
- `${CLAUDE_PLUGIN_ROOT}/references/anti-patterns.md`: the seven review scans with their tell-tale signs, what to do about each and the sources.

## Guardrails

- Frame fast, never gatekeep: missing evidence or trace is a flag with a rewrite or a question, a premature statement is `revise`, and nothing here blocks the work. Never demand proof the problem is "worth solving".
- Problems, not solutions: rewrites remove the solution from the statement and keep it as a candidate solution; a rewrite never names a feature.
- Flag, don't invent: no customer, figure, baseline, target or fact that no source gave; unknowns are `[unknown: flagged]`; a guessed problem is an `**Assumption:**`.
- Label provenance: criteria are Cagan's (as the reference cites them); the pass/flag/fail rating and the verdict rule are derived. Cite no source the reference does not give.
- Never declare "the most important problem". Does not judge importance: no "important", "worth solving", "high-impact" or ranking of a problem, and no verdict that implies one. Ranking language in the reviewed text is itself a finding (Gatekeeping language).
- Size the problem, not the payoff: no revenue, effort, Ease or duration in a rewrite or a finding.
- Judgment over process: the ratings prompt thinking and the verdict is argued; the user decides what to change.
- Never write to the plugin's install directory. Statements are append-only, `## Review` lines are never rewritten after the first, and no file is deleted.
