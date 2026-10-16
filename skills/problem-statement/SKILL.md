---
name: problem-statement
description: Use when writing, drafting or redrafting a problem statement or team objective for a chosen or assigned problem — the solution-free objective, Cagan's four questions, strategic trace, evidence and open assumptions ('frame this problem', 'our team was given X, write it up', 'redraft P-005's statement'). Not for critiquing an existing statement — use problem-review.
---

# problem-statement

Turns a chosen or assigned problem into a framed statement: a one-line, solution-free objective, Cagan's four questions (2017) answered, the strategic trace, the evidence and the open assumptions. Before it finishes it runs problem-review on its own draft. The statement is a starting point, not a contract, and it never decides whether the problem is worth solving. The template is derived: Cagan publishes no problem-statement template.

## When to use

- "Frame P-001", "redraft P-005's statement with a different objective" (a new `-v2` file, never an edit of the saved statement), "write up P-003 as a statement", "our team was given 'reduce onboarding time' — write it up", "draft the team objective for this problem".
- A card that is `chosen` or `assessed`, or a problem a leader has assigned (a card, or text in the conversation).

## When not to use

- Critiquing a statement or OKR that already exists: problem-review.
- A solution-shaped request ("the CEO wants SSO"): reframe-request first; frame the problem it uncovers.
- Success measures or key-result values (success-measures), constraints (viability-constraints), a customer letter (customer-letter), choosing among problems (problem-focus).
- Re-gating an assigned problem. A team given a problem frames it; it does not argue whether it deserves the work.

## Inputs

- **A card** named by ID or described ("the credit-hold problem"; say which card you took), normally `chosen`, `assessed` or `shortlisted`. Read the card (Observations, Interpretation, `confidence`, `## Evidence` if graded), `context.md` (latest `context*.md`), the assessment and sizing it links, and the `inputs/` files it cites.
- **Raw text:** an assigned problem or objective in chat. Use only what it says.
- A card's `problem` line is a claim, not proof. Ground the statement in its Observations and Evidence; anything the Observations do not show goes in as `**Assumption:**`, never as a fact.
- Do not stop to ask for what is missing. A missing objective, customer or trace becomes `[unknown: flagged]` or an Open assumption.

## Steps

### 1. Locate the workspace (problem-workspace → Locate)

Follow Locate in problem-workspace. A bare `P-NNN` names the card `problem-work/<slug>/cards/P-NNN-*.md` in the located workspace; look there and do not ask which file when it exists. No workspace and the user declines to create one, or the user says not to save anything: **chat-only**. The first output line is then `> **Chat-only mode:** nothing is being saved.` Write no file or folder anywhere and stay chat-only until the user asks to save or to create a workspace (Locate step 3).

### 2. Take the problem

Read the card, the context and the cited inputs (Inputs above). Note the card's status and whether a `statements/P-NNN.md` already exists. A card that is `candidate` or `not-now`: frame it if asked and say its status in the reply (Step 6 sets the status it ends with: a `candidate` card becomes `framed`, a `not-now` card stays `not-now`). If the problem is a solution in disguise, say so, name reframe-request, and frame the underlying problem only if the card already holds it.

### 3. Draft the objective

One line, no more: **verb + measurable thing + for whom** ("Reduce the time a new customer takes to send a first invoice"). The thing is measurable but the quantity is not here: key results and targets belong to success-measures. No feature, tool, technology, vendor or deliverable (describe the work, not the system it happens in: "re-keying emailed purchase orders", not "keying into the ERP"), and none of the card's `candidate_solutions`. All three parts are in the line: the thing is something a measure could count or time (a duration, a count, a rate), never "effort" or "experience", and "for whom" names the group in the card's `who` or the user's words, ending "for <who>" or "... a <who> takes ...", not just "rep time". Keep it short enough to read aloud; qualifiers go in the questions below.

### 4. Answer the four questions

