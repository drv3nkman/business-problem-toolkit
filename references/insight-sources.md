# Insight sources

Where the evidence for candidate problems comes from. The first sections are Cagan's own; the last table is synthesis (this plugin's reading across the sources, not any one source's text) that points each signal at a lens, and some of those lenses are non-Cagan (see `discovery-lenses.md`). Quotes are Cagan's unless marked. Citations `[S<n>]` resolve to `sources.md`.

## Four insight types

From "Product Strategy – Insights" (SVPG, 2020) [S23]:

- **Quantitative:** product data such as "your business model, your acquisition funnel, your customer retention factors, your sales execution data". Insights often require constructing live-data tests.
- **Qualitative:** user research, split into *evaluative* ("did it work?") and *generative* ("did we uncover any new opportunities that we weren't pursuing?"). Generative research is where new problems come from.
- **Technology:** new enabling technology "allows us to solve long-standing problems in new, just-now-possible ways", often surfaced by engineers as prototypes.
- **Industry:** competitors, broad trends, other industries, other regions, analysts.
- Prerequisite: insight "*never* happens without real preparation… after you've spent hours studying your data, your customers, the enabling technologies and your industry", grounded in the strategic context.
- Plugin decision: these four become the first four Cagan lenses in `discovery-lenses.md`, with customer misbehavior and context gaps added.

## Four kinds of deep knowledge

*Inspired* 2nd ed., ch. 10. The chapter headings (O'Reilly table of contents) are Deep Knowledge of the Customer, of the Data, of Your Business, and of Your Market and Industry [S17][S32]. The wording below is paraphrase from reader summaries (secondary), not Cagan's text:

- **Customer:** "their issues, pains, desires, how they think—and for business products, how they work, and how they decide to buy." (secondary) [S33][S34]
- **Data:** analytics and A/B tests. (secondary) [S35]
- **Business:** stakeholders, constraints, economics, finance, sales and go-to-market, legal. (secondary) [S35]
- **Market and industry:** competitors, technology trends, customer expectations, analysts. (secondary) [S18][S36]

The 2026 "Build To Learn FAQ" restates this as the PM's "*product sense*": "deep knowledge of the customers, the data, the industry and the business" [S7]. These four areas are the evidence base. A problem statement that cannot cite at least customer evidence and business context is premature (synthesis).

## Why people use or don't use the product

- Synthesis: qualitative evidence includes *why people use or stop using the product*.
- Cagan's 2026 regret #3 names the wrong "why": the PM treating their main contribution as explaining why the problem matters, which strategy should already do, rather than investigating "*why are people using – or not using – our product?*" [S22]
- Plugin decision: ask this question of every input and sort the answers into push, anxiety and habit. Those forces are non-Cagan (Moesta and Spiek); see *Switch forces* in `discovery-lenses.md`.
- Plugin decision: ask for something from people who left or never started. Evidence from current customers alone is a pitfall (`anti-patterns.md`).

## Customer misbehavior

"The Power of Customer Misbehavior" (Cagan, SVPG, 2015) [S89]:

- Two traditional routes to opportunities: look for market areas where significant pain exists, or start from what new technology or data makes possible and match it to that pain.
- A third: let customers use the product for problems it wasn't built for, then study what they are doing. When you see this, Cagan advises you to dig in and "learn what problem they are trying to solve." Enough cases reveal patterns.
- This is the Cagan basis for the workaround lens: side spreadsheets, unintended use, repeat contacts, intermediaries.

## Customers are a source of problems, not solutions

- In his Business of Software talk Cagan argues that "our customers don't know what's technically possible" [S90]. Customers struggle to know what they want until they see it [S10][S90].
- Synthesis: take problems from customer evidence; do not treat a customer's proposed fix as a problem. Plugin decision (guardrail 2): keep the fix, labelled as a candidate solution.
- Charter Customer Programs (SVPG, 2007; updated 2018 as the Customer Discovery Program) recommends a set of reference customers developed alongside the product; for business products the key number is six [S91]. This is mostly solution discovery for a new product, so the plugin does not run it.
- A reader summary (secondary) describes the target customers as ones who already feel the pain acutely [S92]. The idea is useful for scoping discovery on a new bet.

## Understand the problem, then prototype

- The "Build To Learn FAQ" (Apr 2026) describes discovery as needing to "understand the problem, then quickly prototype solutions" [S7].
- "Build to Learn vs Build to Earn" (Apr 2026) puts the bottleneck in finding a solution good enough that customers choose to switch to it [S93].
- Synthesis: problem discovery is the short first step. Cagan's "switch" language lines up with Moesta's forces of progress.
- SVPG's AI resource guide (2025) says an AI-generated PRD does not replace discovery and that an AI answer still has to be evaluated [S94]. A skill that generates candidate problems takes the same stance.
- Leader anti-pattern: "You're Not Helping" (SVPG, 2010) names "Last Customer Visited", a leader who wants to change direction from the most recent customer's issues [S95]. See `anti-patterns.md`.

## Signals and what they reveal

Synthesis; no single source states this table. The lens column uses the names in `discovery-lenses.md`.

| Signal | What it can reveal | Lens |
|---|---|---|
| Funnel drop-off | Where in the job people stall | quantitative / job map |
| Cohort churn, cancellation reasons | Why people switch away | switch forces |
| Win/loss notes | Why people switch to or from us | switch forces |
| Support contact reasons, tickets | Where the product or service fails the job | support |
| Zero-result searches | Demand the product doesn't meet | quantitative |
| NPS/CSAT verbatims, app reviews | Unprompted complaints (self-selected) | qualitative / support |
| Workarounds, side spreadsheets, unintended use | Needs the product almost serves | Cagan's misbehavior |
| Waits, rework, re-keying, handoffs | Operational waste | process / constraint |

Torres's caveat (non-Cagan) applies to every row: these signals surface candidates, but usually without the context needed to frame them well [S59].
