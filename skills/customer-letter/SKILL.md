---
name: customer-letter
description: Use when a large or multi-problem effort needs framing as a customer letter to the CEO (Nordstrom variant), the CEO's reply, or an Amazon-style press release. Not for a single straightforward problem statement — use problem-statement.
---

# customer-letter

Frames a large or multi-problem effort (a redesign, several customer problems, several business objectives) as an imagined letter from a customer in the target market to the CEO, then the CEO's imagined reply to the team. Today's pain comes first, then the improved state. It is framing for the team and its readers, not validation: nobody real has said any of it. The letter is Cagan's (his Nordstrom variant, preferred over the press release); the press release is Amazon's practice (non-Cagan); the template is derived.

## When to use

- "Write the customer letter for P-004", "frame this multi-problem effort as a letter to the CEO", "draft a working-backwards press release for this redesign".
- A framed `statements/P-NNN.md`, ideally with success measures, for an effort with several customer problems or objectives.

## When not to use

- One straightforward problem that needs a statement: problem-statement. If the problem is single and plain, say so and name problem-statement; write the letter only if the user still asks.
- Key results themselves (success-measures), critiquing a statement (problem-review), choosing among problems (problem-focus), validating with real customers (this skill never does).

## Inputs

- **A statement:** a bare `P-NNN` or `statements/P-NNN.md` means the statement `links.statement` names (else the highest `statements/P-NNN-vN.md`, else `statements/P-NNN.md`) in the located workspace: look there, never search outside the project, and do not ask which file when it exists; if the card's link is stale (it names `statements/P-NNN.md` while a `-vN` file exists), say so and use the latest file. Read it with its card (Observations, Interpretation), `context.md` and the cited `inputs/`.
- **Success measures:** the statement's `## Success measures` section. Real key results are the only ones the CEO reply may use.
- **Raw text:** an effort described in chat. Use only what it says.
- No statement but a card: work from the card and say the statement is missing (problem-statement). Raw text alone: draft from it in chat and name problem-statement as the way to save a statement.
- Do not stop to ask for what is missing. A missing measure or number becomes `[unknown: flagged]`.

## Steps

### 1. Locate the workspace (problem-workspace → Locate)

Follow Locate in problem-workspace. No workspace and the user declines to create one, or the user says not to save anything: **chat-only**. The first output line is then `> **Chat-only mode:** nothing is being saved.` Write no file or folder anywhere and stay chat-only until the user asks to save or to create a workspace (Locate step 3).

### 2. Take the effort

Read the statement and card. Name the customer (the target market), the problems the effort covers, and the objective. The card's `problem` line is a claim; ground the letter in its Observations. If success measures are still pending, say so and go on: step 4 handles it. A card's `candidate_solutions` are not material for the letter: do not name them (a request is a solution, not an outcome).

### 3. The customer letter (Nordstrom variant)

An imagined letter from one customer in the target market to the CEO, in plain first-person words:

1. **Today's pain first.** What they live with now: what they try, where it stops, what it costs them, drawn from the Observations. Do not open with the improved state or with praise.
2. **Then the improved state.** What is different in their working life once the problems are solved, as outcomes they notice (what they can finish, stop doing, trust). No feature, screen, tool, technology or mechanism, and no solution from the card's `candidate_solutions` or the requests.
3. The letter says it is imagined. Do not present a quote from `inputs/` as the letter's words, invent a named person, or give a number no source gave. Cover every problem the effort spans, in the customer's own terms.

### 4. The CEO's reply

The CEO's imagined reply to the team, about the business effect, tied to the statement's key results:

- Name the primary and backstop key results as the statement writes them, and say what moving them would mean for the business objective in the context. Quote the baseline the statement gives, and put the source file beside every figure (backstop figures too, not only the first), or mark it `[unknown: flagged]`.
- No targets, revenue, savings, effort or duration projections (size the problem, not the payoff).
- No success measures yet (section still pending, or no statement): do not invent key results. Tie the reply to the objective in `context.md` and the Open assumptions, mark each missing measure `[unknown: flagged]`, and point to success-measures.

