---
name: viability-constraints
description: Use when listing the business constraints any solution must satisfy ('what constraints must any solution satisfy?') — legal and compliance, unit economics, sales channel, partner contracts, brand, ethics, dependencies — either as a quick deal-breaker screen on a candidate problem or as the full bar for a framed problem statement. Never evaluates a specific solution (not 'will this design pass legal?'); not for grading evidence — use problem-evidence.
---

# viability-constraints

Lists what the business requires of *any* solution to a problem, so the limits are known before solutions are explored. Two modes: **screen** (a yes/no deal-breaker list on a candidate card) and **full** (the seven-category bar inside a framed problem statement). It records constraints on the problem. It never judges a solution, a design or a feature: that is what discovery of solutions does later, against the four big risks (`cagan-principles.md`). Cagan's business-viability risk, plus ethics as the proposed fifth, supplies the categories.

## When to use

- A quick screen of a candidate: "screen P-002 for deal-breakers", "any deal-breakers on P-004 before we shortlist it?" (**screen**).
- The bar for a framed problem: "what constraints must any solution to P-005 satisfy?", "write the full viability constraints for P-005" (**full**).
- A named subset ("list legal, brand and channel constraints for this problem"): the same work, with the named categories first and the rest still listed.
- Pasted problem text in chat with no workspace (**chat-only**).

## When not to use

- Evaluating a solution: "will this SSO design pass legal?", "is this feature compliant?", "does the vendor contract work?". Nothing here judges a solution. Decline in one line and reframe (Step 2).
- Grading evidence (problem-evidence), sizing (opportunity-sizing), shortlisting or parking (opportunity-backlog), the go/no-go write-up (opportunity-assessment) or drafting the statement (problem-statement).
- Success measures (success-measures) and the statement's review (problem-review).

## Inputs

- **Screen:** the card (`cards/P-NNN-*.md`): problem line, Observations, Interpretation, `who`, `origin`. **Full:** the statement `links.statement` names (else the highest `statements/P-NNN-vN.md`, else `statements/P-NNN.md`) and its card; if the card's link is stale (it names `statements/P-NNN.md` while a `-vN` file exists), say so and use the latest file.
- Where constraints can come from: `context.md` (`## Known constraints`, objectives, focus), the `inputs/` files the card or statement cites (strategy, process and team notes), and what the user says. Teams and functions named in `inputs/` (a teams file) supply who to consult.
- A card's `candidate_solutions`, and any feature, product or vendor the user names, are **never** an input: constraints come from the problem and its setting, not from a design.
- Do not stop for anything the request already gives.

## Steps

### 1. Locate the workspace (problem-workspace → Locate)

Follow Locate in problem-workspace. No workspace and the user declines one, or says not to save anything: **chat-only**. The first output line is `> **Chat-only mode:** nothing is being saved.` Give the same content in the conversation for the problem the user pasted or named, write no file or folder anywhere, and stay chat-only until the user asks to save or to create a workspace (Locate step 3).

### 2. Choose the mode; decline solution evaluation

- A request that asks whether a *solution* passes, complies or is acceptable names no problem constraint: do not answer it, and do not estimate how it would fare. Say in one line that this skill lists what any solution must satisfy and does not evaluate one, then do the problem's work: if the request or the card's History ties it to a problem, run that problem's mode (below); otherwise the next step is to name the problem it serves. A solution word in the request never enters a constraint or the file.
- Names cards and the request is a screen ("screen", "deal-breakers", a shortlist question), or the card is not framed: **screen**. A statement exists for the problem and the request wants the constraints or "the bar": **full**.
- **Full with no statement** (no statement file for the ID): say so, write nothing, and make the next step problem-statement. Do not draft a statement or the section. Mention that a quick screen of the card is available. In chat-only mode a pasted problem needs no statement: give the seven categories in the conversation.
- Several cards: do each; the reply keeps ID order.

### 3. Gather constraints from what is there

Read the card or statement, `context.md` and the inputs they cite. A constraint is a limit the business, a regulator, a contract or a promise already imposes, stated as what *any* solution must satisfy ("any change must keep EU customer data in-region").

