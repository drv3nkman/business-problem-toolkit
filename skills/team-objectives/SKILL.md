---
name: team-objectives
description: Use when handing framed problems to product teams as team objectives with key results — choosing which team gets which problem ('which team should own P-005?'), checking they can move the outcome, and flagging shared problems. Not for defining the measures of a single problem — use success-measures.
---

# team-objectives

Hands framed problems to teams as objectives for a period. Each objective is a problem stated qualitatively, with a primary key result and a backstop; the team proposes the target values. Each assignment is explained with the five criteria from Moore and Cagan (areas the team is responsible for, skills, enabling technology, data access, the team's ideas for pursuing the problem), checked against whether the team can actually move the outcome, and shared problems are flagged. Keep-the-lights-on work stays out. Objectives as the problem container, two key results and team-set targets are Cagan's; the objectives file layout is derived.

## When to use

- "Assign our framed problems to the teams for 2026-Q4", "which team should own P-005?", "turn these statements into team objectives".
- Framed problems (`statements/P-NNN.md`) plus a team list, ready to be handed over.

## When not to use

- Defining the measures of one problem (success-measures), writing the statement (problem-statement), choosing which problems to work on (problem-focus).
- Ranking teams or problems, or setting targets: the team proposes its own.

## Inputs

- **Framed problems:** cards with a statement: the statement `links.statement` names (else the highest `statements/P-NNN-vN.md`, else `statements/P-NNN.md`); if the card's link is stale (it names `statements/P-NNN.md` while a `-vN` file exists), say so and use the latest file. The user names them (`P-005`), or says "our framed problems" and the framed cards are meant. Read each statement (key results, strategic trace, open assumptions), its card and `context.md`.
- **Team list:** the teams with their areas, skills, technology and data access (a file in `inputs/` such as `inputs/teams.md`, or text in chat). **Without a team list, ask for one and stop: do not invent teams, and do not guess teams from a statement's trace or the context.** Say which four things you need per team.
- **Period:** `YYYY-QN` (for example `2026-Q4`). If not given, ask for it. Anything else ("next quarter", "Q4") is confirmed and written as `YYYY-QN`.
- Keep-the-lights-on work the user names, or that `inputs/` and the context describe as run-the-business.

## Steps

### 1. Locate the workspace (problem-workspace → Locate)

Follow Locate in problem-workspace. No workspace and the user declines to create one, or the user says not to save anything: **chat-only**. The first output line is then `> **Chat-only mode:** nothing is being saved.` Write no file or folder anywhere and stay chat-only until the user asks to save or to create a workspace (Locate step 3).

### 2. Gather what is needed, then ask only for what is missing

You need: the problems, a team list, a period. Missing a team list or a period: ask for it in one short message (the team list as above, the period as `YYYY-QN`), write nothing, and end with the next-step line. Do not continue with invented teams or an assumed period.

### 3. Check the problems are framed

Assign only problems that have a statement (card `status` `framed`, with `links.statement` set and the file present). For a problem that is not framed yet (no statement, or a card that is only `chosen` or `assessed`): do not assign it. Name it, say what is missing, and offer problem-statement first; the other problems go ahead. `assigned` means leadership assigned the problem to a team; `links.objectives` says which team. An `assigned` card whose `links.objectives` names an objectives file is not re-gated: leave it as it is, list it in the reply with that owner, and assign it again only if the user asks. An `assigned` card whose `links.objectives` is empty is assignable like a framed one (a team was given it; this run records which team). Cards in `candidate`, `shortlisted` or `not-now` are never assigned.

### 4. Choose the team for each problem

For each problem compare each team on the five criteria, from the team list and the problem (never from memory of the company):

- **Areas they are responsible for**
- **Skills on the team**
- **Enabling technology they use**
- **Data they have access to**
- **Their ideas for pursuing this problem** (use only ideas the team list or inputs record; otherwise write `[unknown: flagged]` and say the team brings these when it proposes targets). A card's `candidate_solutions` are requests, not the team's ideas: do not copy them into the objective or the reasons.

Name the team that fits best and say in one line per criterion why, quoting the team list. Name any team that fits a criterion better. Never rank teams or problems overall.

### 5. Can they move it?

Check that the chosen team has the access and the levers to change the outcome in the problem, not only to study it. State which lever each part of the outcome needs (a screen, a data feed, a process step, an approval) and whether the team holds it, from its listed areas, technology and data. If a lever sits with another team, the team cannot move the outcome alone: say what is missing and who holds it. Do not invent levers or access; an unknown is `[unknown: flagged]`.

### 6. Shared problems

Derive this from the team list and the problem, not from a note in the statement: a problem is shared when moving the outcome needs a lever, data or area of more than one team (for example one team sees the symptom and another holds the data or the decision). Flag it with `> **Flag:** Shared problem — <teams> — <what each holds>.` Give the lead team as the one named in the objective and the others under "Shared with". Not shared: "none".

### 7. Objectives and key results

Write 1–2 objectives per team, each a problem:

- **Objective:** one qualitative line (verb + measurable thing + for whom) that names no feature, tool or system, taken from the statement's Objective and linked to it. If a team would get more than two, say so and ask which two stay; the rest wait for the next period.
- **Key results:** a primary (an outcome) and a backstop (the guard against hurting something else), taken from the statement's `## Success measures` when written. Statement measures still pending: use the statement's Key results answer, say success-measures has not run, and flag the gap; do not invent measures. Targets are always `team to propose`: set no numbers, and never project revenue, savings, effort or duration.

### 8. Keep-the-lights-on

List under `## Not included (keep-the-lights-on)` the run-the-business work the user or the inputs name (support queues, maintenance, releases, compliance upkeep). It gets no objective and no key result. None named: write that none was named; never invent any. A problem that is really run-the-business work (a recurring chore, an upkeep task with no outcome to move) is not given an objective: say so.

### 9. Record (workspace mode)

- **Objectives file** (write-once): instantiate `_templates/objectives.md` (fall back to the plugin's `templates/objectives.md`) as `objectives/<period>.md`, keeping the derived-template line and the headings, one `## Team:` block per team that received an objective, and the `## Not included (keep-the-lights-on)` section. Remove the template's HTML comment and placeholders. If `objectives/<period>.md` exists, never edit it: write `objectives/<period>-v2.md` (then `-v3`) and add the `revision` decision-log line below.
- **Cards** (append-only body) of each assigned problem: `status: assigned`, `links.objectives: objectives/<period>.md` (the `-v2` file when that is what you wrote), `updated`; append History `- YYYY-MM-DD assigned to <team> by team-objectives (<period>)`. Change no other body line and replace no `_Pending:` line.
- **backlog.md** (living): the card's Status cell `assigned` and Next step `Team proposes targets`. Nothing under `## Focus decisions`.
- **workspace.md** (living): under `## Artifacts` add `- [Team objectives <period>](objectives/<period>.md)`; set `checkpoints_since_decision: 0` and `updated`; move `stage` to `handoff` only if it is earlier (never backwards); put this reply's next step in the next-step line. Append to `## Decision log`, one line per assigned problem: `- YYYY-MM-DD — assigned — P-NNN — <team>, <period>: <one-clause reason>`. A `-v2` file also gets `- YYYY-MM-DD — revision — objectives/<period> — objectives/<period>-v2.md replaces it: <what changed>`. Never edit a past log line.
- Chat-only: give the objectives in the reply under the chat-only notice.

## Output

- Reply, in this order: the file written (or chat-only notice); per team its objective(s), key results (targets: team to propose), the five-criteria reasons (name each of the five criteria in the reply, as in the file, one short line each per team), the can-they-move-it result and any shared-problem flag; problems not assigned and why (not framed, already assigned); the keep-the-lights-on list; what changed (the objectives file, the cards' status, backlog rows, workspace.md).
- Every response ends with a line `**Next suggested step:** <skill or action>`, one step only: the teams propose their targets and review the objectives; problem-statement for an unframed problem that is wanted; or the team list or period when asked for. Never "Next step", never a closing question.

## References

- `${CLAUDE_PLUGIN_ROOT}/references/cagan-principles.md`: objectives as problems, two key results, team-set targets, keep-the-lights-on, Moore and Cagan's selection criteria.
- `${CLAUDE_PLUGIN_ROOT}/references/good-vs-bad-criteria.md`: the criteria for objectives and key results (an outcome, not an activity; solution-free).
- `${CLAUDE_PLUGIN_ROOT}/references/guardrails.md`: the seven guardrails and the standard responses (flag syntax, chat-only notice).

## Guardrails

- Frame fast, never gatekeep: unknowns are flagged and carried; only the team list, the period and, when a team would get more than two objectives, which two stay are asked for, because nothing can be assigned without them.
- Problems, not solutions: objectives and key results name no feature or tool; candidate solutions are not copied in.
- Flag, don't invent: no team, lever, access, idea, key result, number or owner that no source gave; unknowns are `[unknown: flagged]`; user estimates are labelled `user-estimate`. Targets belong to the team.
- Label provenance: objectives, key results, backstop and the five criteria are Cagan's (Moore and Cagan); the objectives file layout is derived.
- Never declare "the most important problem": assignment says nothing about rank, and teams are not ranked.
- Size the problem, not the payoff: no revenue, savings, effort, Ease or duration projection.
- Judgment over process: the leaders and teams decide the assignment; this skill proposes it with reasons.
- Never write to the plugin's install directory. Objectives files are write-once (a revision is `-v2`), card bodies and `## Decision log` are append-only, and no file is deleted.
