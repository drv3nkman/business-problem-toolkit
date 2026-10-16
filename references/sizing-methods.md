# Sizing methods

How to size a problem at two depths. The methods in this file are (non-Cagan) practitioner work, and skills label them non-Cagan when they use them. Cagan quotes are named where used; the first section, labelled in its heading, is his. The methods were chosen for sizing problems and opportunities, not for prioritising features. Citations `[S<n>]` resolve to `sources.md`.

## What can't be sized before a solution (Cagan)

- **Product Fail** (Cagan, SVPG, 2015) [S51]: teams think they need a business case per item, "1) how much money will it make? and 2) how much money or time will it cost?" His answer: "The cold truth is that at this stage, we have no clue on either of these, and we can't know." Revenue "depends hugely on how good the solution turns out to be"; cost is "extremely hard for engineering to predict" without the solution.
- **2026 keynote** (Cagan) [S22]: "Whether enough people have this problem, and wish it could be solved, is rarely hard, and not where the real work is."
- **What Cagan does say about size** [S14]: 2006 question 3, "How big is the opportunity? (market size)"; look to analysts, trade associations, finance staff and your own bottom-up calculations; and "be conservative and realize that not every opportunity needs to be a billion dollar market."
- **Implication (synthesis):** estimate how big the *problem* is: who has it, how often, what it costs them or us. Do not estimate what a solution will earn or cost. **Size the problem, not the payoff.**

## Quick mode

Quick mode (non-Cagan) compares sibling candidate problems during identification. Methods, with what survives at problem stage:

| Method | Keep | Drop |
|---|---|---|
| RICE (McBride) [S52] | Reach, in a defined period; the Impact scale (Massive 3, High 2, Medium 1, Low 0.5, Minimal 0.25) as pain per person; Confidence (100/80/50%) | Effort: ÷ Effort is "total impact per time worked", a solution estimate |
| ICE (Ellis; via Gilad) [S53] | Confidence | Ease, a solution estimate. Origin and arithmetic unverified |
| Confidence Meter (Gilad) [S53][S54] | Evidence-graded confidence; see `evidence-ladder.md` | Top rungs, which usually need a solution |
| ODI (Ulwick) [S56][S57] | "Opportunity = Importance + max(Importance – Satisfaction, 0)"; outcomes "devoid of solutions". A 1–10 judgment proxy is quicker than the survey but is labelled a proxy | Nothing: fully need-based |
| Opportunity assessment (Torres) [S59][S60] | "How many customers are affected and how often?", plus importance and satisfaction with existing solutions | Effort: "we aren't exploring solutions yet" |
| Cost of Delay (Arnold; Reinertsen) [S62][S63][S64][S87] | Cost per period ("usually in $/week or $/month"); value types below; qualitative fallback Value (Killer/Bonus/Meh) × Urgency (ASAP/Soon/Whenever) | CD3 (Cost of Delay ÷ duration) [S88]: duration is a solution estimate |

ODI thresholds are secondary [S58]: above 15 "extreme", above 12 high, above 10 solid; not on strategyn.com, and disputed by one practitioner. Severity is Nielsen's frequency, impact and persistence [S61]; *people × frequency × severity* is a synthesis of Nielsen and Torres, not a named method. Torres warns against "another made-up math formula" [S60].

**Recipe (synthesis; no single source states it).** For each candidate:

1. **Who and how many** have it in a defined period.
2. **How often** it occurs.
3. **How bad** each occurrence is (0.25–3 or 0–4 scale), or the importance–satisfaction gap.
4. **Value per period, as a range**, Fermi-style: people × frequency × cost per occurrence. For internal problems, the cost of today's workaround.
5. **Urgency:** ASAP, Soon or Whenever.
6. **Confidence**, from the evidence ladder.

**Output rules.**

- Show siblings side by side in bands (L/M/H or order of magnitude) and ranges, with the assumptions and which number could change the pick. No composite score decides; Torres: "The more we quantify them, the more likely we are to treat them as truth" [S60].
- The table has no Effort, Ease, duration or revenue-projection column (Cost of Delay is a cost of the problem, not revenue earned by a solution).
- Every number carries `basis: user-estimate | data`. A user's own figure with no data behind it is `basis: user-estimate`, graded `estimates and plans`, and its confidence is never above `low`. Never upgrade it, never invent a figure; an unknown stays `[unknown: flagged]`. A figure from data names its source.

## Deep mode

Deep mode (non-Cagan) sizes one finalist and feeds `opportunity-assessment`. Definitions first, then the procedure.

- **TAM / SAM / SOM** (Wikipedia, secondary [S68]): TAM is total demand if 100% of the market were reached; SAM the part reachable by your distribution; SOM the share realistically achieved. Origin untraced and expansions vary: define them once. TAM is a ceiling, not a forecast; SOM rests on the most assumptions.
- **Top-down vs. bottom-up** (Seibel, YC) [S69]: top-down takes the total market and a share; bottom-up counts comparable products sold and the share you could take. He prefers bottom-up because it avoids "not narrowing down the customer enough". Build bottom-up, then cross-check top-down. Value-based sizing (customer value × share captured as price) has no traceable originator (secondary [S70]).
- **Inside an existing product** (Hilal, practitioner) [S71]: affected population × baseline metric (from a comparable) × expected lift × value per unit, annualised; "quantify your estimate in ranges with an upper and lower bound"; "You should be conservative in your initial estimates"; document assumptions. Her template is feature-shaped; restate it as: *if this problem were solved for segment S, metric M would move by Δ (range) in T, under these assumptions.*
- **Scale rigor to the commitment** (Harter) [S72]: "When we're deciding whether to commit 20 engineers for 6 months, we should have more confidence in our estimates."
- **Link to success measures (synthesis):** the "expected change" input is Cagan's key-results test, "would a 1 percent improvement be considered excellent or would it be considered a waste of time?" [S17]; deep sizing also sets up `success-measures`.
- **Uncertainty** (Hubbard) [S77][S78]: "A 90% CI is a range of values that is 90% likely to contain the correct value"; people are "systematically overconfident". To counter anchoring, start from absurdly high and low values and ask how likely the quantity is to be above or below each.