- **Cite the source** for each constraint: a quoted phrase and the file and location (`inputs/strategy.md, Constraint`), or "you said". Quote what the input says; do not restate or extend it.
- **Never invent a legal or contractual fact.** Name no law, regulation, standard, clause, fine, deadline, fee, rate or threshold that no input or the user gave. When an input implies a constraint without saying how it applies (a data rule and an unnamed region), state what the input says and write the rest as `[unknown: flagged]`, with who can settle it.
- Card problem lines can overstate their evidence (they are claims, graded against Observations by problem-evidence): take constraints from the inputs and context, not from the card's Interpretation. A card with no cited input and no context has few constraints: say that, do not fill the gap.
- Every constraint is about the problem's setting. A constraint that only makes sense for one design is a solution detail: leave it out.
- A constraint no input states but the problem's setting suggests (who could be harmed, who must approve) is an inference: begin it **Assumption:** and cite what it rests on. Never write an inference as if an input said it, and never write a rule ("data must not be shared beyond…") that no source gave.

### 4. Screen mode

Seven deal-breaker questions per card, in this order, each answered **yes** or **no**:

1. Legal / compliance
2. Financial / unit economics
3. Sales channel / go-to-market
4. Partner contracts
5. Brand
6. Ethics
7. Dependencies

A **deal-breaker** is a constraint, known from an input or the user, that any solution must clear and that could stop the work if it cannot be cleared. Answer **yes** when one is known: say what it is, cite it, state its reach, name who to consult. Answer **no** when nothing in the card, context, inputs or the user's words points to one; **no** means "none known", never "none exists", so where the inputs are silent on a category the line says `[unknown: flagged]` and who would know.

