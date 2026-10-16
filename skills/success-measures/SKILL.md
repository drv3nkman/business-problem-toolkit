---
name: success-measures
description: Use when defining how success will be measured for a problem that has a statement, or when asked for key results, a backstop metric, a baseline or leading indicators ('how should we measure success for P-001?', 'what's a good backstop metric?', 'add key results to statements/P-001.md'). Not for assigning objectives to teams — use team-objectives; not for critiquing an existing OKR — use problem-review.
---

# success-measures

Defines how success will be measured for a problem that already has a statement: an outcome as the primary key result, a backstop that guards against a side effect, the baseline if one is known, the measurement that still has to be added and the leading indicators. Success is defined before metrics are chosen. Target values are left to the team; this skill offers a calibration question and, when deep sizing exists, a reference range. The pairing of a primary key result with a backstop is Cagan's.

## When to use

- "How should we measure success for P-001?", "add key results to statements/P-001.md", "what's a good backstop metric for this?", "define the key results for this objective".
- A statement (a `statements/P-NNN.md`, or an objective in the conversation) whose `## Success measures` still holds `_Pending: run success-measures._`.

## When not to use

- Assigning objectives or problems to teams: team-objectives.
- Writing the statement itself (problem-statement), critiquing key results already written (problem-review), constraints (viability-constraints).
- Choosing which problem to work on, or sizing it (problem-focus, opportunity-sizing).
- A user who wants to pick the metric first ("we already track NPS, so make that the problem"): see step 2.

## Inputs

- **A statement:** `statements/P-NNN.md`, or a bare `P-NNN` or `statements/P-NNN.md`. Either form means the statement `links.statement` names (else the highest `statements/P-NNN-vN.md`, else `statements/P-NNN.md`) in the located workspace: look there, never search outside the project, and do not ask which file when it exists; if the card's link is stale, say so and use the latest file. Read the statement, its card, `context.md` and the cited `inputs/`.
- **Raw text:** an objective or problem in chat. Use only what it says.
- The deep sizing the card's `links.sizing` names, when it is a `sizing/P-NNN-deep*.md` file (use the highest `-vN`), for a reference range (step 6). A quick sizing file is not one.
- A statement with no card, or a card that is not yet framed, is fine: say so and work from the text. Raw text with no statement is worked from in chat (chat-only), and the reply names problem-statement as the way to save a statement.
- Do not stop to ask for what is missing. A missing baseline or measurement becomes `[unknown: flagged]`.

## Steps

### 1. Locate the workspace (problem-workspace → Locate)

Follow Locate in problem-workspace. No workspace and the user declines to create one, or the user says not to save anything: **chat-only**. The first output line is then `> **Chat-only mode:** nothing is being saved.` Write no file or folder anywhere and stay chat-only until the user asks to save or to create a workspace (Locate step 3).

### 2. Define success before choosing metrics

Read the objective and the customer problem. In one or two sentences say what would be true in the world if the problem were solved (for whom, what changes), without naming a metric. Then choose measures. If the user starts from a metric ("increase NPS", "move the dashboard number"), flag it: the problem comes first and a metric already being tracked is not a reason to choose a problem (Cagan: "letting the tail wag the dog"). Ask what customer or business problem they are seeing, name problem-discovery or reframe-request if they have none, and write no key results around the metric as given. A new KPI may be needed; that goes in step 5.

### 3. Primary key result

One line, an outcome: a business or customer result that moves, never an activity or a deliverable. It never starts with Ship, Launch, Build, Release or Deliver, and names no feature, tool or system. Say the thing counted or timed (a duration, a count, a rate), for whom, and the direction. No number as a target. Test: could the team hit it by shipping nothing the customer notices? If it could be met by shipping something, it is an output; rewrite it.

### 4. Backstop key result

A second key result that guards the primary from being hit by hurting something else: name the plausible side effect (a speed-up that raises errors, a cost cut that lowers quality, a deflection that raises complaints) and the measure that would show it. Say in a clause why that side effect is plausible here (from the card, context or inputs; otherwise label it `**Assumption:**`). Prefer a measure someone already owns (name the team from `inputs/teams.md` if it fits). No target.

### 5. Baseline, new measurement, leading indicators

- **Baseline:** the current value of the primary key result if a source gives it (quote it with its file and period, and `data` or `user-estimate`). Never compute, round up or estimate one. None: `[unknown: flagged]` and say what would give it.
- **New measurement needed:** the measure that does not exist yet and has to be added (a timestamp, a count, a field), or "none: existing data is enough" with the source. Anything cited as existing must be in an input.
- **Leading indicators:** two to four earlier signals that move before the primary does, each tied to the problem's Observations. They are signs to watch, not targets and not further key results.

### 6. Targets

Do not set a target. Write that the team proposes it, and ask the calibration question: "Would a 1% improvement be excellent or a waste of time here?" Then read the deep sizing the card's `links.sizing` names (a `sizing/P-NNN-deep*.md` file, highest `-vN`; a quick-sizing table is a triage aid and is not a source of ranges). If deep sizing gives a range, quote its low, base and high values (all three, even when two are equal) with their basis (`data` or `user-estimate`) and file, label it a reference range from sizing and say it is not a target. No deep sizing for this problem: say there is no reference range. Ask the calibration question as written, with 1%; do not substitute another percentage. Never turn a range into a target, never add a figure no source gave, and never project revenue or savings (size the problem, not the payoff).

### 7. Record (workspace mode)

- **Statement file** (append-only): replace only the single line `_Pending: run success-measures._` under `## Success measures` with the six H3s, in order and with exactly these headings: `### Primary key result`, `### Backstop key result`, `### Baseline`, `### New measurement needed`, `### Leading indicators`, `### Targets`. Every other line of the statement stays byte-identical, the `## Review` section included, and so does any text you did not write. If the section already holds real content, or the placeholder is gone, do not edit the file: report what is there and name problem-statement (a redraft, which makes a `-v2` whose measures this skill then fills).
- **workspace.md** (living): set `updated`, move `stage` to `define` if it is earlier, leave `checkpoints_since_decision` as it is, and put this reply's next step in the next-step line. No decision-log line (defining measures is not a logged decision). Touch no card or backlog row.
- Chat-only: give the six sections in the reply, under the chat-only notice.

## Output

- Reply, in this order: the one-sentence success definition; the primary and backstop key results; the baseline; the measurement to add; the leading indicators; the targets note (team proposes, calibration question, reference range or its absence); what changed ("only `## Success measures` in <the statement file written>, plus workspace.md").
- Every response ends with a line `**Next suggested step:** <skill or action>`, one step only: viability-constraints for P-NNN when the statement's constraints are still pending; otherwise customer-letter for a large or multi-problem effort, or team-objectives when the work is to be assigned. For a metric-first start, problem-discovery. Never "Next step", never a closing question.

## References

- `${CLAUDE_PLUGIN_ROOT}/references/good-vs-bad-criteria.md`: the outcome-linked and not-metric-driven criteria and Cagan's worked backstop example.
- `${CLAUDE_PLUGIN_ROOT}/references/cagan-principles.md`: Cagan on outcomes versus activity, and two key results per objective.
- `${CLAUDE_PLUGIN_ROOT}/references/guardrails.md`: the seven guardrails and the standard responses (flag syntax, chat-only notice).

## Guardrails

- Frame fast, never gatekeep: missing baselines and measures are flagged and carried, not a reason to stop.
- Problems, not solutions: no key result names a feature or tool; an output ("ship X") is rewritten as an outcome.
- Flag, don't invent: no baseline, number, owner or existing measure that no source gave; unknowns are `[unknown: flagged]`; user estimates are labelled `user-estimate`. Targets are the team's; sizing ranges are quoted with their basis, never as targets.
- Label provenance: key results and the backstop are Cagan's; the reference-range rule and calibration question are this plugin's (derived); sizing is non-Cagan and is quoted as such.
- Never declare "the most important problem": measures say nothing about rank or worth.
- Size the problem, not the payoff: no revenue, savings, effort, Ease or duration projection.
- Judgment over process: the team and user decide the measures; this skill proposes.
- Never write to the plugin's install directory. Statements are append-only (only the `_Pending:` line is replaced), `## Decision log` is append-only, and no file is deleted.
