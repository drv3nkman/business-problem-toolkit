---
name: strategic-context
description: Use when capturing or summarizing the strategic context behind problem work — product vision, company objectives, scorecard or KPIs, OKRs, focus areas, known constraints — or when checking whether a strategy exists at all. Not for setting up or locating the working folder — use problem-workspace.
---

# strategic-context

Captures the strategy a problem has to serve, and the gaps in it, in `context.md`. Cagan: problems come from strategy, not stakeholder requests, so this comes before discovery and framing. It records what the documents say. It never makes a strategy up.

## When to use

- The user supplies or points at a strategy deck, vision, company objectives, OKRs, a scorecard or KPIs, and wants the context for problem work pulled out.
- The user asks whether a strategy exists ("Do we even have a product strategy? Check these docs").
- A team has an assigned objective or focus area and wants it recorded before framing ("Capture our team's objective and focus area"). This is **light** mode.
- Another skill needs context and there is no `context.md` (problem-focus needs at least light context).

## When not to use

- Creating, finding or importing into the working folder: use problem-workspace.
- Finding or listing candidate problems in notes, tickets or data: use problem-discovery. This skill never lists candidate problems.
- Framing a problem for a team: use problem-statement. Setting a team's objective and key results: use team-objectives.

## Inputs

- Whatever exists: vision, company or team objectives, scorecard or KPIs, OKRs, strategy documents. Pasted text, files named in the request, or files in the workspace `inputs/`.
- The mode, decided in this order: (1) the mode the caller or the user names (`full` or `light`); (2) else `light` when the manifest says `mode: team`; (3) else `full`. Light captures only the objective and the focus area.
- Do not stop to ask for what the files already give.

## Steps

### 1. Locate the workspace (problem-workspace → Locate)

Follow Locate in problem-workspace. Read `workspace.md` for `mode`. No workspace and the user declines one: **chat-only**. The first output line is `> **Chat-only mode:** nothing is being saved.` Give the same content in the conversation, write no file anywhere, and stay chat-only until the user asks to save or to create a workspace (Locate step 3).

### 2. Read the inputs

1. Pasted material first, then every file in `inputs/`, but only enough of each to know what it is. Strategy documents, OKRs, decks and scorecards are the sources. Metrics exports are read only to say where a stated objective stands today.
2. A file you cannot read (image, scanned PDF, binary) is listed as "not read" with the reason. Never describe what it might contain.
3. Interviews, tickets, request lists, churn notes and similar are not strategy. Use them only as "today" evidence for a gap, cited by file. Never mine them for problems, and never copy a requested solution into the context.
4. **Authority.** Strategy comes from leadership's strategy documents or statements. An executive email, a request list or a sponsor's assertion ("this is our #1 problem") with no strategy behind it is not an objective or a focus area (Cagan: problems come from strategy, not stakeholder requests). Record it as a flag: stated without evidence or without a strategy behind it, so a hypothesis for discovery. A team objective the user states in chat is the objective, and is attributed to the user.

### 3. Fill the template

Start `context.md` from `_templates/context.md` in the workspace; if it is missing, fall back to reading `${CLAUDE_PLUGIN_ROOT}/templates/context.md`. Set `mode: light` or `mode: full`. Replace the title placeholder with the initiative name, keep the derived-template line, remove the HTML comments and every angle-bracket placeholder. Quote the user's own words, with the source (a file in `inputs/` or "conversation") on every item. Never invent a vision, objective, scorecard figure, target or constraint. Anything not given is `[unknown: flagged]`.

**Full mode**, in this order:

1. **Vision:** the vision in the source's words, with its horizon. The horizon comes from the source; Cagan's reference is 3–10 years, but never fill a horizon the source does not give (write `[unknown: flagged]`).
2. **Objectives and scorecard:** objectives and the KPIs that measure them, each with its source. No scorecard or no target: say so, and write the missing figure as `[unknown: flagged]`. A metrics export that measures the objective may be quoted, named and labelled as not a stated scorecard.
3. **Focus areas:** the areas the strategy says to concentrate on, and the team's assigned objective or focus if there is one.
4. **Known constraints:** legal, financial, partner, brand, ethical or other limits already stated, as limits on the problem and never as solutions. A deadline is not a constraint on the problem; keep it apart.
5. **Gaps:** two kinds only, each with the input it came from:
   - *Vision versus today:* what the vision describes against what the inputs show now.
   - *Scorecard miss:* an objective's measure against its target, or, with no target, against the direction the objective states (write the target as `[unknown: flagged]` and say the distance cannot be given).
   - Gaps are seeds for discovery. List them; never rank them or say which matters most. A gap is not a candidate problem and never contains a solution. If there is no vision or no scorecard, say that gap type cannot be assessed and why; do not substitute interview findings.