- **Reach** is whether the constraint is known to apply to *this* problem. `reach: established` when the card, its cited inputs or the user tie it to this problem (the problem's own data, people, contract or margin), with what ties it. `reach: [unknown: flagged]` when an input states the constraint but nothing shows it touches this problem (a data rule and a region or data set the card never mentions), with what is unknown. An in-region data rule, a margin floor or a contract exclusivity found in an input is still a **yes** when its reach is unknown: it is the check this skill exists to raise, and its reach line says so.
- **What a yes with each reach means downstream.** opportunity-backlog, problem-focus and opportunity-assessment treat a yes with `reach: established` as a deal-breaker for the card (suggest not-now; do not choose unless the user names it; no-go unless the user overrides). A yes with `reach: [unknown: flagged]` is a flag carried on the card, with who settles it: it never blocks the card.
- **Dependencies.** An ordinary dependency (the problem sits in a system another team owns, another function runs the process, the team needs another team's help) is not a deal-breaker: answer **no**, and leave it to "can the team move it" in problem-focus and to the Dependencies category in full mode. Answer **yes** only when an input or the user says the dependency can stop the work (a freeze, a refusal, a contract that rules the change out).

Each line is plain and parseable, because opportunity-backlog, problem-focus and opportunity-assessment read it:

`- <Category> deal-breaker: yes — <what the constraint is; source>; reach: established — <what ties it to this problem>. Consult: <role>`
`- <Category> deal-breaker: yes — <what the constraint is; source>; reach: [unknown: flagged] — <what is unknown>. Consult: <role>`
`- <Category> deal-breaker: no — <none known from X; [unknown: flagged] if unchecked>. Consult: <role>`

A yes line uses exactly one of the two `reach:` forms.

Under the answer lines add nothing about solutions, effort or size.

### 5. Full mode

Fill `## Viability constraints` of the statement with seven H3 categories, in this order, with these headings: `### Legal and compliance`, `### Financial and unit economics`, `### Sales channel and go-to-market`, `### Partner contracts`, `### Brand`, `### Ethics`, `### Dependencies`.

- Each holds bullets, each a constraint written as what any solution must do, keep or respect ("Any solution must …"), with its source (Step 3): a plain fact about the setting that no solution has to satisfy is not a constraint, so leave it out. Each category **ends with a line `Consult: <role>`**: the team or function from `inputs/` (a teams file, context) when one fits, else a generic function (legal counsel, finance partner, sales leadership, partner or procurement manager, brand lead, an ethics or privacy reviewer, the owner of the system or team depended on). Never an invented person's name.
- A category with nothing in the inputs holds exactly one line, `No constraint known from the inputs. [unknown: flagged]` (add what is unknown and who would know), never a bullet saying what the inputs lack in other words, and still ends with `Consult:`.
- *Financial and unit economics*: constraints on cost to serve or margin that the objective, context or user states; unknown figures stay `[unknown: flagged]`. *Dependencies*: the teams, systems or data the problem sits across (for example the teams file), as what any solution must work with or involve ("Any solution must work within the billing system, which the finance team owns"), not as tasks and not as a description of the teams. *Ethics*: like every category, each bullet is what any solution must do or avoid, never a statement of a risk: `Any solution must not disadvantage <who> <how>.` followed by `**Assumption:** <why they could be harmed, from the problem's who and setting>.`, unless an input states a policy (then cite it, with no **Assumption:**).
- Say nothing about how a constraint would be met.

### 6. Record (workspace mode)

- **Screen:** replace the one `_Pending: run viability-constraints (screen mode)._` line in `## Viability screen` with `Screened YYYY-MM-DD (viability-constraints, screen mode):` and the seven lines. A card already screened: never edit its earlier lines; append below them `Re-screened YYYY-MM-DD:` and a new set of seven lines. An earlier **yes** is carried forward (with its source, or "earlier screen" if it had none, and its reach) unless the user or an input says it is cleared; never turn a yes into a no because this run found no source for it. Its reach may move from `[unknown: flagged]` to `established` (or back) only on what an input or the user says. The answer lines stay plain `yes` or `no` answers: note any answer that changed on a separate line after the seven, `Changed since the last screen: <Category> was yes, now no; <what cleared it>.`, never on the answer line. Card bodies are append-only, so the earlier lines stay exactly as written; opportunity-backlog, problem-focus and opportunity-assessment read only the latest block, which is why every Re-screened block repeats all seven answers. Append to History `- YYYY-MM-DD viability-screened by viability-constraints: <N> deal-breaker(s) answered yes`; set `updated`. Never change `status`, `problem`, `confidence`, `candidate_solutions` or any other body line.
- **Full:** replace the one `_Pending: run viability-constraints._` line in that statement file with the seven H3 categories; change nothing else in the statement. A section that is already filled is never edited: add a `**Update YYYY-MM-DD:**` paragraph at the end of the section with the changed constraints. Append to the card's History `- YYYY-MM-DD viability constraints written to <the statement file written>`; set `updated`.
- `workspace.md` (living): set `updated` and put this reply's next step in the next-step line. Screen: move `stage` to `choose` if it is `foundation` or `identify` and add 1 to `checkpoints_since_decision`. Full: move `stage` to `define` if it is earlier and leave the counter as it is. Writing constraints is not a decision: no Decision log line. `backlog.md` is not touched. Existing files are never overwritten and nothing is deleted.

## Output

- Workspace mode: the changed card(s) or statement and `workspace.md`. Chat-only: the lines or categories in the conversation after the notice line.
- Reply: per card or statement, the answers (screen: all seven, each yes or no; full: the seven categories and who to consult, briefly), each deal-breaker answered yes with its source, its reach (established, or `[unknown: flagged]` and so a flag, not a block) and whom to consult, what is `[unknown: flagged]`, and what changed. A yes means "settle this with the person named", never "drop the problem" and never a ranking; a not-now that problem-focus records on a deal-breaker is parking with a revisit trigger, not dropping. Present cards in ID order. No score, size, rank or "most important".
- Every response ends with a line `**Next suggested step:** <skill or action>`, one step only: after a screen with a yes, consulting the named role about it; after a screen with no yes, opportunity-backlog (shortlist) for a candidate, problem-statement for a chosen or assessed card; after full, success-measures if the statement's Success measures section is still pending, else problem-review; a statement missing: problem-statement; a solution-shaped ask: name the problem it serves. Never a closing question after it.

## References

- `${CLAUDE_PLUGIN_ROOT}/references/cagan-principles.md`: the four big risks plus ethics (viability and ethics supply the categories), and the rule that recording viability constraints up front is part of framing; the risks themselves are tested against solutions later, not here.

## Guardrails

- Frame fast, never gatekeep: constraints from what is there, unknowns flagged; a missing category is `[unknown: flagged]`, not a reason to refuse.
- Problems, not solutions: constraints on any solution; never evaluate one, never use `candidate_solutions`, never let a user-named design shape a constraint.
- Flag, don't invent: no legal fact, law, clause, figure or deadline no input or user gave; the cited source is shown; inferences are **Assumption:**.
- Label provenance: statement sections keep the template's derived-template line; these categories are the plugin's (derived from Cagan's viability risk plus ethics), not a Cagan template.
- Never declare "the most important problem": a screen answer is not a ranking and a yes is not a verdict on the problem.
- Size the problem, not the payoff: no revenue, effort, cost or duration estimate for meeting a constraint.
- Judgment over process: whether a constraint is a deal-breaker is a judgment the user can overrule; say why you answered as you did.
- Never write to the plugin's install directory. Card and statement lines are never overwritten (only `_Pending:` lines are replaced), `## Decision log` is append-only, and no file is deleted.
