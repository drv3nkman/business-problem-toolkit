---
name: problem-discovery
description: Use when looking for problems or opportunities that haven't been named yet — 'what problems are in these interview notes, tickets or exports?', 'something's off with X but I can't say what', 'where are we losing people?' — by sweeping raw material or interviewing the user. Not for grading the evidence behind an existing card — use problem-evidence; not for converting a feature request into a problem — use reframe-request.
---

# problem-discovery

Produces a rough first set of candidate problems that nobody has defined yet, in one sitting, each tied to evidence. The output is a first draft for the backlog: cards with `status: candidate`, a sweep record, and unranked backlog rows. It is not a verdict on what is worth pursuing, and it never blocks the user from moving on (frame fast, never gatekeep).

## When to use

- Raw material to read: interview notes, support tickets, churn or exit notes, metrics exports, process notes, emails ("what problems are in these notes?", "we have a pile of tickets").
- A vague sense with no named problem: "something's off with trial conversions", "where are we losing people?". With files in `inputs/` this is a **sweep**; with none, or when the user would rather talk, it is **elicit**.
- New files landed in `inputs/` since the last sweep: **incremental**.

## When not to use

- Grading how strong the evidence behind a card is: use problem-evidence.
- A solution-shaped ask ("the CEO wants SSO", "add a dashboard"): use reframe-request. If a request list is the main input, hand it over; here a request is only ever a candidate solution.
- Choosing what to pursue (problem-focus), sizing (opportunity-sizing) or writing a statement (problem-statement). This skill never sizes, ranks or judges worth.

## Inputs

- `inputs/` (any file types), existing cards and `backlog.md` (never duplicate them), and `context.md` if it exists. If there is no `context.md`, say so in a `> **Flag:**` line and continue; do not route away and stop. Strategy found in `inputs/` still sets the scope.
- Optional: a focus area or objective to scope the sweep.
- Asked for, never required, in this order: (1) raw verbatims of any kind; (2) something from people who left or never started; (3) one operational trace of where work waits or gets redone. Do not stop to ask for them; missing items become flags and learn-next lines.

## Steps

### 1. Locate the workspace (problem-workspace → Locate)

Follow Locate in problem-workspace. No workspace and the user declines one, or says not to save anything: **chat-only**. The first output line is `> **Chat-only mode:** nothing is being saved.` Give the same content in the conversation, write no file or folder anywhere, and stay chat-only until the user asks to save or to create a workspace (Locate step 3). Pasted material is swept like files.

### 2. Choose the mode

- **Sweep:** `inputs/` has files and `discovery/` holds no sweep yet.
- **Incremental:** a sweep exists. Read the latest sweep, every card and the backlog first. The new material is every file under `inputs/` that its Input inventory does not name, or what the user points at. Steps 3–11 run on the new material only, with the changes listed under Incremental mode below.
- **Elicit:** `inputs/` is empty or holds nothing readable, or the user wants to talk it through. Follow Elicit mode below, then Steps 4–11 with the conversation as the only input. Never generate a candidate with no evidence and no `**Assumption:**` label.

### 3. Set the frame

Take scope from the user's focus area or the objective in `context.md` (or `strategy` material in `inputs/`). No strategy anywhere: write the exact flag `> **Flag:** No product strategy provided — Cagan calls this 'no strategy'.` and continue. For a public service, also ask the user for the policy intent as a stand-in, and carry on without waiting for the answer. State what is out of scope. Record solution-shaped items (requests, feature names) as candidate solutions, never as problems. Name the timebox: a sitting, default 60–90 minutes, or what the user gave.

### 4. Inventory the inputs

List **every** file under `inputs/` (every depth, whatever its type). For each: its type; the kind of evidence it holds (direct observation, self-report, stakeholder assertion, aggregate number); who is represented and who is missing (non-users, churned users, excluded groups). A file you cannot read or that has no extractable content (an image with nothing legible, a binary, an unsupported format) is listed as `not read — <reason>`; never describe a file you did not read. A very large export (hundreds of rows) is read in chunks and clustered before anything is written; the inventory says what was read or sampled. Evidence only from current or successful users: add `> **Flag:** Survivorship — the evidence comes only from current or successful users; people who left, never started or gave up are missing.` to Coverage gaps, and a learn-next item to reach those people.