Answer the 2017 set in `${CLAUDE_PLUGIN_ROOT}/references/question-sets.md`, in its order, each in a sentence or two: Objective (the business objective it addresses, from `context.md` or the user's words), Key results (outcomes, no targets; "targets come from success-measures"), Customer problem (the customer's problem, from the Observations), Target market (who: the card's `who`). Use the exact bold labels from the template. **Requests are not quoted.** An Observations row of kind `stakeholder assertion`, or one that comes from an origin of kind `request`, may name a solution someone asked for: take from it only who is affected and the situation they are in, and quote none of its words that name or describe a requested thing (the feature, product, tool or change asked for). The same applies to every section of the statement. No section says that anyone asked for anything; describe the situation, never the request or its subject. State no figure that no source gave. Each answer states only what the card's Observations, the context or the user's words show. A customer effect, a cause or an outcome that they do not show (a customer waiting, errors reaching an order, a measure that will fall) goes in the same sentence as `**Assumption:**`, never as a plain fact: "the problem line says so" is not evidence, and a plausible inference is still an assumption.

### 5. Trace, evidence, assumptions

- **Strategic trace:** the focus area or objective this serves and where it comes from (a quoted line of `context.md`, or "assigned by the user in this conversation"). Never invent a company objective. No strategy on file: say so and carry `> **Flag:** No product strategy provided — Cagan calls this 'no strategy'.` (or the context's own flag).
- **Evidence:** link the card (`[P-NNN card](../cards/<file>)`), state its evidence verdict if it has one and its confidence band, and say what the Observations show and do not show. Thin evidence is a flag and a learn-next item, never a reason to stop.
- **Open assumptions:** what the statement assumes beyond the Observations, each `**Assumption:**` with what would confirm it, plus every `[unknown: flagged]`. At least one line, even if only "none beyond the card".

Check the draft against `${CLAUDE_PLUGIN_ROOT}/references/good-vs-bad-criteria.md` (the seven criteria) before writing it down.

### 6. Record (workspace mode)

- **Statement file:** instantiate `_templates/statement.md` (fall back to `${CLAUDE_PLUGIN_ROOT}/templates/statement.md`) as `statements/P-NNN.md`, keeping the derived-template line and every heading. Fill Objective, Four questions, Strategic trace, Evidence and Open assumptions. Leave the `## Success measures`, `## Viability constraints` and `## Review` placeholders as `_Pending: ...` lines: success-measures, viability-constraints and problem-review each replace their own. Do not fill them, and do not copy the template's comments or placeholders.
- **Already exists:** statements are append-only. Never edit or replace `statements/P-NNN.md`. A redraft is `statements/P-NNN-v2.md` (then `-v3`), a complete new statement made from the template, with its own `## Review` line. A redraft is append-only like the first statement: later skills fill its pending sections in place.
- **Card** (append-only body): `status: framed` when the card is `candidate`, `shortlisted`, `chosen` or `assessed`; an `assigned` or `not-now` card keeps its status. `links.statement` to the file, `updated`. Append History `- YYYY-MM-DD framed by problem-statement (was: <status>)`; for a `-v2`, `- YYYY-MM-DD re-framed by problem-statement (statements/P-NNN-v2.md)` and `links.statement` points to the new file. Change no other line and replace no `_Pending:` line of the card.
- **No card yet** (an assigned objective given in chat or by `context.md`, in a workspace): create the card first, from `_templates/card.md` (fall back to `${CLAUDE_PLUGIN_ROOT}/templates/card.md`), keeping every front-matter key (`not_now` included) and every section heading of the template; ID = the highest `P-NNN` ever used plus one, counting card file names and every ID in `workspace.md`'s `## Decision log` (a merged-away ID is still used), never a reused one; `status: assigned` (leadership assigned the problem to the team; `links.objectives` stays empty until team-objectives records which team), `origin` of kind `stakeholder` citing where the objective was given, `discovered_in` empty, `quick_size` and `not_now` left as the template has them; add its row to `backlog.md` (Status `assigned`) and link it under `## Artifacts`. The Evidence and Viability screen sections keep their `_Pending:` lines.
- **backlog.md** (living): the card's Status cell and Next step cell only.
- **workspace.md:** under `## Artifacts` add `- [Statement P-NNN](statements/P-NNN.md)`; set `updated` and leave `checkpoints_since_decision` as it is; move `stage` to `define` only if it is `foundation`, `identify` or `choose` (never backwards); put this reply's next step in the next-step line. A first statement for a card writes no decision-log line (framing is not one of the logged decisions). A `-v2` appends `- YYYY-MM-DD — revision — P-NNN — statements/P-NNN-v2.md replaces statements/P-NNN.md: <what changed>`. Never edit a past log line.

### 7. Run problem-review on the draft

Before finishing, always invoke the problem-review skill on the statement you just wrote. In a workspace, hand it the file path (`statements/P-NNN.md`, or the `-v2` file); problem-review records its result in that file's `## Review` section, so do not fill that section yourself. In chat-only mode, hand it the drafted statement; the review is chat-only too. Do not skip it, shorten it or replace it with your own self-check, and do not tell the user it is optional. Then read the verdict: `ready` means fit to hand on as written, not a judgement of importance; `revise` or `reframe` is reported as it stands. If the verdict is `revise` and the fix is a plain rewrite the review suggested, say so and offer a redraft; do not silently rewrite a statement that is already saved.

### 8. New bet

If the problem is a new product or market bet (the user says so, or the card is a new-product or new-market opportunity a leader is choosing and no assessment exists), end the reply with `**Next suggested step:** opportunity-assessment` and one sentence on why (market, competition and go/no-go are leader questions the four questions drop). A problem assigned to a team inside an existing product or process is not a new bet.

## Output

- Workspace mode: `statements/P-NNN.md` (or the `-v2`), the card, the backlog row and `workspace.md`; the review's result sits in the statement. Chat-only: the whole statement and the review in the conversation, same shape and headings, starting with the chat-only notice.
- Reply, in this order: the objective line; the four questions' answers in brief; the trace; the review's verdict and its main flags; the open assumptions; what changed per file ("only the card, backlog and workspace.md, plus the new statement"). Say the four questions are Cagan's (2017) and the template is derived; the derived-template line `*Derived template — Cagan publishes no problem-statement template.*` appears in the statement and in a chat-only draft.
- Every response ends with a line `**Next suggested step:** <skill or action>`, one step only, the first that applies: a new bet: opportunity-assessment; a `reframe` verdict: reframe-request on the statement's text; a `revise` verdict: problem-statement to redraft P-NNN with the review's rewrites (chat-only: apply them and send it back for another review), or problem-evidence for P-NNN when the evidence row is the only fail or flag; otherwise success-measures for P-NNN (then viability-constraints). Never "Next step", never a closing question.

## References

- `${CLAUDE_PLUGIN_ROOT}/references/question-sets.md`: the 2017 four questions and Cagan's guidance on each, and which question set fits which situation.
- `${CLAUDE_PLUGIN_ROOT}/references/good-vs-bad-criteria.md`: the seven statement criteria and the form of a statement.
- `${CLAUDE_PLUGIN_ROOT}/references/guardrails.md`: the seven guardrails and the standard responses (flag syntax, derived-template line).

## Guardrails

- Frame fast, never gatekeep: thin evidence is flagged and carried into Open assumptions, an assigned problem is not re-gated, and the review's verdict informs the user without blocking the file.
- Problems, not solutions: the objective names no feature or tool; `candidate_solutions` stay on the card and never enter the statement.
- Flag, don't invent: no customer, objective, figure, baseline or target that no source gave; unknowns are `[unknown: flagged]`; a guess about the problem is an `**Assumption:**`; the card's problem line is graded against its Observations, not trusted.
- Label provenance: the four questions are Cagan's (2017); the statement template is derived and says so; the review's rating and verdict rule are derived.
- Never declare "the most important problem": framing a problem says nothing about its rank.
- Size the problem, not the payoff: no revenue projection, effort, Ease or duration in the statement.
- Judgment over process: the questions prompt thinking; the user decides what the statement says.
- Never write to the plugin's install directory. Statements are append-only (a redraft is `-v2`), `## Decision log` is append-only, existing card lines are never overwritten, and no file is deleted.