6. **Flags:** each as `> **Flag:** <text>`. See below.

**Light mode:** fill only **Objectives and scorecard** and **Focus areas**, from what the user said and any strategy file. Vision, Known constraints and Gaps each hold exactly `_Not captured (light mode)._` and nothing else. No gap analysis, no reading beyond what the objective and focus need. Flags still apply.

### 4. Flags and questions

1. **No strategy.** If there is no strategy document or leadership statement (vision, company objectives or focus), the Flags section holds this exact line (`${CLAUDE_PLUGIN_ROOT}/references/guardrails.md`, *Standard responses*):

   `> **Flag:** No product strategy provided — Cagan calls this 'no strategy'.`

   Then fill every section with what exists and `[unknown: flagged]` for the rest. An absent strategy never stops the work.
2. Other flags: conflicts between sources, an unsupported executive claim, undefined metrics, unreadable files. Remove the template's placeholder flag line if there is nothing to flag.
3. **Questions: at most 3, in one message, then proceed.** Write `context.md` first. Then, in the chat reply, ask up to three questions on what is missing and would change the context (for no strategy: vision and horizon, the objective or KPI the team answers for, known constraints). Ask none if the inputs answer them. Never wait for the answers. Record each unanswered question as `> **Flag:** Open question: …`. When answers come, write `context-v2.md` (below).

### 5. Write, never overwrite

`context.md` is write-once. Before writing, Glob the workspace for `context*.md`.

- None: write `context.md`.
- `context.md` exists and the inputs and conversation give nothing new: write nothing, report what it holds and offer a `-v2`. Something new (answers to the open questions, a new strategy file): write `context-v2.md` (`-v3` if that exists), never change the old file, and append one line to `## Decision log` in `workspace.md`: `- YYYY-MM-DD — revision — context.md — wrote context-v2.md: <what changed>`.
- Then in `workspace.md`: add `- [Context](context.md)` (or `- [Context v2](context-v2.md)`) under `## Artifacts` and set `updated`. A first context is not a decision, so it gets no decision-log line. Leave `stage` and every other line alone.

### 6. Report

Summarize in chat: mode, the source of each item, the flags raised, the gaps (as a list) and the questions. Do not rank gaps and do not name a most important problem.

## Output

- `<workspace>/context.md` (or `context-v2.md`, `-v3`), `mode: light | full`, built from the context template.
- A new Artifacts link and `updated` in `workspace.md`; a `revision` line only for a revision.
- Chat-only: the same content in the conversation, after the notice line.
- Every response ends with a line `**Next suggested step:** <skill or action>`. After full context: problem-discovery. After light context on an assigned problem: problem-statement. With no strategy flag: problem-discovery (it will carry the flag), and answering the open questions to write `context-v2.md`. Never "Next step" and never a closing question.

## References

- `${CLAUDE_PLUGIN_ROOT}/references/cagan-principles.md`: strategy as the source of problems, focus, vision horizon, team objectives.
- `${CLAUDE_PLUGIN_ROOT}/references/insight-sources.md`: the four insight types and what each input can and cannot show.
- `${CLAUDE_PLUGIN_ROOT}/references/guardrails.md`: the exact no-strategy flag and chat-only notice (*Standard responses*).

## Guardrails

- Frame fast, never gatekeep: missing strategy is a flag and open questions, not a stop. At most 3 questions, once.
- Problems, not solutions: requested solutions never enter the context; gaps are not candidate problems.
- Flag, don't invent: no vision, objective, KPI, target or constraint that no input states. Unknowns are `[unknown: flagged]`; user estimates are labelled as user estimates.
- Label provenance: keep the derived-template line; cite the input for every item.
- Never name "the most important problem"; gaps are listed, not ranked.
- Size the problem, not the payoff: no revenue projections, effort or duration.
- Judgment over process: the context prompts discovery; it does not decide what to work on.
- Never write to the plugin's install directory. `context.md` is write-once: a revision is `context-v2.md` plus a decision-log line.
