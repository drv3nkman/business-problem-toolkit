# Anti-patterns

Pitfalls Cagan names, arranged for use by `problem-review` and `reframe-request`. They are prompts for judgment: a hit is a question to ask, not a verdict. Citations `[S<n>]` resolve to `sources.md`.

## Statement anti-patterns

### Review scans

The seven scans `problem-review` runs on any statement.

| Scan | Tell-tale signs | What to do | Source |
|---|---|---|---|
| Feature in disguise | Names a feature, app, project or deliverable; reads as a roadmap line; problem and solution split between PM and engineering | Reverse it: "what is the underlying problem to solve, and what is the logical way to measure success?" Keep the original as a candidate solution. | Feature roadmaps hide the problem; discovery typically finds "at least half of what is on the roadmap is simply not worth doing" [S15]. Cagan's estimate that "95% of roadmaps are not outcome-based roadmaps" is anecdotal ("I don't [have] formal studies") [S45]. Splitting problem from solution "usually kills any chance for real innovation" [S10]. |
| OKR theater | Objectives handed over with the solution still dictated; deliverables listed as key results; individual or functional objectives that dilute team objectives; OKRs layered on an output-based roadmap process | Ask what outcome the key result measures; move the solution out of the objective | "Check the empowerment box" yet "still continue to tell them the solutions" [S1][S46]. Layering OKRs on output processes "fueled the backlash to OKR's" [S4]. |
| Vague | Cannot be defined or measured by an executive; abstract verbs such as "provide integrated platforms" | Name the customer, the thing that changes and the direction of change | [S4] |
| Metric-driven | Chosen because a KPI already exists; general KPIs mistaken for outcome measures (gas gauge, tachometer vs. miles per gallon) | Pick the problem for its importance first; define new KPIs if needed | "Letting the tail wag the dog" [S1]; [S4] |
| Gatekeeping language | Demands proof the problem is "worth solving" before any work; ranks it as "the most important"; leaves too little time for solutions | Frame it, flag missing evidence, hand off. Never rank importance (guardrails 1 and 5). | Regret #2: PMs as "gatekeepers for determining if they have a problem worth solving"; "the most important problem" is "a fruitless and unanswerable question" [S22][S47]. A weak solution can make demand look absent: "If you have a crappy solution, it can look to you like the demand isn't there." [S10] |
| Request with no "why" | A stakeholder, customer or competitor ask with no link to a strategy, objective or customer problem; a large customer funding a "special" | Ask what problem the request solves and for whom; link it to an objective or flag that it has none | Teams need the strategic context "to understand the *why*" [S1]. Reacting to sales deals, competitors, customer requests and price pressure is not strategy [S5]; a large customer funding a "special" is a bad origin for a product effort [S14]. |
| Missing customer or business evidence | Cites no customer evidence (interviews, observation, why people use or stop using the product) and no business context (strategy, constraints, data) | Verdict: premature. List the evidence to collect; do not block the frame (guardrail 1). | A statement that cannot cite customer evidence and business context is premature (synthesis) [S7]. Titles without the deep knowledge needed to frame real problems are "product management theater" [S48]. |

### Other pitfalls

- **Outcomes without the product model.** Outcome language on top of output-based processes [S4].
- **Prioritizing without focusing.** Twenty or thirty "top priorities" instead of two or three [S38].
- **The wrong "why" (regret #3).** Treating the PM's main contribution as explaining why the problem matters, which strategy should already do, rather than investigating "*why are people using – or not using – our product?*" [S22]
- **Discovery theater.** Continuing feature design while calling it discovery [S49].
- **Process as a substitute for thinking (regret #10).** "Process all too often really is used as a substitute for thinking." [S22] See guardrail 7.
- **Stakeholder-driven strategy.** In feature-team companies "the product strategy is literally to try to deliver as many features as possible for the different stakeholders." [S5]

## Discovery pitfalls

Pitfalls for `problem-discovery`. Most sources are non-Cagan; Cagan's own is "Last Customer Visited".

### Checks before output

Run these on the candidate set before writing the sweep record. A hit is a question to ask, not a verdict.

1. **Solutions in disguise.** A candidate with only one way to address it, or that names a feature, technology or vendor. Reverse it and keep the original as a candidate solution.
2. **Candidates with no excerpt.** No verbatim excerpt with file and location: add one or mark it `**Assumption:**`.
3. **Evidence drawn only from current customers.** Look for people who left or never started.
4. **One loud source dominating.** Cagan's "Last Customer Visited": a leader who wants to change direction from the most recent customer's issues [S95].
5. **A stakeholder assertion presented as evidence.** Record it as an assertion and say what evidence supports it.
6. **Hypothetical "would use" statements counted as evidence.** Statements about future behavior are over-optimistic (*Mom Test*, non-Cagan; secondary) [S102].
7. **Any ranking or sizing.** Discovery does neither (guardrails 5 and 6).
8. **Too many top-level candidates.** Merge upward; the plugin default is ≤ 7 (`discovery-lenses.md`, *Stopping rules*).

### Pitfalls with sources

- **Last Customer Visited.** A leader changes direction because of the latest customer's issues (Cagan, "You're Not Helping") [S95].
- **Invented opportunities.** Opportunities made up from scratch bring in the team's own biases (Torres, non-Cagan) [S59].
- **Overreacting to the latest interview, sales call or ticket** (Torres, non-Cagan) [S59].
- **Treating a request as an opportunity** (Torres, non-Cagan [S59]; GOV.UK, non-Cagan [S113]).
- **A validation mindset.** "Discovery is not for validation" (GDS user research blog, non-Cagan) [S114]. Also gatekeeping (guardrail 1).
- **Analysis paralysis** (Torres, non-Cagan) [S59].
- **Single-root-cause tunnel vision.** Card: 5 Whys forces one causal path and assumes the deepest "why" is the right place to intervene (non-Cagan) [S110].
- **Survivorship bias and highest-paid-person's-opinion problems.** Well-known biases, but no primary source was gathered for them.

### AI-synthesis risks

Apart from NN/g and one preprint, the material is from vendors; the quote rule is a precaution, not a proven safeguard.

- AI-assisted analysis can be inaccurate: NN/g reports AI legal research tools wrong 17% to 33% of the time, and advises making the tool link each insight to the original data [S120].
- Product managers were less critical of GenAI output than researchers were [S121], a direct risk for this plugin's audience.
- **Hallucinated themes:** plausible patterns not grounded in the data (vendor blog, secondary) [S122]. The countermeasure is the exact quote behind each theme: every candidate cites a verbatim excerpt or is marked `**Assumption:**`.
- AI-generated opportunity trees may produce too many top-level opportunities (a Product Talk teaser, unverified). Merge upward.
