---
name: define-problem
description: Use when someone describes a business-problem situation and wants to be taken through the work end to end, not through one named step — a vague sense of trouble with notes or tickets to go through ('something's off with retention and I have a pile of notes'), a list of problems to choose from ('here's our list of problems — which should we pursue?'), an assigned objective to work up ('our team was given the objective X'), a folder of materials to go through ('help me find problems in materials/'), a bare 'help with problems', or resuming problem work in an existing problem-work folder ('continue', 'pick up where we left off'). Routes to the focused problem-definition skills and pauses after each. Not when the user names the step (frame, critique, size, compare, assess, assign, measure, screen) — use that skill directly (reframe-request for a feature or stakeholder request, problem-statement, problem-review, opportunity-sizing, problem-focus, opportunity-assessment, team-objectives).
---

# define-problem

The router. It works out where the user is starting, runs the focused skills in order with the Skill tool, and pauses after each one. It does none of their work itself.

## When to use

- The request is broad and names no step: "what problems should we work on?", "something's wrong with retention", "we have a pile of notes and tickets", "which of these should we pursue?", "turn these feature requests into problems and take them through to framing", "our team was given this objective", "pick up where we left off".
- Resuming: a `problem-work/` folder exists and the user wants to carry on.

## When not to use

- The user names one step ("size these", "draft the statement for P-003", "set up a workspace"): call that skill directly. A single feature or stakeholder request on its own ("sales wants X built") is one step: reframe-request, directly.
- A single status question: problem-workspace (Status).

## Inputs

What the user said, and the workspace if one exists. Nothing else is required to start.

## Steps

### 1. Locate the workspace

