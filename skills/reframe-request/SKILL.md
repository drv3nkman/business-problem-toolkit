---
name: reframe-request
description: Use when handed something solution-shaped — a feature request, stakeholder ask, sales ask, roadmap item or a list of them ('the CEO wants SSO', 'customers keep asking for a dashboard'), or an instruction to skip the problem work and design the fix for a named problem ('just design the fix for P-001') — and the underlying problem needs uncovering. Not for open-ended searching of raw notes for unnamed problems — use problem-discovery.
---

# reframe-request

Turns a request that already names a solution into the problem underneath it, as a candidate card (or, in chat-only mode, a reframed list). Cagan's reversal: "what is the underlying problem to solve, and what is the logical way to measure success?" The request is kept, as a candidate solution. It is never evidence that the problem exists.

## When to use

- One request: a feature, a stakeholder or executive ask, a sales ask ("the CEO wants SSO", "sales keeps asking for an accounting-software sync", "stakeholder wants a new dashboard").
- A batch: a roadmap, a request log, a list of asks, in a file or pasted into the chat ("turn this roadmap into problems").
- The user says to skip the problem work and design the fix for a problem or card ("just design the fix for P-001"). Design is outside this plugin: say so in a line, do not write any design, option list or plan (not even a sketch), and offer what the plugin does: the frame (reuse the card's existing statement if it has one, otherwise offer problem-statement) and a hand-off of the framed problem to solution discovery. Do not lecture; the user decides.
- Another skill meets solution-shaped input: route it here first, keep the original as a candidate solution.

## When not to use

- Searching notes, interviews, tickets or data for problems nobody has named: use problem-discovery. This skill starts from what someone asked for and never mines other files for problems.
- Grading the evidence behind a card (problem-evidence), or critiquing a finished statement (problem-review).
- Judging whether the requested solution is a good one, or designing it. That is solution discovery, outside this plugin.

## Inputs

- The request or requests: pasted text, or a file named in the request or sitting in `inputs/`. Keep each one's exact words and note who asked, when that is known.
- Optional context: `context.md` (to link a problem to an objective) and the existing cards and backlog (to avoid duplicates and to number new cards).
- Do not stop to ask for what the request already gives. Missing information becomes a flag or a question for the requester, not a stop.

## Steps

### 1. Locate the workspace (problem-workspace → Locate)

Follow Locate in problem-workspace. No workspace and the user declines one, or says not to save anything: **chat-only**. The first output line is `> **Chat-only mode:** nothing is being saved.` Give the same content in the conversation, write no file or folder anywhere, and stay chat-only until the user asks to save or to create a workspace (Locate step 3). Pasted requests with a workspace present are saved like file requests unless the user said otherwise.

### 2. List the requests

One entry per ask, with its exact words and its source (a file and item, such as `inputs/requests.md R2`, or `conversation`). Split an entry that holds several asks. If the user says "reframe the request list in `inputs/requests.md`", read that file.

### 3. Reverse each request

For each ask, work out three things (the "why" Cagan says a request must carry; anti-patterns.md *Request with no why* and *Feature in disguise*):

1. **Who** has the problem: the people named or clearly implied, as a group, in the situation they are in. The requester is not automatically the one with the problem. When the request does not say, commit to the most likely group, label it `**Assumption:**` and list the other candidates beside it. The problem line is always a real sentence about that group, with no `[unknown: flagged]` and no bracketed note anywhere in it (unknowns belong to the baseline and the measure, under What we'd need to learn next).
2. **The unmet need**: what they cannot do, know or get today, in the present tense. Use the form of good-vs-bad-criteria.md: verb + measurable thing + for whom. Not a feeling ("users are frustrated"), not a category ("reporting problems").
3. **How success would be measured**: the measurable thing that would change if it were solved. Never invent a figure or a target. Write the missing baseline as `[unknown: flagged]` and ask the requester how they would tell, in the problem's `Question for the requester:` line (Step 8).

The problem text is **solution-free**: no feature, product, technology or vendor name from the request, and no description of what the requested thing does (a request for single sign-on is not reframed as "sign in through the company's identity provider"), and no word taken from the request's description of the fix. Describe the situation the requested thing would change: who is stuck, at what, at what cost. Ask yourself "could two quite different solutions fix this?" If not, reverse it again.

A request is a stakeholder assertion, one rung of the evidence ladder (others' opinions). What the requester says is the problem is a hypothesis. Quote it, label inferences `**Assumption:**`, and never write "customers need…" as fact. Many asks, or a loud or senior asker, do not raise confidence above `low`, and only several unconnected askers get `low` (Cagan's "Last Customer Visited").

If the ask is already a problem ("customers cannot find their invoices"), keep it as the problem and leave `candidate_solutions` empty.

### 4. Cluster

Several asks that share the same who and the same unmet need become **one** problem, even when the solutions differ (a status view and a shipping email can both answer "customers cannot tell where their order is"). Merge upward rather than writing one problem per ask. Every original text goes into that card's `candidate_solutions`, and each gets its own origin entry. A batch of N asks yields fewer than N problems whenever any two share a need; if they do not, say why in the report.

### 5. When the problem can't be worked out

If you cannot tell who has the problem or what they cannot do, even as a labelled assumption (a bare solution with no who, no situation, no hint of a need, such as "a bigger text box" or "make it pop"), write **no card**. Write one line in the reply instead: `Question for the requester: <one question that asks what the person is trying to do, who is affected and what they cannot do today, with the unclear item quoted>`. Do not guess a problem to avoid asking. A question is a valid output; so is "several asks became one card and one question".

### 6. Check the existing workspace

Before writing, read `cards/P-*.md` (front-matter), `backlog.md` and `context.md` if they exist.

- **Already recorded.** Only when an existing card holds the ask's text (in `origin` or `candidate_solutions`) **and** states the same who and the same need as your reframe: do not make another card, and say which card holds it. A card that merely holds the text while its problem is narrower or different (it covers one part of the need, or another group) is not a match: fall through to **Partial overlap**. Never report the same ask as both "already held" and "a different problem".
- **Same problem as an existing card** (same who, same need, the text not yet on it): do not make a duplicate. Add the original text to that card's `candidate_solutions`, add one line to its `## History` (`- YYYY-MM-DD request added by reframe-request: <source>`) and set `updated`. Change nothing else, and report it.
- **Partial overlap** (including a card that holds the text but states a narrower or different problem): make the new card, with the original text in its own `candidate_solutions`, and name the related card in its Notes ("Related: P-005 (overlap: …); merge only if the same problem"). Never merge cards here.
- **Objective link.** If `context.md` states an objective or focus the problem serves, say which in Interpretation; if none does, say the request has no stated strategy behind it, as a flag. A request that has no "why" is a hypothesis, not a strategy.

### 7. Write the cards (workspace mode)

1. **IDs.** Take the highest ID ever used plus one: the highest `P-NNN` among card file names **and** among IDs mentioned in `workspace.md`'s `## Decision log` (a merged-away ID such as P-002 is still used). Number new cards in sequence from there. Never reuse a gap.
2. **File.** Start each card from `_templates/card.md` (fall back to reading `${CLAUDE_PLUGIN_ROOT}/templates/card.md`). Name it `cards/P-NNN-<slug>.md`, the slug three to five words from the problem and never from the solution. Fill every front-matter key (only `parent` may be left out) and double-quote string values. Remove the template comments.
   - `problem` (solution-free), `type` (customer | business | both), `who`, `altitude` (team unless the request clearly spans more), `level` (product, or purpose when the problem is about what the person is trying to get done whatever the product).
   - `origin`: one `- kind: request` entry per original text, with `ref` the exact original words and, in brackets after them, the source (`[inputs/requests.md R1]` or `[conversation]`).
   - `candidate_solutions`: every original text, exact words.
   - `distinct_sources`: the number of distinct people or teams who asked, never the number of times.
   - `evidence_grade: "others' opinions (provisional)"`; `confidence: very-low`. When several unconnected people raised the same need on their own: `evidence_grade: "anecdotal evidence (provisional)"` and `confidence: low`.
   - `status: candidate`. Keep `discovered_in:` as an empty key (a sweep did not find it, a request did; the card schema still needs the key). Leave every `quick_size` key empty as the template has them. This skill does not size.
   - `updated`: today (YYYY-MM-DD).
3. **Body.** Problem (the unmet need and who, solution-free). Observations: one row per ask with the verbatim text, its source and `stakeholder assertion` as the kind. Interpretation: kept apart from the quotes, with the **Assumption:** labels, the objective link or its absence and any related card. What we'd need to learn next: the success measure (`[unknown: flagged]`), the requester's situation and the cheapest next evidence (observe the people it affects; do not claim to have done it). Where it does / doesn't occur: `Not yet examined.` Leave `## Evidence` and `## Viability screen` as their `_Pending:` lines. Keep every H2 of the template, in order: Problem, Observations, Interpretation, What we'd need to learn next, Where it does / doesn't occur, Evidence, Viability screen, Notes, History. Notes: "Seeded from <source>. Original request(s) kept in candidate_solutions, not in the problem." History: `- YYYY-MM-DD candidate created by reframe-request from <source>`.
4. **Backlog.** `backlog.md` is a living file: add one row per new card in the table's columns (Origin `request`, Confidence `very-low`, Quick size and Urgency `—`, Status `candidate`, Next step `Gather evidence (problem-evidence)`). Replace the template's placeholder row if it is still there; never touch `## Focus decisions`. If `backlog.md` does not exist, create it from `_templates/backlog.md` with the initiative name in the title and add `- [Backlog](backlog.md)` under `## Artifacts`.
5. **Manifest.** Under `## Artifacts` in `workspace.md` add `- [Card P-NNN](cards/P-NNN-<slug>.md)` for each new card and set `updated`. No decision-log line: creating a card is not a decision in the log's vocabulary; move `stage` to `identify` if it is `foundation` and add 1 to `checkpoints_since_decision`.
6. Existing files are never overwritten: new cards are new files, and an existing card changes only as step 6 describes.

### 8. Report

Chat-only: the whole result in the conversation after the notice line, with nothing written. Otherwise a short report. Both give, for each problem: the problem, who, the original request(s) kept as candidate solutions, the assumptions, how success would be measured (asked, not invented), the confidence, and one line `Question for the requester: <…> How would you tell this is solved?`. That line is mandatory for every card and every chat-only reframe: it is the question to send the requester, written to them in the second person ("How would you tell…"), never an instruction to the user ("Ask the CEO…"); it may also ask what they are trying to get done. Then the questions for items that produced no card (Step 5), then the requests tied to existing cards. The `Question for the requester:` lines are part of the report, not a closing question: the next-step line still comes last. In workspace mode also list the files written. Do not rank the problems or say which to work on first, and do not size them.

## Output

- Workspace mode: new `cards/P-NNN-<slug>.md` files (status `candidate`, confidence `very-low` or `low`, origin `request`), rows in `backlog.md`, Artifacts links in `workspace.md`, and a `candidate_solutions` plus History line on an existing card only when a request matches it.
- Chat-only: the reframed list in the conversation after the notice line; no file anywhere.
- `Question for the requester:` lines in the reply: one per card or chat-only reframe (always asking how they would tell it is solved, Step 8), and one for every item that produced no card (Step 5).
- Every response ends with a line `**Next suggested step:** <skill or action>`. After new cards: problem-evidence, or problem-discovery to look for evidence in notes or data. If only questions came out: send them to the requester, then run reframe-request again with the answers. Never "Next step" and never a closing question (the `Question for the requester:` lines above it are not one).

## References

- `${CLAUDE_PLUGIN_ROOT}/references/anti-patterns.md`: *Feature in disguise*, *Request with no "why"*, and the discovery pitfalls on treating a request as an opportunity and a stakeholder assertion as evidence.
- `${CLAUDE_PLUGIN_ROOT}/references/good-vs-bad-criteria.md`: solution-free, customer-anchored, the verb + measurable thing + for whom form.

## Guardrails

- Frame fast, never gatekeep: a thin request is a flag, a question and a low confidence, not a refusal. Do not demand proof that the requester is right before framing.
- Problems, not solutions: no solution term in a problem; the original stays in `candidate_solutions`, verbatim. Do not evaluate, design or approve the solution.
- Flag, don't invent: no who, number, target or evidence the request does not give. Inferences are `**Assumption:**`, unknowns are `[unknown: flagged]`, and a request is never recorded as evidence.
- Label provenance: keep the derived-template line from the card template.
- Never name "the most important problem", and never rank the requests or problems.
- Size the problem, not the payoff: no sizing here, no revenue, effort or duration.
- Judgment over process: clustering and "can this be worked out?" are judgments you explain; do not force a card out of an item that has no problem you can name.
- Never write to the plugin's install directory. IDs are never reused, and an existing file is never overwritten.
