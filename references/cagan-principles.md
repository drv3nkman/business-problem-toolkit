# Cagan's principles

Condensed from the research this plugin was built from. Quotes are Cagan's unless marked. Cagan publishes no problem-statement template; anything marked *synthesis* is this plugin's reading across the sources, not his text. Citations `[S<n>]` resolve to `sources.md`.

## Core principles (P1–P8)

| # | Principle | Evidence |
|---|---|---|
| P1 | **Assign problems, not features.** Give a team "a *problem to solve* rather than a feature to build" plus the strategic context for the "why". Why: the people closest to the problem find the best solution; accountability needs ownership of the solution; if the first solution fails, "they know they must continue to *iterate*." | [S1] |
| P2 | **Empowered vs. feature teams differ in how problems are assigned**: a *problem to solve* versus *features to build*. | [S2]; Chris Jones, secondary [S3] |
| P3 | **Outcomes over output.** An outcome is framed around "a *problem to solve* and the *measures of success*." | [S4] |
| P4 | **Problems come from strategy, not stakeholder requests.** Strategy identifies "the most critical problems to solve in the quarter"; choosing them is "the explicit responsibility of product leadership." | [S5][S6] |
| P5 | **Customer problems and business problems both count.** Either, or both. | [S1][S7] |
| P6 | **"Fall in love with the problem, not the solution."** In context: stay loyal to the problem while discarding failed solutions, not a mandate for long problem study. | [S8] (quote site, secondary); [S9] |
| P7 | **Problem and solution are entangled.** Understanding "develops and deepens" as solutions are explored; he rejects the split where PM and design define the problem and engineering then builds a solution. | [S10] |
| P8 | **Clarity is the real work.** "Most measurement and alignment challenges are actually *clarity challenges*." | [S4] |

Altitude: problems exist "at different levels of granularity", from one team to many teams [S4].

## Four big risks plus ethics

Strictly, the risks are evaluated against *solutions*. A good problem frame anticipates them by recording constraints (*synthesis*).

1. **Value**: "whether customers will buy it or users will choose to use it".
2. **Usability**: "whether users can figure out how to use it".
3. **Feasibility**: "whether our engineers can build what we need with the time, skills and technology we have".
4. **Business viability**: "whether this solution also works for the various aspects of our business": go-to-market and sales-channel fit, partner contracts and legal compliance, cost-effective acquisition, monetization, brand consistency [S20].

- Ownership: PM owns value and viability and the product's *outcomes*; designer owns usability; lead engineer owns feasibility [S20].
- Ethics is proposed as a fifth risk in "Coaching – Ethics"; viability there is phrased "Can the stakeholders support this solution?" [S21].
- For problem framing, record viability constraints up front: legal, compliance, financial, sales channel, brand, partner, ethical. The 2006 Q9 ("critical success factors… dependencies or constraints") does this job [S14].
- Version note: viability was not a separate risk until 2017, and in 2026 Cagan calls under-weighting it his biggest regret [S20][S22].

## Strategy: focus, insights, action, management

- **Focus.** Rumelt via Cagan: good strategy focuses "on one, or a very few, pivotal objectives". Leaders often have "at least 20-30" priorities instead of "2-3 truly important things": "prioritizing, but not focusing." [S38]
- **Insights**, four sources [S23]:
  - *Quantitative*: product data (business model, funnel, retention, sales execution).
  - *Qualitative*: evaluative ("did it work?") and generative ("did we uncover any new opportunities…?"). Generative research is where new problems come from.
  - *Technology*: what is newly possible, often surfaced by engineers.
  - *Industry*: competitors, trends, other industries and regions, analysts.
  - Insight "*never* happens without real preparation": hours with data, customers, technology and industry, grounded in the strategic context.
- **Action.** Insights become team objectives: "Tell each team which problems you need them to work on, and what business results they should measure." [S24]
- **Management.** Ongoing coaching, because "no product strategy survives its initial encounter with the real world." [S25]
- Output of strategy: "a set of business or customer problems to solve (team objectives)" [S27].
- No strategy: write the flag from *Standard responses* in `guardrails.md`; Cagan's term is "no product strategy" [S38].

Four deep-knowledge areas as the evidence base: customer, data, business, market/industry (*Inspired* ch. 10, via summaries, secondary [S33][S34][S35][S36]); restated in 2026 as "product sense" [S7]. A statement that cannot cite customer evidence and business context is premature (*synthesis*).

## Team objectives

- **Objective = the problem, stated qualitatively.** "Notice also the example objectives are all qualitative. The quantitative dimension will be discussed in the key results." [S1]
- **Key results = business results**, "not simply activity or output." [S1]
- **Two key results per objective**: a primary measure plus a quality "backstop… to ensure that the first key result is not inadvertently achieved by hurting something else." [S1]
- **The team proposes target values and timeframe**, so it owns the commitment; leaders iterate with teams top-down and bottom-up [S1][S30].
- **How many**: "one or two clear objectives" per team, typically quarterly; several teams may share a hard problem; "keep the lights on" work sits outside objectives [S6][S27][S31].
- **Why this team** (Moore & Cagan's five criteria): "the areas they are responsible for, the skills on the team, the enabling technology used by that team, the data the team has access to, and the team's ideas for pursuing this problem." [S5]
- Teams "won't feel empowered… if they lack the access or ability to make the changes necessary." [S4]
- Define the problem "*before* discussing the metrics", even if that means new KPIs [S4].

## Outcomes hierarchy

Product vision → company objectives → product strategy (focus + insights) → team objectives (problems) → key results (outcomes) → discovery (solutions tested against the four risks) → delivery with instrumentation (synthesis).

- Vision horizon: "most are 3-10 year product visions", and the vision is "first and foremost about the customer" [S5][S27]. An earlier SVPG FAQ gave 2–5 years for software and 5–10 for devices (version note).
- Product outcomes vs. business outcomes (Torres) and output → outcome → impact (Patton); outcomes are "dominoes, with each piece helping to topple the next." [S4]
- Input metrics drive output metrics (Amazon: selection, price, convenience drive orders, revenue). Cagan warns this "output" differs from his use of the word (things built) [S4].
- Behavior-based KPIs are "one useful technique", but "many important problems do not necessarily impact user behavior." [S4]
- Telemetry: "commit to continuously improving your product's telemetry, creating new KPI's… to measure if you are solving the necessary problems." [S4]
- Success test: "if your work generated the necessary business impact, then we know your product team made the right choices." [S7]
- Prompt from Cagan's *Transformed* discussion guide: "What would be some good examples of important problems to solve, and the relevant outcomes for those problems, that your company and your customers would value?" [S50]

## Opportunity backlog

Keep problems, not features, on a prioritized list that feeds discovery. Cagan adopted the idea from Jeff Patton [S15].

- When a solution fails, the problem remains, and the next attempt is measured against the same outcome. An opportunity assessment exists to "untangle your initial ideas or assumptions about the solution from the problem" [S15].
- Two main sources of opportunities: the product vision and the product scorecard, "the prioritized business objectives for this team" [S15].
- Discovery typically finds "at least half of what is on the roadmap is simply not worth doing" [S15].
- Use the opportunity assessment for ongoing work on an existing product; a canvas is for a new business or product line, where distribution, monetization and cost are all open [S16] (out of scope for this plugin's v1).
- Cap the active set at a few problems; see guardrail 5 in `guardrails.md`.
