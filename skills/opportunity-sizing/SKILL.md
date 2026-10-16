---
name: opportunity-sizing
description: Use when estimating how big a problem is, or roughly how much problems are costing us ('compare the size of P-001 and P-005', 'how big is P-001? build a proper sizing', 'size P-002 and P-003 quickly'). Sizes the problem, never a solution's payoff. Not for choosing which problems to pursue — use problem-focus; not for a go/no-go write-up — use opportunity-assessment.
---

# opportunity-sizing

Sizes problems, in two modes (both non-Cagan, except Cagan's "be conservative"): **quick** compares sibling candidates side by side in bands and ranges; **deep** builds a low/base/high range for one finalist. It sizes the problem (who has it, how often, what it costs them or us today), never what a solution would earn or cost: Cagan says that is unknowable before the solution exists. It compares and never picks; choosing is problem-focus.

## When to use

- Comparing the size of two or more candidates: "compare the size of P-001, P-005 and P-007", "roughly how much is each of these problems costing us?", "size P-002 and P-003 quickly".
- One finalist needs a proper range for a go/no-go or an exec review: "how big is P-001? build a proper sizing", "deep sizing for P-001".
- A re-run with new numbers: the same request again, or the user's answers to a question this skill asked.

## When not to use

- Choosing which problems to pursue ("which of these should we pursue?", "pick the 2–3"): problem-focus. This skill never says which problem to pick.
- The go/no-go write-up for a bet: opportunity-assessment. Deep sizing feeds it.
- Grading evidence (problem-evidence), or changing status, shortlist or not-now (opportunity-backlog).
- Anything about a solution: its revenue, uplift, adoption, cost, effort, Ease or duration. Not sized here, not asked for.

## Inputs

- The cards named (IDs), or, when the request names none ("each of these problems"), every `shortlisted` card, else every `candidate`; say which. Never a `not-now` card unless named.
- Each card's Observations and `quick_size`, `inputs/` files the cards cite, `context.md` (the objective the value serves), `backlog.md`, and the figures the user gives. A card's `candidate_solutions` are never an input.
- Do not stop for anything the request already gives; the one allowed stop is Step 4, except when the request says the sizing feeds an assessment the user has already asked for: then write the brief with every missing figure `[unknown: flagged]` and hand the ranges question back to the caller to ask.

## Steps

### 1. Locate the workspace (problem-workspace → Locate)

Follow Locate in problem-workspace. No workspace and the user declines one, or says not to save anything: **chat-only**. The first output line is `> **Chat-only mode:** nothing is being saved.` Give the same table and notes in the conversation, write no file or folder anywhere, and stay chat-only until the user asks to save or to create a workspace (Locate step 3). A card the user pastes is sized the same way.

### 2. Choose the mode

Two or more cards: **quick**. One card, or the words "deep", "proper" or "for the exec review": **deep**. Deep is for one finalist; "deep" asked of several cards: size them all quick in one table and say that deep mode takes one card, naming it as the next step. One card with no deep wording is deep, and the reply offers a quick comparison with its siblings as the next step. No `context.md`: carry on, and say in one line that strategic-context would give the objective the value serves.

### 3. Read each card for what its evidence shows

The problem line, Interpretation and any existing `quick_size` are claims. Size what the Observations show: a count in a log or sample is a count of that sample, not a count of everyone affected (6 of 40 logged contacts is not a rate across all applicants); a self-report is one person's estimate; a request is not a measurement. Where the problem line is broader than its Observations, size the narrower thing and say so in Assumptions. Earlier figures on the card carry forward with their original basis: a `data` figure is re-checked against its source; a `user-estimate` is the user's own and stays theirs (it cannot be checked against an input, so it is not dropped for that). Never upgrade one.

**Every number is read off an input (name the file and row or location), derived with its arithmetic and inputs shown inline, or given by the user, and carries `basis: user-estimate | data`**. A derived figure (a sum, a share, "above 8 of 12 months", a conversion) is re-counted against the input before it is written: show "<figure> = <a> ÷ <b>, <file> <rows>" in Assumptions, and a count of sources counts only distinct sources that show the claim. A figure with no such trail is `[unknown: flagged]`. That covers every figure in the table, reach and frequency included, not only value per period: write each as `<figure> (basis: data, <source>)` or `<figure> (basis: user-estimate)`. `data` is a record or measurement of events you can count (log rows, an export, tickets, analytics, a CSV); anything people reported (interviews, a request, a salesperson's tally, including how many people said something) and any figure only someone's say-so supports is `user-estimate`. One label per cell: a cell that mixes the two takes `user-estimate`. Rates and frequencies are labelled too. An unknown is `[unknown: flagged]`: never a placeholder, a typical figure, a market number from memory, or a default (a default urgency is an invented urgency). Money appears only where the user or an input gives the rate; otherwise the value stays in its own unit (hours, orders, customers) and the rate is `[unknown: flagged]`.

### 4. No data: ask for ranges, once

A card with no value per period anywhere (no per-period count of the people or cases affected, no cost per occurrence times frequency, no estimate, in its Observations, `quick_size`, the inputs or the request; a count of a sample, such as the rows of a log or the interviewees, is not one): write nothing yet. (Unless the request says the sizing feeds an assessment already asked for: Inputs.) Ask one short message covering every card that lacks one: what you do have per card, then for each missing input (how many are affected per period, how often, the cost of each occurrence, or for an internal problem what today's workaround costs) ask for a low–high range the user is about 90% sure contains the real value. A rough range is enough; "don't know" stays `[unknown: flagged]` and the row says so. End that message with the next-step line, which is answering. When the user answers, size with their numbers, labelled `user-estimate`. The user's answer is the only source for those figures.

### 5. Quick mode

Build the table from `_templates/sizing-quick.md` (fall back to `${CLAUDE_PLUGIN_ROOT}/templates/sizing-quick.md`): one row per card, the template's columns exactly, the ID leading the Problem cell. Read `${CLAUDE_PLUGIN_ROOT}/references/sizing-methods.md` (Quick mode) and follow its recipe and rules; use nothing its table drops.

- Reach, frequency and value per period are ranges or counts with their unit; severity (`low | medium | high`, resting on what the Observations show: how bad, how persistent, any workaround) and urgency (`asap | soon | whenever`, a judgment from a deadline, a worsening trend, a cost that grows each period or the card's own earlier urgency, with the reason in Assumptions) are bands. When nothing at all bears on urgency, the table cell is `[unknown: flagged]` and the card's `urgency` is left empty, never that text: the front-matter holds only `asap`, `soon` or `whenever`.
- **Confidence** is the lower of the card's `confidence` and the ladder band of the figure's basis (`${CLAUDE_PLUGIN_ROOT}/references/evidence-ladder.md`). A `user-estimate` is `estimates and plans`, so never above `low`.
- Problems in different units are not converted, totalled, scored or ranked. Convert only when the inputs give the rate.
- **Assumptions:** where each figure came from, the arithmetic, and what is `[unknown: flagged]`.
- **Which number could change the pick:** the one or two figures that, if they moved, would change which problems you would pick, and the cheapest way to get each. Name them; do not refine the rest. If the user stated a bar, say which problems clear it. Never say which to pick.

### 6. Deep mode

Fill `_templates/sizing-deep.md` (fall back to `${CLAUDE_PLUGIN_ROOT}/templates/sizing-deep.md`) following the procedure in `sizing-methods.md` (Deep mode and Internal problems). Specific rules:

- **Unit of value.** Internal and non-revenue problems use the Cost of Delay value types: Reduce Costs (cost incurred now) or Avoid Costs (cost likely later), written by name; revenue lost today by existing customers is Protect Revenue. Define the affected population narrowly.
- **Inputs are properties of the problem**: people or cases affected, share who hit it, cost per occurrence today. A solution's uptake, lift, payoff, cost, effort or duration is refused in one line, left `[unknown: flagged]`, and the problem-side figure asked for instead.
- **Self-reports bear on the figure: use them.** Derive the range from them in the unit the sources use, label it `user-estimate` and show the arithmetic in Assumptions. Add no conversion factor that no input or the user gave (hours in a working day or week, working weeks, a typical task time, a headcount you assumed): leave the result in the unit it came in (for example a share of the team's time), or ask for the factor. Calendar constants (7 days, 52 weeks) are fine.
- **Low, Base, High** per input from the card, inputs and user (Step 3 rules). A row whose figures are all unknown says what would supply it in its Source cell. **Base is conservative**: where an input rests on a self-report or a single source, Base sits at its conservative end (never the optimistic end or a midpoint of one), and no "x% of a big market" step appears. Say how Base was set. Upside (a wider market, new use) goes only under Upside (flagged), never in Base.
- **Top-down cross-check** from a total the inputs or the user give (all orders, all customers, the whole cost base); the bottom-up result must sit well inside it. No total available: say what is needed and write `[unknown: flagged]`; do not supply one.
- **Swing variable:** flex each input from Low to High, name the one that moves the result most, and give the **cheapest test** that would narrow it: a way to learn about the problem (pull a count, time a handful of cases, ask a few affected people), never a prototype or a solution test, with `timebox: <N> days` (a whole number).
- **Big enough?** Against a threshold the user gives; with none, say the threshold is `[unknown: flagged]`, state the range and its confidence, and ask the calibration question (would a 1 percent change be excellent or a waste?). Not a ranking, not "most important". Note that the range feeds success-measures.
- Missing central inputs, with nothing to derive them from: Step 4. Partial data: write the brief with the gaps flagged and ask for them after.

### 7. Record (workspace mode)

- **Re-running** (the same request again, or new numbers): write `-v2` (then `-v3`) even when the figures come out the same; say "nothing changed" in the note rather than skipping the file, because the user asked again. Never answer from the earlier file.
- **Sizing file:** quick: `sizing/quick-<today>.md`; deep: `sizing/P-NNN-deep.md`. Sizing files are write-once: if the name exists, write `-v2`, then `-v3`, never edit or replace one. Keep the template's derived-template line, its non-Cagan label and the `## Assumptions` section; remove the template comments. No column or figure for effort, Ease, duration or revenue (the Cost of Delay value goes in the Value cell with its unit).
- **Cards** (append-only body): set `quick_size` (`reach`, `frequency`, `severity`, `value_per_period` with `low`, `high`, `unit`, `basis`, and `urgency`; leave `base` empty in quick mode) for each sized card, `links.sizing` to the new file, and `updated`; append History `- YYYY-MM-DD quick-sized by opportunity-sizing (<basis>): <range> <unit> (was: <old range or none>)` (`deep-sized` for deep; deep sets `links.sizing` only and leaves `quick_size` alone). Set every `quick_size` key from the table row so card and file agree: `reach` and `frequency` are the cell's text as written, `[unknown: flagged]` parts included; `severity` is its band; `urgency` is left empty when the cell is `[unknown: flagged]`; `value_per_period` needs `low`, `high` and `basis` together: for one exact count put it in both, and when an end is unknown leave `value_per_period` empty and keep the figure in the table. A card not sized keeps its front-matter. Never change `status`, `confidence`, `problem` or `candidate_solutions`. A card that does not parse is reported and skipped.
- **backlog.md** (living): for each sized card set the Quick size cell to `<low>–<high> <unit> (<basis>)` and the Urgency cell; unknown is `—`. Edit only those cells.
- **workspace.md:** under `## Artifacts` add `- [Quick sizing <date>](sizing/quick-<date>.md)` (or `- [Deep sizing P-NNN](sizing/P-NNN-deep.md)`), set `updated`, move `stage` to `choose` if it is `foundation` or `identify`, add 1 to `checkpoints_since_decision`, and put this reply's next step in the next-step line. A `-v2`, `-v3` file supersedes an earlier sizing: append to the end of `## Decision log` `- YYYY-MM-DD — revision — <P-IDs> — <file> replaces <earlier file>: <what changed>`, never editing a past line. A first sizing is not a decision: no log line. Existing files are never overwritten and nothing is deleted.

## Output

- Workspace mode: the sizing file, the cards' front-matter and History, the backlog cells, `workspace.md`. Chat-only: the table and notes after the notice line.
- Reply: the table (or the deep brief's range and assumptions), the assumptions, which number could change the pick (quick) or the swing variable and cheapest test (deep), what was `[unknown: flagged]` and what you ask for, and the changes per card. Present problems in ID order. Say "problem", "figure" and "range", never "winner" or "best". No score, rank or "most important".
- Every response ends with a line `**Next suggested step:** <skill or action>`, one step only: after quick, problem-focus when the sized cards are shortlisted, else opportunity-backlog to shortlist them; after deep, opportunity-assessment; after a question in Step 4, answering it. Never a closing question after it.

## References

- `${CLAUDE_PLUGIN_ROOT}/references/sizing-methods.md`: Cagan on what can and cannot be sized, the quick recipe and its table rules, the deep procedure, Cost of Delay value types for internal problems, choosing rules, pitfalls. Non-Cagan except its first section.
- `${CLAUDE_PLUGIN_ROOT}/references/evidence-ladder.md`: the confidence bands; a user's own estimate is `estimates and plans`.

## Guardrails

- Frame fast, never gatekeep: size with thin data and flag it; the single stop is Step 4, and a user who says "don't know" gets `[unknown: flagged]`, not a refusal.
- Problems, not solutions: no solution term in a row; `candidate_solutions` are never inputs.
- Flag, don't invent: no figure, rate, total, default or placeholder that no source or user gave; user figures are `basis: user-estimate`, confidence never above `low`; inferences are **Assumption:**.
- Label provenance: sizing methods are non-Cagan; keep the derived-template line.
- Never declare "the most important problem"; no composite score decides, and nothing here ranks or picks.
- Size the problem, not the payoff: no revenue projection, effort, Ease, duration or CD3; Cost of Delay is a cost of the problem today.
- Judgment over process: severity, urgency and Base are judgments you explain; the numbers inform, they do not decide.
- Never write to the plugin's install directory. Sizing files are write-once, `## Decision log` is append-only, existing card lines are never overwritten, and no file is deleted.