**Guard.** Every input is a property of the problem (people affected, cost or value lost today, share affected), never a solution's uptake, lift or earnings. If only a solution-dependent figure exists, write `[unknown: flagged]`.

**Procedure (synthesis):**

1. State the unit of value: revenue (increase or protect), cost (reduce or avoid) or an outcome metric. Define the affected population narrowly.
2. Build the estimate bottom-up: reachable customers × adoption × annual value, or affected users or accounts × % whose behaviour changes × size of change × value per unit, annualised.
3. Anchor each input to evidence (analytics, comparables, research) and record its source and `basis`.
4. Give a calibrated 90% range for each key input. Produce Low, Base and High cases, with a conservative Base case and no "1% of a big market" step.
5. Cross-check against top-down; the result must sit well inside a defensible SAM.
6. Treat market expansion as flagged upside only.
7. Name the swing variable, the assumption the result is most sensitive to, and propose the cheapest test that would narrow it.
8. Report the range, an assumptions table, the swing variable and the confidence. Answer "is it big enough to justify this team's investment?", not "is it a billion?"

## Internal and non-revenue problems

Cost of Delay value types (Arnold, Black Swan Farming) [S63]: Increase Revenue and Protect Revenue; **Reduce Costs**, "reduce the costs that we are currently incurring"; **Avoid Costs**, costs "not *currently* incurring but there is some likelihood that we will in the future, unless some action is taken." The framework was "developed and tested in a public sector environment, where profit is *not* the objective", and "what matters is **not** the $ figures. What matters is that you have the conversations about what is valuable."

- Derived (synthesis): Reduce = volume × cost per unit × reduction. Avoid = probability × impact per year.
- "If we automate process X, the value of the change is equal to the cost of executing process X manually"; "having a number is usually better than having no number at all" [S64].
- Where neither finance input nor data exists, use the qualitative fallback (Value × Urgency) [S87] and label it qualitative.

## Choosing rules

These rules are synthesis (non-Cagan), each tied to its sources.

1. **Size to a threshold, not a rank.** "Its often much harder to ask 'How much is X' than 'Is X enough'" (Hubbard slides) [S80]. Stop once a problem clearly clears the bar (Cagan [S14][S22]).
2. **Estimate only what could change the choice.** Hubbard (secondary, quote site): a measurement matters only if it has "some conceivable effect on decisions and behaviour" [S67]. "The value of information is simply the cost of being wrong times the chance of being wrong" [S80].
3. **Use no input that depends on a solution:** no revenue projections (Cagan, "we can't know" [S51]), effort or Ease (Torres [S59]), or CD3 duration [S88].
4. **Put value as Cost of Delay with urgency,** a range and stated assumptions, not relative points [S64][S66]. Reinertsen's "If you only quantify one thing, quantify the cost of delay" is verified only through a secondary list [S65].
5. **Compare siblings, never one problem alone.** "Is this idea good or not?" treats "good" as an absolute; "Which of these ideas looks best?" does not (Torres) [S81].
6. **Label numbers rough, subjective and revisable;** show ranges and assumptions; no total score decides alone [S60].
7. **Treat the choice as a two-way door.** Bezos: decisions are "changeable, reversible", made with "around 70% of the information you wish you had" [S82][S83]. Torres (secondary, quote site): choosing a target means "simply committing to exploring it further" [S84].
8. **Cap output at 2–3 problems with explicit "not now" decisions.** Rumelt via Cagan (SVPG strategy series): "one, or a very few, pivotal objectives" [S38]. The hard part is saying no to "less promising (but still good!) ideas" (Goetzmann, secondary [S85]).
9. **Never declare "the most important problem."** Cagan's 2026 keynote calls the question "fruitless and unanswerable" [S22]; see `guardrails.md`. Confirm the problem is real and big enough, then hand off to solution discovery.
10. **Without a strategy, don't score.** "In the absence of a product strategy, the most critical job function of a Product Leader is to set one" (Perri) [S86]. Route the user to `strategic-context` first.

## Pitfalls

- **Overestimating.** Kawasaki: "An entrepreneur's projections are never conservative. If they were, they would be $0" [S73]. A vendor blog post (secondary): 1% of "office productivity market" is as meaningless as 1% of "the software market" [S74]. Damodaran's "big market delusion": overconfidence yields "unrealistic judgments of future profits" [S75].
- **Underestimating.** Gurley: "The past can be a poor guide for the future if the future offering is materially different"; a 1980 forecast of 900,000 US cell phone subscribers for 2000 was under 1% of the actual figure [S76].
- **Reconciliation (synthesis):** base case on the incumbent market; model expansion only as flagged upside, and only if solving the problem would materially change price, access or use cases.
- **Rigor varies:** ODI needs survey data; Cost of Delay works best with finance input. Without them, label qualitative fallbacks as such.
- **Unverified at the primary source:** RICE's original date, ICE's origin and arithmetic, Gilad's numeric values, ODI thresholds, Reinertsen's E3 wording, most Hubbard quotes, value-based sizing's originator, the year of Kawasaki's post. Hilal's and Harter's templates are feature-shaped; restate them around the problem.