Follow problem-workspace → Locate.
- **Found:** first summarise the manifest in a few lines: initiative, `stage`, problems per status, the open decisions (shortlisted or chosen cards not yet framed, anything parked), the last decision-log line, and the recorded next suggested step. Write the summary as the first lines of the reply, headed `Where things stand:` and giving the stage, the recorded next step and any open decisions (one line each; say "none recorded" when there are none) — even when the user's words say to resume at once, and even though a focused skill's output follows. The summary is the opening lines of your final reply for the turn (before the skill's output and the block), written even when you run a skill in between: text before tool calls is not part of the reply the user reads. Then, when the user's words say to resume or continue ("continue", "pick up where we left off"), run that recorded step at once: the checkpoint after it is the offer to carry on, so ask no separate question. For any other request, classify (Step 2) and begin that chain at its first step. Trust the manifest: if a file seems out of step with it, say so in one line and point to problem-workspace Repair, but do not stop to reconcile. Locating and classifying never get a checkpoint block of their own, and you never ask "should I start?"; blocks come only after a skill has run.
  - **Which chain a resume is on:** recover it from the manifest. Find the recorded next step in the chain tables below; if it appears in both A and B (they share a tail), the chain is A when `discovery/` holds a sweep record, otherwise B. From then on the block's `<next skill>` is always the next step of that chain in table order (for example, after problem-evidence in chain A: viability-constraints (screen)), never a later step the recorded line happens to name.
- **Not found:** if the start is unclear, classify first (Step 2) and ask nothing but its one question. For chains A–D then offer to create a workspace (invoke problem-workspace Create with the initiative name and the chain's mode: `mode: leader` for chains A and B, `mode: team` for C and D) and wait for the answer; write nothing before it. Creating the workspace is not a chain step: when the user agrees, create it and run the chain's first step in the same reply, with no checkpoint block after the Create. If the user declines, the whole chain is **chat-only**: your first output line, on that reply and every later one, is `> **Chat-only mode:** nothing is being saved.`, every skill you invoke is told it is chat-only, no file or folder is written anywhere, and you carry on with the chain in the conversation until it ends. Never answer a decline with "understood" and stop: run the next skill. Chat-only lasts until the user asks to save or to create a workspace; then run problem-workspace Create (with the chain's mode) and continue the chain in workspace mode from that step. This offer is the router's own rule and applies to pasted text alone as well: a chain writes several artifacts, so it asks once even where Locate step 3 would go chat-only without asking; a decline is chat-only as Locate says.
- **Chain E needs no workspace.** A pasted statement to review is reviewed in chat; do not offer a workspace first.

### 2. Classify the starting point

Pick the chain from what the user said. If it fits two chains or none, ask exactly one multiple-choice question and stop: the options are the starting points in plain words (find new problems; choose among problems we already have; turn a feature request or roadmap into problems; frame a problem our team was given; review a statement we have). That question is the whole reply, closed (like every reply) by `**Next suggested step:** none yet: waiting for your choice of starting point` as its last line: no second question (no workspace offer yet), no focused skill run and no file written before the answer.

| Starting point | Signals | Chain |
|---|---|---|
| A. Find new problems | "what problems / opportunities…", "something's off with…", "we have a pile of notes, tickets or feedback", "something's wrong but no data", no specific problem named | strategic-context (full) → problem-discovery (sweep or elicit) → [reframe-request on the request list the sweep found] → problem-evidence → viability-constraints (screen) → opportunity-backlog (view) → opportunity-sizing (quick) → problem-focus → [opportunity-assessment for a new product or market bet] → Define chain → [customer-letter if more than one card was framed, or asked for] → team-objectives |
| B. Choose from known candidates | a list of problems, "which should we pursue" | strategic-context (full) → opportunity-backlog (load or import) → problem-evidence → viability-constraints (screen) → opportunity-sizing (quick) → problem-focus → … as A |
| C. Handed a feature, request or roadmap | solution-shaped language, feature names, "stakeholder wants X" | reframe-request → problem-evidence → Define chain |
| D. Assigned problem (team mode) | "our team was given…", an objective or OKR supplied | strategic-context (light) → Define chain → [customer-letter if more than one card was framed, or asked for] |
| E. Review existing statement | a pasted statement + "review / critique / check" | problem-review |

"Define chain" means problem-statement → success-measures → viability-constraints (full) → problem-review, run once per card.

The chain tables are exhaustive: the router runs those steps in that order and no others, under Keep going as well, even when a skill's own `Next suggested step` names another (chains C and D have no team-objectives: C ends at problem-review, D at customer-letter or, when that optional step is skipped, problem-review). problem-statement runs problem-review on its own draft before it finishes; that internal review is not the chain's problem-review step, which still runs after viability-constraints (full).

Chain A's bracketed reframe-request step: when problem-discovery's sweep found a list of requests (its reply or sweep frame names one, or names reframe-request for it), the step after problem-discovery is reframe-request on that list, then problem-evidence; the checkpoint block after discovery names reframe-request. With no request list it is left out and problem-evidence follows discovery. This step is for a request list the sweep comes across; it never decides the route. A user who asks to turn feature requests (a request file, a roadmap, "stakeholder wants X") into problems is starting point C, even when the folder also holds notes and tickets.

The chain A opportunity-backlog step is `view`: it reconciles rows with cards and shows the table, and asks nothing. The user shortlists by replying Edit at that checkpoint ("shortlist P-001 and P-004"); with no shortlist, sizing and focus take every `candidate` card.

Notes: begin at the chain's first step (or, when resuming, at the manifest's next suggested step); never start later because a file looks done. A step whose output already exists is run so the skill can load it (it reports what exists and offers a `-v2`); the user can Skip it at the checkpoint. In chain B the second step, opportunity-backlog, loads the backlog or imports the list the user gave; picking winners belongs to problem-focus, later. Solution-shaped input at any point goes through reframe-request first, keeping the original as a candidate solution. A request to rank "the most important problem" is declined with the focus-on-2–3 offer; never name one yourself.

### What the router passes to each step

Every invocation names the step's inputs; a skill is never left to guess them.

| Step | Passed with the invocation |
|---|---|
| problem-workspace (Create) | the initiative name; `mode: leader` for chains A and B, `mode: team` for C and D |
| strategic-context | `mode: full` (A and B) or `mode: light` (D) |
| problem-discovery | the focus area or objective from `context.md` when it has one; otherwise nothing |
| reframe-request | the request list or file the sweep named (A), or the user's requests (C) |
| problem-evidence | "every card whose Evidence is pending" (A, B); the cards reframe-request created or attached a request to (C) |
| viability-constraints (screen) | every card with `status: candidate` or `shortlisted` |
| opportunity-backlog | `view` (A); `load`, or `import` with the user's list (B) |
| opportunity-sizing (quick) | every `shortlisted` card, else every `candidate` card |
| problem-focus | the same set as sizing; under Keep going, also "the user delegated the choice" |
| opportunity-assessment | the chosen card the condition applies to |
| problem-statement, success-measures, viability-constraints (full), problem-review | the card ID of the card the loop is on |
| customer-letter | the lead card and the IDs of the other cards framed in this chain |
| team-objectives | every card framed in this chain |

### Per-card loop (Define chain)

The Define chain runs once per card, in ID order, over the chain's **framing set**: in A and B the cards problem-focus just chose (and, after an assessment, the card it assessed); in C the cards reframe-request created or attached a request to in this chain; in D the one card problem-statement makes from the objective. In the reply that shows the checkpoint block after the step that fixes the set (reframe-request in C, problem-focus in A and B), say in one line before the block which cards, by ID, the rest of the chain works on, one card at a time. In C the line reads `Framing set: P-004, P-007 — problem-evidence grades these next, then the Define chain frames each in turn.`; in A and B it reads `Framing set: P-004, P-007 — the Define chain frames each in turn.` The set holds only the cards that step created, attached a request to or chose. A request that already sits on a card (reframe-request found it there and added nothing) counts as attached to that card. A card among those that already has a statement is not put in the set: the line names its statement instead (`P-005 already has statements/P-005.md; ask problem-statement for a redraft`). The line names no card other than the set and those left-out statements. Run problem-statement, success-measures, viability-constraints (full) and problem-review for the first card, then the same four for the next. In the block and in the last line, a Define-chain step is named with its card: `problem-statement for P-003`, `problem-review for P-003`. The step after the last card's problem-review is the chain's next step after the Define chain (the bracketed customer-letter, then team-objectives, or the chain end). Skip at a Define-chain checkpoint skips that step for that card only. When the framing set is empty (C: every request attached to a card that already has a statement), say so in one line, name the statements that exist, and end the chain with the chain-end block. Run each skill yourself, in this conversation, one card at a time: never give cards to parallel agents and never run one skill across all the cards before the next skill. Under Keep going, the reply holds one short summary per skill run, each starting with the skill's name and, in the Define chain, its card (`problem-statement for P-003: <the objective line, the verdict, or the file written>`), in the order the skills ran, and ends with the chain-end block; it does not reproduce each skill's full output, and it finishes every card in the set before it ends.

### 3. Run one skill, then checkpoint

1. Invoke the next skill in the chain with the Skill tool, passing what it needs (initiative, card IDs, mode, chat-only). Do not do its work yourself or paraphrase it from memory, even when the step looks small.
2. Show its output, minus its own closing `**Next suggested step:**` line and, in chat-only mode, minus its leading notice line: the router's reply carries each of those once (the notice as the first line, the next-step line as the last). Put no header of your own before the block (no "Checkpoint: <skill> done." line, no summary banner): the block's first line is the only checkpoint line.
3. Read the manifest the skill just updated: `stage`, `updated` and `checkpoints_since_decision` are the skill's to set, and the router writes none of them (workspace only; chat-only keeps the count in the conversation). The router writes one line only: the `**Next suggested step:**` line under `## Next suggested step` in `workspace.md`, set to the `<next skill>` the block names (the chain's next step, even when the skill's own next-step line names another or left the line unchanged), so a later session resumes there; at chain end leave it as it is. Never touch the decision log.
4. Re-read `workspace.md` now that the skill has written it, and take `checkpoints_since_decision` from the file (not from the value you saw before the skill ran; in chat-only mode, from the count kept in the conversation).
5. If the count is now a multiple of 3, print the nudge (below) beside the block: before it, never in place of it. The nudge never changes the block's `<next skill>`; it only adds the suggestion to go to problem-focus.
6. Print the checkpoint block, exactly:

```
**Checkpoint — <skill> done.** Reply with one of:
1. **Confirm** — continue to <next skill>
2. **Edit** — tell me what to change
3. **Skip** — skip <next skill>
4. **Keep going** — run the rest without pausing
```

7. Last line of the reply: `**Next suggested step:** <next skill>` (the same text as in the block, see Output). Nothing follows that line, not even a side note. Then stop and wait.

**Chain end.** When the skill just run was the chain's last step (problem-review in chain E; team-objectives in A and B; problem-review for the last card of the framing set in C; customer-letter in D, or problem-review when D's optional last step was skipped), `<next skill>` is exactly `none — chain complete`: options 1 and 3 read `continue to none — chain complete` and `skip none — chain complete`, and the last line is `**Next suggested step:** none — chain complete`. Chain E is problem-review alone, even when the user also mentions measuring or handing off: those are the optional follow-on, never the Confirm target. A follow-on (for example solution discovery for the chosen problems, or a skill the user has not run) may be suggested only as optional, in a sentence before the block that starts `Optional, outside this chain:`; it is never the block's `<next skill>` and never what Confirm runs. A Confirm, Skip or Keep going sent after the chain-end block has nothing left to run: reply in a line or two that the chain is complete, run no skill, redraft nothing and write nothing, repeat the optional follow-on sentence and the chain-end block (a chat-only reply still begins with the chat-only notice line), and close with `**Next suggested step:** none — chain complete`. Anything the user wants changed is an Edit, which re-runs problem-review only.

**Bracketed steps.** A step in square brackets in the chain tables is optional and conditional: `[opportunity-assessment for a new product or market bet]`, `[customer-letter if more than one card was framed, or asked for]`. When it is the chain's next step, offer it with its condition: say in one line before the block whether the condition looks met and why, and name it in the block as `<skill> (optional: <condition>)`. The condition is the one the chain table states, word for word. Never run it unasked and never pass over it silently: Confirm runs it, Skip moves on to the step after it (or to the chain end). Under Keep going, run it only when its condition is plainly met from the manifest or cards, and say so; otherwise say it was left out and why.

**Keep going delegates the choices that are reversible.** When the chain reaches problem-focus under Keep going and no card is `shortlisted`, name the IDs of every card still `candidate` (not `not-now`) as its candidates and tell it the user delegated the choice: it chooses 2–3 and records them as proposed, never asking which. Say in the reply that the user can change the choice; the focus block is the two-way door. A real question stays a question (a missing context, fewer than two candidates).

Replies: **Confirm** runs the next skill. **Edit** re-runs the same skill with the change (it makes the `-v2`). **Skip** moves past the next skill (tell the user what that leaves out). **Keep going** runs the rest of the chain with no checkpoint block between steps and no nudge; the reply that ends the chain still ends with the chain-end block (Chain end); the manifest is still updated after each skill; stop early only where a skill must ask the user something to continue, and then ask. Keep going stays in force after that question: when the user answers it ("don't know" included), carry on with the chain from where it stopped, still with no blocks, until the chain ends or another skill must ask. Anything else: answer it, then show the block again.

### Nudge (timebox)

When 3 checkpoints in identify or choose pass with no problem chosen or parked, say in a few plain sentences: Cagan's regret that product managers act as gatekeepers on whether a problem is "worth solving" and leave too little time for solution discovery; and Bezos's rule of thumb (non-Cagan; label it as his, not Cagan's) of deciding with about 70% of the information you wish you had; the choice is reversible. Suggest (in the nudge text only; the block still names the chain's next step) going to problem-focus now to pick 2–3 and park the rest with a revisit trigger, or carrying on if the user prefers. The user decides; do not force it.

## Output

- The focused skills' own files; the router itself writes only the manifest fields in step 3.
- Each reply: the skill's output, the nudge when due, the checkpoint block, and a last line `**Next suggested step:** <skill>`, the same skill the block names as next (so a reply never contradicts itself). At the end of a chain it is `none — chain complete` (see Chain end).
- Chat-only replies begin with the chat-only notice line (`> **Chat-only mode:** nothing is being saved.`) and carry the same content.

## References

None; the focused skills load their own. Chain behaviour and the nudge follow `${CLAUDE_PLUGIN_ROOT}/references/guardrails.md` (1, 5, 7).

## Guardrails

- Frame fast, never gatekeep: pause is the default, but never lengthen the chain; honour "keep going" and the nudge.
- Never declare "the most important problem"; choose 2–3, reversibly.
- Problems, not solutions: a solution-shaped request goes through reframe-request.
- Flag, don't invent: no counts, decisions or files that no file supports; report the manifest as it is.
- Never write to the plugin's install directory; never overwrite or delete a file; chat-only means no file anywhere.
- Judgment over process: the user confirms, edits or skips each step; the router never decides for them.