### 5. Sweep the lenses

Read `${CLAUDE_PLUGIN_ROOT}/references/discovery-lenses.md` and `${CLAUDE_PLUGIN_ROOT}/references/insight-sources.md`. Read each input and extract **observations**: the verbatim excerpt and where it is (file plus location). Apply the Cagan lenses (quantitative, qualitative, technology, industry, customer misbehavior and workarounds, context gaps) and the non-Cagan lenses, always labelled as such: switch forces, job map, operational. Sort why people use or don't use the product into push, pull, anxiety and habit. Observation first, interpretation after: what a source says is kept apart from the problem you infer. Hypothetical "would use" statements are not evidence. Count distinct people, accounts or teams, not mentions or rows, and count only those whose rows show the claim: a source that is silent on it, or that shows the opposite, is not counted. One account filing many tickets is one source.

### 6. Write candidates

Apply the Candidate-writing rules in `discovery-lenses.md` and the *Discovered-candidate criteria* in:
`${CLAUDE_PLUGIN_ROOT}/references/good-vs-bad-criteria.md`

Every candidate names who, the situation and the unmet need; passes "is there more than one way to address this?"; has no feature, technology or vendor name (not even inside a quoted request or after **Assumption:**: a card built from a request states the need and keeps the requested feature's name only in `candidate_solutions`); is not a bare feeling or a bare category; and states operational problems as the present-tense state of the system. Vague quantity words are unflagged estimates: not "a large part of the day", "a long time", "often", "many". State the situation without them, or write `[unknown: flagged]`; a figure appears only if a cited input gives it. Write the problem as who is stuck at what, not as a goal ("Reduce…"). Where two or more rows show the same operational stuck point, state it in the present tense as the state of the system ("orders on hold wait in a queue"), not as reported speech ("the note says orders wait"); a single episode stays a faithful restatement of what the row shows, with its source count. The problem line is held to the Step 10 audit: word it from the observed stuck point, never from a cause, a belief or a request, and put the inference in Interpretation as **Assumption:**. Avoid necessity words ("have to", "must", "only way") the quotes do not use. A stakeholder claim with no data ("X is our #1 problem") becomes a candidate with origin `stakeholder` and `very-low` confidence (others' opinions): never ranked and never dropped for lacking data.

### 7. Reframe quickly

