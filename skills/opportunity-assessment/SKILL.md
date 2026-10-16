---
name: opportunity-assessment
description: Use when a leader needs a one-page go / no-go / go-to-discovery assessment of a single new product or market bet, using Cagan's opportunity-assessment questions. Not for choosing among several candidate problems — use problem-focus; not for framing a problem already assigned to a team — use problem-statement.
---

# opportunity-assessment

Writes the one-page assessment of one new product or market bet: Cagan's ten questions (2006, "Assessing Product Opportunities"), answered from the card, the deep sizing, the context and the viability work, ending in a recommendation: go, no-go or go to discovery, with named risks. It assesses the problem behind the bet, never a solution: no revenue projection, effort, Ease or duration. Cagan says what a solution will earn or cost is unknowable before the solution exists; ruling out effort, Ease and duration as well is this plugin's guardrail. It recommends; the leader decides, and the recommendation is not a ranking against other problems.

## When to use

- A leader wants a go/no-go on one bet: "write the opportunity assessment for P-002", "should we go after the new-region bet? give me a go/no-go", "assess this new market opportunity".
- A chosen card whose bet is new to the company (a new product, segment or market), after problem-focus or on its own.
- A revised assessment when the sizing, the screen or the facts changed (a `-v2`, Step 7).

## When not to use

- Choosing among several candidate problems, or "which of these should we do?": problem-focus.
- Framing a problem a team has been assigned (the 2017 four questions): problem-statement.
- Sizing alone (opportunity-sizing), grading evidence (problem-evidence), listing constraints (viability-constraints).
- A brand-new business whose distribution and monetization are open: a canvas, outside this plugin's v1 (`question-sets.md`).

## Inputs

- **One card** (`cards/P-NNN-*.md`), named by ID or described ("the new-region bet"; say which card you took). Normally `chosen`. A `candidate` or `shortlisted` card is assessed too (say its status). A `not-now` card only when named, showing its not-now reason. Several cards named: this skill assesses one bet; ask which, and name problem-focus if the question is which to pursue. A bet the user describes that no card holds: say so and name reframe-request to make the card; in chat-only mode answer for the pasted description.
- `sizing/P-NNN-deep.md` (latest `-vN`) via the card's `links.sizing`; `context.md` (latest `context*.md`); the card's `## Viability screen`; the `## Viability constraints` of the statement `links.statement` names (else the highest `statements/P-NNN-vN.md`, else `statements/P-NNN.md`); if the card's link is stale (it names `statements/P-NNN.md` while a `-vN` file exists), say so and use the latest file, if a statement exists; `backlog.md`, `workspace.md`, and the `inputs/` files the card cites.
- A card's `candidate_solutions` are never an input. The card's problem line is a claim: read its Observations and `confidence`.

## Steps

### 1. Locate the workspace (problem-workspace → Locate)

Follow Locate in problem-workspace. No workspace and the user declines one, or says not to save anything: **chat-only**. The first output line is `> **Chat-only mode:** nothing is being saved.` Answer the ten questions in the conversation for the bet the user pasted or named, write no file anywhere, and stay chat-only until the user asks to save or to create a workspace (Locate step 3). Chat-only has no deep sizing file: Q3 uses only figures the user gave, labelled `user-estimate`.

### 2. Take the card and the context

Read the card, `context.md` and the cited inputs before drafting. No `context.md`: carry on, answer Q5 and Q6 `[unknown: flagged]`, and say strategic-context would supply them. A context carrying the no-strategy flag: repeat `> **Flag:** No product strategy provided — Cagan calls this 'no strategy'.` in the reply. A card already `framed` or `assigned`: write the assessment if asked, but say a team assigned a problem needs the 2017 four questions (problem-statement) and keep its status.

### 3. Deep sizing first, if it is missing

Q3 comes from the deep sizing, never from memory or a market number. If the card's `links.sizing` points to `sizing/P-NNN-deep*.md` (use the latest `-vN`), read it. If there is no deep file (none, or only a quick sizing): **run opportunity-sizing in deep mode for this card first** (Skill tool), before writing anything. Say in your request that the sizing feeds an assessment and that the user has already asked for the assessment, so when the card has no figure at all it should write the brief with the gaps `[unknown: flagged]` and not stop at its ranges question; put that question in this reply instead. opportunity-sizing's Inputs name this hand-off as the one case where it writes the brief with gaps instead of stopping. If after that no deep file exists, carry on: Q3 is `[unknown: flagged]` ("no deep sizing yet"), `links.sizing` stays as it was, and the unanswered ranges question goes in the reply. Never write a sizing file yourself, never put a figure of your own in Q3.

### 4. Viability for Q9

For Q9 Cagan writes "we're not describing the product here but rather making clear any dependencies or constraints" (2006): list constraints, not the product. Cite what exists, in this order, each with its source:

