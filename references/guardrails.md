# Guardrails

Seven rules every skill follows. Citations `[S<n>]` resolve to `sources.md`.

## 1. Frame fast, never gatekeep

Aim for a usable frame in one sitting, then hand off to solution discovery. Cagan lists problem-discovery over-emphasis as regret #2 of his 2026 keynote: PMs "viewing themselves as gatekeepers for determining if they have a problem worth solving, and leave themselves too little time for solution discovery" [S22][S47].

- Missing evidence becomes a flag and a "learn next" item, not a reason to stop.
- Timebox problem validation; "as soon as you start working on a problem… the clock starts ticking" [S10].
- Once leadership has assigned a problem, do not re-gate it (the reconciliation is an inference, synthesis; Moore & Cagan [S5] say strategy picks the problems).
- Cagan still wants the problem understood: "who we're solving that problem for, and what success looks like" [S22].

## 2. Problems, not solutions

No feature, app or project names appear in a problem. Cagan's team objectives give "a problem to solve rather than a feature to build" [S1].

- Anything shaped like a solution is reversed: "what is the underlying problem to solve, and what is the logical way to measure success?" [S5].
- Keep the original idea, labelled as a *candidate solution*, so nothing the user said is lost.
- Problem and solution stay entangled: framing will shift as solutions are explored [S10]. The frame is a starting point, not a contract.

## 3. Flag, don't invent

Missing information becomes an explicit flag. See *Standard responses* for the exact no-strategy flag; Cagan treats the absence of a strategy as a state of its own ("no product strategy") [S38].

- Numbers are never fabricated. A user's estimate is labelled as a user estimate; a figure from data names its source.
- An unknown quantity in discovery output is written `[unknown: flagged]`.
- Flag syntax is `> **Flag:** <text>`.

## 4. Label provenance

Cagan publishes no problem-statement template, only question sets, example objectives and criteria; he is hostile to "paint-by-number" frameworks for strategy [S23]. So:

- Every template the plugin writes carries the derived-template line (*Standard responses*).
- Methods from outside Cagan carry `(non-Cagan)` beside the method name: most of sizing, the evidence ladder, ODI, Cost of Delay, and the discovery techniques that do not come from Cagan.
- Sources marked secondary or unverified stay marked that way in anything that cites them.

## 5. Never declare "the most important problem."

Choose a few good problems; the choice is reversible. Cagan calls the question "fruitless and unanswerable" [S22].

- Confirm each candidate is real and big enough, then pick 2–3 and record explicit "not now" decisions. Rumelt via Cagan: "one, or a very few, pivotal objectives" [S38].
- Treat the choice as a two-way door. Bezos (non-Cagan): most decisions are "changeable, reversible", and should be made with roughly 70% of the information you wish you had [S82][S83].
- Torres (non-Cagan; secondary, reached through a quote site): choosing a target opportunity means "simply committing to exploring it further" [S84].
- Tension to know about: Moore & Cagan write that strategy identifies "the most important problems to solve now" [S5]. The reconciliation (synthesis, an inference): leaders pick a few problems without an exhaustive search for "the" best.

## 6. Size the problem, not the payoff

At problem stage, estimate who has the problem, how often, how bad and what it costs. Do not estimate revenue, effort, Ease or duration.

- Cagan: for revenue and cost "we have no clue on either of these, and we can't know" before there is a solution [S51].
- Cagan's basis is the quote above [S51]. The wider exclusion list is non-Cagan: no effort or Ease (Torres, non-Cagan [S59]) and no CD3 duration (Black Swan Farming, non-Cagan [S88]), on top of no revenue projections.
- "Whether enough people have this problem… is rarely hard, and not where the real work is" [S22].

## 7. Judgment over process

Outputs prompt thinking. A score or template never makes the decision on its own. Cagan: "Process all too often really is used as a substitute for thinking" (regret #10) [S22].

- Show ranges, assumptions and confidence; label numbers rough, subjective and revisable (Torres, non-Cagan) [S60].
- Estimate only what could change the choice (Hubbard, non-Cagan; secondary, reached through a quote site) [S67]; never let a total score decide on its own.

## Standard responses

Use these exactly. Copy the text between the fences without the fences.

**Asked which problem is "the most important problem" (decline, then redirect):**

```
I won't name any problem as "the most important problem." Cagan calls that "a fruitless and unanswerable question". What I can do is check that each candidate is real and big enough, then help you pick two or three to work on now. The choice is reversible, and the others are recorded as "not now" rather than dropped.
```

Citation for readers of this file, not part of the reply: Cagan's 2026 keynote [S22]; synthesis.

**No product strategy provided:**

```
> **Flag:** No product strategy provided — Cagan calls this 'no strategy'.
```

**Chat-only mode, the first output line when nothing is saved:**

```
> **Chat-only mode:** nothing is being saved.
```

**Provenance labels:**

- On every derived template, as a line of its own: `*Derived template — Cagan publishes no problem-statement template.*`
- Beside the name of any method from outside Cagan: `(non-Cagan)`, for example "Cost of Delay (non-Cagan)".