For each candidate ask three questions (Wedell-Wedellsborg, non-Cagan; `discovery-lenses.md` *Reframing prompts*): what is missing; where does the problem not happen (positive exceptions: evidence of the same people succeeding); is the objective itself right. A better framing becomes a **sibling** candidate noted "Related: P-NNN"; the original stays. A request is never the problem: reverse it into the need underneath, in terms of what the people affected are trying to do (the interactive-map example in `discovery-lenses.md`, *Public services*: a map of service points becomes "people cannot easily find the nearest one"), and put the request in `candidate_solutions` of the card for that need. A request is not evidence of the problem, but it is recorded as an observation of what was asked: one Observations row per request, kind `stakeholder assertion`, with the request's exact words and its file and location (a request in the conversation cites `conversation, turn <n>`). A request row never counts toward `distinct_sources` for the problem's claim (only a request found inside an input is an `origin` entry, kind `request`; the sweep record's frame lists the others; reframe-request owns request lists). A request in a **list of requests** (a roadmap, a request inbox) stays a candidate solution on the card for the need it serves, is named in the sweep frame, and is handed to reframe-request in the next-step line; it does not get a card of its own. A request found **inside an evidence input** (for example a ticket that asks for a feature) that you choose to reframe gets its own card with origin kind `request` (file and location), one Observations row for the request (kind `stakeholder assertion`), `distinct_sources` equal to the number of distinct askers (one ticket is one), and a Problem line that begins `**Assumption:**` (inside the Problem line, e.g. `**Assumption:** people cannot easily find the nearest service point.`); when an existing evidence card shows the same who and need, attach the request to it as a candidate solution and leave its observed Problem line as it is. Give the other plausible readings in Interpretation and ask the requester in learn-next; "the underlying need is unstated" is not a problem line. In the reply and in Notes (never in the `problem` field or the Problem section) say "reframed from <request>"; the request is not the card's evidence, so do not offer it as the strongest verbatim.

### 8. Merge and cluster

Group by journey moment or job step. Climb one or two "why" levels to find parent problems; several parents are fine, and the deepest "why" is not assumed to be the right level. Symptoms become evidence rows or child cards (`parent:` set), not top-level candidates. Keep the top level to **7 or fewer**, merging upward beyond that (a starting value, tuned later). Tag `altitude` (team, multi-team, company); a company-level candidate may be phrased as a diagnosis but is never "the crux". Tag `level`: `purpose` when the need exists whatever the product, `product` when it is friction with this product (Young, non-Cagan).

### 9. Learn next

For each candidate: the missing who, how often (written `[unknown: flagged]`, never estimated), where it does and does not occur, and the cheapest next source. Never estimate a quantity the inputs do not give.

### 10. Check, stop, write

Read `${CLAUDE_PLUGIN_ROOT}/references/guardrails.md`.
Read `${CLAUDE_PLUGIN_ROOT}/references/anti-patterns.md` and run its eight *Checks before output* on the candidate set; record any flag they raise (loud single source, survivorship, stakeholder assertion) in Coverage gaps.
**Problem-line audit** (a ninth check, on every card, before it is written). The Problem line restates what the cited Observations show: who, the observed stuck point, scoped by the counter-cases, with a source count in parentheses (`<who> <stuck point> (in three interviews)`, or `One <who> <stuck point>`). A faithful paraphrase of the rows is fine. Write it from the narrowest row set that shows it; generalising to a segment belongs in Interpretation. Run these steps on each line:

1. **Nothing added, word by word.** The line adds no who, role, plan, reader, actor, channel, cause, scope or necessity ("every", "always", "only", "anyway", "had to") that no cited row shows, and no cause or belief tail (`so …`, `because …`): those go in Interpretation as **Assumption:**. Once the line is drafted, go through it word by word. For every word that names a person or role, a channel or place (a phone line, a website, a desk, an app, an email), a purpose (`to …`, `for …`, `in order to …`), an outcome (`finished`, `stayed`, `gave up`) or a frequency, point to the cited Observations row whose Verbatim holds that word or a plain synonym of it. Delete any word with no such row; do not soften it. If the line then reads badly, use the row's own words. Do not join two rows into one clause (`after A, never B`, `A on X and B on Y`) unless one row shows both. Word the counter-case from its own row, too: what that row says happened, not an outcome you infer from it.
2. **Count.** The source count equals the number of distinct sources, among the card's Observations rows, that show the claim, and `distinct_sources` matches it; a source silent on the claim, or showing the opposite, is not counted. State a base ("of five") only when the Input inventory or the input gives it. A claim that needs more rows than the card quotes is cut back to the rows it quotes.
3. **Counter-case.** Scan the inputs the card cites for a source where the same thing did not happen or that had help, and, for a funnel or cohort, the part that did not fail. When one exists the line says so (`in three of the five interviews; a fourth had help`) or names the narrower group, never a group-wide claim past it.
4. **Attribution.** A stakeholder's assertion, a self-conviction or a second-hand report (someone describing other people) is not a first-hand source for the group it describes: word the line as what was said (`The sales lead's email says larger buyers distrust the company`) or begin it `**Assumption:**`, and do not count it as a source for those people.
5. **Request cards** (Step 7) begin `**Assumption:**`; the audit applies to the who only.
6. **Figures.** A figure in a Problem line is read off a cited input (same digits as the input) or omitted; prefer counts in words. A count you derived yourself (distinct accounts after grouping an export's rows, a number of weeks or rows you tallied) is not read off an input: keep it out of the Problem line, in digits and in words. The line still carries a source count, in words, per *Count* above: the distinct sources among the Observations rows the card quotes, and the file (`(eight accounts quoted from <file>; the full count is in Interpretation)`). Give the derived count in Interpretation with its arithmetic and the rows it covers (Derived figures, below).

It catches: "staff reading cancellation reasons see price" (no row says who reads the field), "could not find out from the helpline" (only the website was quoted), "new accounts never finish setup" (one interviewee did). An element with no row is removed or moved to Interpretation.

**Derived figures.** A figure anywhere in a card, the sweep record or the reply is either read off an input (cite file and location) or derived with its arithmetic and inputs shown inline (`4 interviews + 6 notes = 10 accounts`; `12 of 30 trial accounts, accounts.csv rows 2-31`); a derived count names its members (`late in Notes A, C, F`). Discovery computes no percentages, shares or rates: give the counts as the input does and leave the ratio unsaid; a range or span is quoted from the input with its location. A base the input does not give is `[unknown: flagged]`. The Learn-next rollup is an unordered list: say "not in priority order", never "in order" or numbered by importance.
**Stop** at the timebox (one full pass over the lenses) or when one whole input adds no new candidate: record it, and list files you did not reach as `not read — stopped: <file> added nothing new`. Plugin-default heuristic (same wording in `discovery-lenses.md`, *Stopping rules*): with a handful of short, distinct inputs, read them all; the "adds nothing" stop is for long or numerous inputs of the same kind (exports, many interviews). If nothing credible turns up, say so: stopping there is fine, and a sweep record with no cards is a valid result. Never stop for lack of certainty; it goes into confidence and learn-next. After 3–4 new substantial inputs later, suggest a re-run.

Then write (workspace mode; existing files are never overwritten). Write every file yourself with the Write tool, one call per file: do not generate cards or the sweep record with a script (a shell may not be available, and a script you cannot run leaves the workspace empty). Type verbatims from the text you read. Write the cards before the sweep record, so the record can list them:

1. **Cards** (Step 11 below).
2. **Sweep record:** `discovery/sweep-<date>.md` from `_templates/discovery-sweep.md` (fall back to `${CLAUDE_PLUGIN_ROOT}/templates/discovery-sweep.md`), keeping its derived-template line and all eight sections. If the file exists (same day), write `sweep-<date>-v2.md`, then `-v3`. Lenses applied: one lens per line; any line that mentions switch forces, the job map or operational problems, in any wording (even in a "not used" note on another lens), also says `non-Cagan`.
3. **Backlog:** add one unranked row per new card (Origin = first origin kind, Confidence, Quick size and Urgency `—`, Status `candidate`, Next step `Gather evidence (problem-evidence)`); order by ID, no rank. Replace the template's placeholder row; never touch `## Focus decisions`. No `backlog.md`: create it from `_templates/backlog.md` and link it under Artifacts.
4. **Manifest** (`workspace.md`): link the sweep and each new card under `## Artifacts`, set `updated`, move `stage` to `identify` if it is `foundation`, add 1 to `checkpoints_since_decision` (a whole discovery pass counts once), set the next-step line to problem-evidence, and append one line to `## Decision log`: `- YYYY-MM-DD — discovery — discovery/sweep-<date>.md — <n> new candidates; stop: timebox` (or `stop: no new candidates` when a whole input added nothing or nothing credible turned up). The note is exactly `<n> new candidates; stop: <reason>` with nothing added, even when n is 1 (`1 new candidates`); evidence attached to existing cards is recorded in their History lines, not here. A pass that only adds evidence still gets its line (`0 new candidates`).

### 11. Card format

Start each card from `_templates/card.md` (fall back to `${CLAUDE_PLUGIN_ROOT}/templates/card.md`); name it `cards/P-NNN-<slug>.md`; keep every H2 in order; double-quote strings; remove template comments. New ID = highest `P-NNN` among card files **and** IDs in the decision log, plus one (start at P-001); never fill a gap.

- Front-matter: every key of the template, none dropped (id, problem, type, who, altitude, origin, level, parent, children, distinct_sources, evidence_grade, discovered_in, confidence, quick_size, status, not_now, candidate_solutions, links, updated); the key most often dropped is `status`: write `status: "candidate"` on its own line right after the `quick_size` block and before `not_now`, and check `status` and `updated` are there before you save. `origin`: list, most specific kind first, each `kind` from the card template and `ref` the file and location (or `conversation, turn <n>`). `level` set. `distinct_sources`: whole number, counting only distinct sources whose rows show the Problem line's claim (a source silent on it, or showing the opposite, is not counted; on a request card it is the number of distinct askers). `evidence_grade: "<rung> (provisional)"` with the highest rung present: `others' opinions` (assertion only), `anecdotal evidence` (a few quotes or tickets), `user/customer evidence` (several distinct people or systematic data), `self-conviction` (assumption only); copy the names exactly. `confidence` is the rung's band, never above `medium`. `discovered_in: discovery/sweep-<date>.md` (the exact sweep file name). `status: candidate`. `candidate_solutions`: the asks and user-proposed fixes, exact words. Leave every `quick_size` value empty: discovery never sizes. `updated`: today.
- Body: Problem (the problem line only, one observed sentence per the Step 10 audit, solution-free, with no "the need underneath is…" reading, which belongs in Interpretation as an **Assumption:**; exception: a card reframed from a request, whose problem line begins `**Assumption:**` (Step 7); any digit in it must appear in a cited input, otherwise write `[unknown: flagged]`, so prefer no digits); Observations table, one row per observation with Source, Location, Verbatim, Evidence kind; Interpretation (apart from the quotes, with **Assumption:** labels, `Related: P-NNN` where cards overlap); What we'd need to learn next (non-empty); Where it does / doesn't occur (positive exceptions, or `Not yet examined.`); Evidence and Viability screen left as their `_Pending:` lines; Notes (`Seeded from discovery/sweep-<date>.md.`); History (`- YYYY-MM-DD candidate created by problem-discovery`).
- **Interpretation holds only labelled inferences.** Every sentence in it that states a cause, a belief, a likelihood or an explanation ("so it is unlikely to come from…", "so the log undercounts…") begins **Assumption:**; plain restatement of an observation belongs in Observations, not here. A count you derived (Step 10, *Figures*) is the exception: it goes here, unlabelled, with its arithmetic and the rows it covers.
- **Verbatims are exact.** The Verbatim cell is copied character for character from the cited file (or from a user turn when the source is `conversation`): one fragment per row, no paraphrase, no ellipsis, no `|`, no Markdown markers, no merged sentences. For a CSV quote the cell or the row. If you cannot quote a claim, delete the row and mark the claim `**Assumption:**` in Interpretation. Cite an aggregate row or figure only when it supports the problem the card states, with the file named; never extrapolate it.
- **Existing cards first** (reframe-request's rule): same who and same need: attach to that card; partial overlap: a new card noting `Related: P-NNN`; never merge silently, never duplicate.

### Elicit mode

Say in one line that the prompts are Mom Test and switch-interview style (non-Cagan). Ask in the order under Inputs, one short question at a time, and wait for the answer. Prompts are past-tense and specific, from `discovery-lenses.md` *Elicitation prompts* ("Tell me about the last time…", "What did you do next?", "When did you stop, and what was going on that day?", "Where did work wait or get redone last week?"). Never ask what they would do or like, or whether an idea is good. When the user says "usually", "always" or "would", ask for the last specific time. Start with the story when the user has not given one, then people who left or never started, then one operational trace; ask at most three rounds. Do not write cards until the user says that is all they have, or the three have been asked. Then take the user's own words, verbatim, as observations (source `conversation`, location `turn <n>`, kind `self-report`), and write candidates with confidence `very-low` or `low` and `distinct_sources` counting people, not messages. A story about one customer is one source: say so. Never claim to have run interviews or queried data; the cheapest next source goes into learn-next.

### Incremental mode

Only the new files are swept. New evidence for an existing card is **appended** to it: new rows at the end of its Observations table, one History line (`- YYYY-MM-DD evidence added by problem-discovery from <file>`), `updated`, and `distinct_sources` raised if the source is new; no other body line changes, and a status never changes. An observation that matches no card makes a new one. The new sweep record is a new file (`-v2` on a same-day collision) and its Input inventory names every file under `inputs/`: earlier files as `read in discovery/sweep-<earlier date>.md`. Add the decision-log line and Artifacts links as in Step 10.

### "Just give me N problems"

Return only candidates tied to evidence, however many that is. List any extras in the reply as `**Assumption:** <claim> — confirm by <the named source to ask or data to pull>` (the confirming step is in the reply itself, not only in the sweep record); they do not become cards unless the user asks. Asked which problem is "the most important": use the standard decline in `guardrails.md` and offer problem-focus on a few. The decline names no single card either (not "the one to check first", "start with" or "the strongest"): say that problem-focus compares them on several dimensions and picks two or three. That reply, like every other reply in this skill's conversation (including a decline or a follow-up question), still ends with `**Next suggested step:** problem-focus` (or problem-evidence when the cards are still ungraded): never close on an offer such as "say the word".

## Output

- Workspace mode: `cards/P-NNN-<slug>.md` files (status `candidate`), appended rows on existing cards, backlog rows, `discovery/sweep-<date>.md`, and the manifest edits above. Chat-only: the same content in the conversation after the notice line; nothing written.
- Reply: a short list per candidate (problem, who, origin, confidence, the strongest verbatim), then the flags (no strategy or context, survivorship, stakeholder claims), the learn-next rollup, what was sampled or not read, and the files written. No ranking, sizing or "most important", and no "strongest", "main", "key" or "top" finding either: where a few candidates stand out, say what each rests on, not that it leads.
- The reply ends with `**Next suggested step:** problem-evidence` (grade each card's evidence; if the inputs held a request list, name reframe-request for it in the line before). In elicit, when the user wants to keep talking, ask the next prompt instead. Never "Next step" and never a closing question.

## References

- `${CLAUDE_PLUGIN_ROOT}/references/insight-sources.md`: the insight types and why people use or don't use the product.
- `${CLAUDE_PLUGIN_ROOT}/references/discovery-lenses.md`: lenses, elicitation prompts, candidate-writing rules, reframing, clustering, stopping rules.
- `${CLAUDE_PLUGIN_ROOT}/references/good-vs-bad-criteria.md`: *Discovered-candidate criteria*.
- `${CLAUDE_PLUGIN_ROOT}/references/anti-patterns.md`: the eight checks to run on the candidate set (Step 10 adds the problem-line audit as a ninth).
- `${CLAUDE_PLUGIN_ROOT}/references/guardrails.md`: the seven guardrails and the standard responses.

## Guardrails

- Frame fast, never gatekeep: thin evidence is a flag, a confidence and a learn-next line, not a refusal or a reason to stop.
- Problems, not solutions: no feature, technology or vendor name in a problem; the original ask stays in `candidate_solutions`.
- Flag, don't invent: no quote you cannot find, no number the inputs do not give (`[unknown: flagged]`), no claim of interviews run or data queried; inferences are **Assumption:**.
- Label provenance: derived-template lines stay; every non-Cagan lens or prompt says `non-Cagan`.
- Never declare "the most important problem"; never rank candidates or the backlog rows.
- Size the problem, not the payoff: no sizing, frequency or duration estimates, revenue, effort or ease.
- Judgment over process: clustering, reframing and when to stop are judgments you explain.
- Never write to the plugin's install directory. IDs are never reused; existing files are never overwritten (a re-run is `-v2`).