- the card's `## Viability screen` (yes/no lines from viability-constraints screen mode), **only its latest block**: the last `Screened` or `Re-screened` line and the lines under it, up to the next such line or the end of the section (no such line: the whole section is one block). Earlier blocks are history: a yes a later block answers no is cleared and is not cited as open. Every deal-breaker answered **yes** in that block, with its reach and who to consult; the `no` lines as "none known";
- the `## Viability constraints` of the statement `links.statement` names (else the highest `statements/P-NNN-vN.md`, else `statements/P-NNN.md`) (full mode), its constraints by category;
- `context.md`'s Known constraints, quoted, when the screen and the statement do not exist.

When the card still reads `_Pending: run viability-constraints (screen mode)._` and there is no statement: **flag the viability work as missing** in Q9 (`viability screen not run [unknown: flagged]`), cite only what the context or inputs state, quoting them, and make the screen the next step. Never write a legal, contractual or regulatory fact no input gave. This skill does not run viability-constraints itself.

### 5. Answer the ten questions

Fill `_templates/assessment.md` (fall back to `${CLAUDE_PLUGIN_ROOT}/templates/assessment.md`): the ten questions verbatim from the template, in order, each answered in a line or two, then the recommendation line, then the 2017 section. **At most 600 words in the file in total.** The title, template headings and 2017 section already use about 225, and the file is write-once, so keep to these limits: Q1–Q9 at most 35 words each; Q10 one sentence; the Recommendation line at most 50 words, with at most four risks of a few words each. Draft within them rather than trimming later. Remove the template comments and every `<placeholder>`. Keep the derived-template line.

- **Q1 problem, Q2 for whom:** the card's problem and `who`, as the Observations support them, with no feature or product in it. Say where the Observations are thinner than the problem line.
- **Q3 market size:** cite `sizing/P-NNN-deep.md` by name: its low–base–high range with the unit and the basis label as written there (`user-estimate` or `data`), its confidence, and its swing variable. Be conservative, as Cagan says ("not every opportunity needs to be a billion dollar market"): Base, never Upside. Size is the problem's, never what a solution would earn. A figure not in the sizing file is not in Q3; a `[unknown: flagged]` stays.
- **Q4 alternatives, Q5 differentiator, Q6 why now, Q7 go-to-market:** only what `context.md`, the card and the inputs say (what people use today, the vision and focus, a deadline or a worsening trend, channels already named). Name no competitor, window or channel that no input gave; write what is not known as `[unknown: flagged]` and who could answer. Q7 states what is known about reaching the people, not a plan.
- **Q8 measures and "make money":** the measure that would show the problem is being solved (the number the sizing sizes, who it is for) and, if a scorecard exists, the objective it serves. No revenue figure, pricing or payoff estimate; the revenue model is `[unknown: flagged]`, left to discovery.
- **Q9:** Step 4. A fact the user reports ("counsel confirmed ...") is attributed to the user wherever it is used, Q10 and the Recommendation line included, and is not written as cleared or settled as if a document said so; the card's screen is not edited (viability-constraints owns it).
- **Q10 recommendation:** Step 6.

Every figure carries its basis or is `[unknown: flagged]`. Figures come from the sizing file (Q3) or the card; Q4–Q8 hold none unless the card, the context or a cited input gives one, with its source named, and they are never computed or rounded by you. A figure from another problem's data (another card's cohort numbers) does not belong in this bet's answers. Say "problem", never "most important". No effort, Ease, duration or revenue projection anywhere in the file, including Q3.

### 6. The recommendation

End the file's answers with exactly one line `Recommendation: go | no-go | go to discovery — <named risks>` (pick one value; the line starts with it). Choose by judgment and say why in one or two sentences before the line:

- **go**: the problem is real on the evidence, big enough by the user's bar (or the sizing's "big enough?" with that bar), fits the stated objective, and no deal-breaker is known or open. "Go" hands the problem to framing and to the team's solution discovery. It is not a build decision.
- **no-go**: a known deal-breaker (below), or the evidence or size clearly falls short of a bar the user gave, or it sits outside the stated focus and the user has no reason to override it. Say which fact.
- **go to discovery**: plausible, but named unknowns could change the answer (thin evidence, an unsized or `[unknown: flagged]` Q3, a pending screen, an unnamed region or segment). The usual result when evidence is `low` or `very-low`.

Without a bar from the user, "big enough" is `[unknown: flagged]`: say so, and say what bar (a count or a value per period) would make it a go. Which deal-breakers count, from the latest screen block, in any of the seven categories: a **yes** whose reach to this card is established (the line says `reach: established`, or it gives no reach and nothing on the line marks its reach `[unknown: flagged]`) is a **known** deal-breaker, the only kind that gates the bet (no-go, above). A **yes** whose reach is `[unknown: flagged]` is an **open** deal-breaker: a flag carried on the card, not a known one and never a no-go on its own; it keeps the answer from being a plain go, and the risk names who settles it.

Name risks for every recommendation: each a fact, an unknown or a deal-breaker from the card, the sizing or the screen, with who or what would settle it. For go to discovery, the sizing's swing variable and the cheapest test are among them: name the test, and leave out its timebox and any duration (those stay in the sizing file). A deal-breaker answered yes is always named. Never invent a risk, a threshold or a date. Never recommend on a ranking against other problems.