### 5. Press release (offered, not written)

Do not write the Amazon-style press release unless the user asked for it. Offer it in the reply as an option (Amazon's working-backwards practice, non-Cagan): "How does this improve the life of our customers? What are the real benefits to them?" When asked, fill the template's `## Optional: press release` section in outcomes, with no feature list, and no invented quote, date or figure. If the user asked only for the press release, still create the file: fill that section and write under the letter and reply headings "Not written: press release requested only."

### 6. Feature-drift check and reader test

- **Feature-drift check:** scan the letter, the reply and any press release for a slide into listing features, screens, tools or the card's candidate solutions. Quote each such line and restate it as an outcome, and fix the text before saving. Write "none found" if clean.
- **Reader test:** keep the template's three checkboxes unticked (they are for the real readers) plus its note: if the team, impacted teams or leadership do not see the value after reading, the framing needs more work or the effort needs reconsidering.
- **Caveat:** the file and the reply both say it plainly: "This is framing, not validation." It is checked only with colleagues, never real customers; do not offer to test it on customers as if it proved anything.

### 7. Record (workspace mode)

- **Letter file** (write-once): copy `_templates/customer-letter.md` (falling back to the plugin's templates) and fill it as `statements/P-NNN-letter.md`, keeping the derived-template line, the caveat sentence, the section headings and the reader-test list. Replace the template's `<…>` instructions and the HTML comment with your text; mark the press release section unused (leave the heading, text left out) when not asked. For a multi-card effort, use the statement of the lead problem and list the other problems in the letter's heading.
- A letter for that statement already exists: never edit it. Write `statements/P-NNN-letter-v2.md` (then `-v3`) and add one decision-log line to workspace.md: `- YYYY-MM-DD — revision — P-NNN-letter — <why>`. A first letter needs no log line.
- **workspace.md** (living): set `updated`, move `stage` to `define` if it is earlier, leave `checkpoints_since_decision` as it is, and put this reply's next step in the next-step line. Touch no card, statement or backlog row.
- Chat-only: give the letter, the reply, the drift check and the reader test in the reply under the chat-only notice.

## Output

- Reply, in this order: the file written (or chat-only notice); the letter and CEO reply (or a short quote of each opening if long); the drift-check result; the reader-test line and "This is framing, not validation."; the press release offer (when not written); what changed ("only statements/P-NNN-letter.md, plus workspace.md").
- Every response ends with a line `**Next suggested step:** <skill or action>`, one step only: show the letter to the team, impacted teams and leadership for the reader test; or success-measures when the reply had to flag missing key results; or team-objectives when the work is ready to be assigned. Never "Next step", never a closing question.

## References

- `${CLAUDE_PLUGIN_ROOT}/references/question-sets.md`: the customer-letter and press-release guidance (Nordstrom variant, reader test, Cagan's caveat).
- `${CLAUDE_PLUGIN_ROOT}/references/guardrails.md`: the seven guardrails and the standard responses (flag syntax, chat-only notice).

## Guardrails

- Frame fast, never gatekeep: missing measures are flagged and carried; the letter is still written.
- Problems, not solutions: outcomes only; no feature, tool or candidate solution in the letter, reply or press release; drift is flagged and rewritten.
- Flag, don't invent: no figure, quote, person, key result or baseline that no source gave; unknowns are `[unknown: flagged]`; user estimates are labelled `user-estimate`.
- Label provenance: the letter and reply are Cagan's; the press release is non-Cagan (Amazon); the template is derived.
- Never declare "the most important problem": the letter makes a case for the customer's pain, not for rank.
- Size the problem, not the payoff: no revenue, savings, effort, Ease or duration in the reply.
- Judgment over process: the team and leaders decide whether the framing holds; this skill drafts.
- Never write to the plugin's install directory. The letter is write-once (a revision is `-v2`), `## Decision log` is append-only, and no file is deleted.