### 7. Record (workspace mode)

- **Assessment file:** `assessments/P-NNN.md`. Assessments are write-once: if the file exists, write `-v2` (then `-v3`), never edit or replace one. Re-asked, with nothing changed, still writes `-v2` and says "nothing changed" in the note.
- **Card** (append-only body): `links.assessment` to the file, `links.sizing` to the deep file (the sizing step normally set it), `updated`. `status: assessed` when the card is `candidate`, `shortlisted` or `chosen`; a `framed`, `assigned` or `not-now` card keeps its status. Append History `- YYYY-MM-DD assessed by opportunity-assessment: <go | no-go | go to discovery> (was: <status>)`; for a `-v2` (or `-v3`) `- YYYY-MM-DD re-assessed by opportunity-assessment (assessments/P-NNN-v2.md): <recommendation> (was: <earlier recommendation>)`, and `links.assessment` then points to the new file. Never change `confidence`, `problem` or other lines; replace no `_Pending:` line (the screen and the evidence are other skills').
- **backlog.md** (living): the card's Status cell, and Next step for the step in Output. Edit only those cells.
- **workspace.md:** under `## Artifacts` add `- [Assessment P-NNN](assessments/P-NNN.md)`; append at the end of `## Decision log` `- YYYY-MM-DD — go/no-go — P-NNN — <recommendation>: <the main risk or reason, one clause>` (for a `-v2`, add "replaces assessments/P-NNN.md: <what changed>"); set `checkpoints_since_decision: 0` and `updated`; move `stage` to `choose` only if it is `foundation` or `identify`; put this reply's next step in the next-step line. Never edit a past log line. Nothing is deleted.

## Output

- Workspace mode: the assessment file, the card, the backlog row, `workspace.md`, and the deep sizing if Step 3 wrote one. Chat-only: the assessment in the conversation, same shape.
- Reply, in this order: the recommendation and why in a few lines; what the sizing says (range, basis, confidence); the risks and what is `[unknown: flagged]`, including a missing screen or sizing figures and the ranges question if one is open; the 2017 note (below); what changed per file. Say the ten questions are Cagan's 2006 list, and that the one-page form and the recommendation rule are this plugin's derived template. If the sizing is a user estimate say so plainly.
- The 2017 note. In the file, keep the template's `## 2017 four-question subset` section exactly as it is (it is the note) and add nothing to it. In the reply, **always** include one sentence in this form, with both halves: the four questions (objective, key results, customer problem, target market) are Cagan's (*Inspired*, 2nd ed., 2017); that they replace the ten for a team framing an assigned problem, and that the six dropped questions still apply to a leader choosing a bet like this one, is a synthesis across Cagan's eras, not Cagan's own statement (`question-sets.md`). Never say Cagan "cut", "dropped" or "replaced" the ten, and attribute no more of that chapter than the reference does.
- Every response ends with a line `**Next suggested step:** <skill or action>`, one step only, the first that applies: no-go: opportunity-backlog (park P-NNN as not-now with a revisit trigger); a pending viability screen: viability-constraints (screen mode) on P-NNN; go to discovery with `low` or `very-low` evidence: problem-evidence on P-NNN, for the named risks; otherwise problem-statement for P-NNN. An open ranges question: answering it comes first. Never "Next step", never a closing question.

## References

- `${CLAUDE_PLUGIN_ROOT}/references/question-sets.md`: the ten 2006 questions verbatim with Cagan's commentary on Q1, Q3 and Q9, the 2017 four-question subset, and which set fits which situation.
- `${CLAUDE_PLUGIN_ROOT}/references/sizing-methods.md`: what Cagan says can and cannot be sized (Q3 sizes the problem, never the payoff) and the deep-sizing procedure whose result Q3 cites. Non-Cagan except its first section.

## Guardrails

- Frame fast, never gatekeep: assess with thin evidence and flag it; "go to discovery" is a recommendation, not a refusal, and a card already assigned is not re-gated.
- Problems, not solutions: no feature or product in an answer; `candidate_solutions` are never an input, and Q9 lists constraints, not a design.
- Flag, don't invent: no figure, competitor, window, channel, constraint or date that no source or the user gave; unknowns are `[unknown: flagged]`; user figures keep `basis: user-estimate`.
- Label provenance: the ten questions are Cagan's (2006); the one-page template and the recommendation rule are derived (keep the derived-template line); sizing is non-Cagan.
- Never declare "the most important problem": a recommendation on one bet is not an order of merit.
- Size the problem, not the payoff: no revenue projection, effort, Ease or duration in any answer, Q3 included.
- Judgment over process: the questions prompt thinking and the recommendation is argued; the leader decides.
- Never write to the plugin's install directory. Assessments are write-once, `## Decision log` is append-only, existing card lines are never overwritten, and no file is deleted.
