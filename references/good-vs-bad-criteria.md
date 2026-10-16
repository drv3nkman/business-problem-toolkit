# Good vs. bad problem statements

Criteria drawn from Cagan's texts. Cagan gives criteria and examples but no "[user] needs [X] because [Y]" formula, so any statement template is derived. The criteria prompt judgment; they are not a score. Citations `[S<n>]` resolve to `sources.md`. The "Example" columns are invented and generic, written for this reference.

## Statement criteria

| Criterion | Good (Cagan) | Bad (Cagan) | Good example | Bad example |
|---|---|---|---|---|
| Solution-free | Allows "any number of potential solutions" [S1] | Names a feature, app or project | Reduce the share of new customers who give up before finishing setup | Build a guided setup wizard |
| Clear and meaningful | Executives can define and measure it [S4] | Vague, e.g. "provide integrated platforms" (Cagan's own bad example) [S4] | Reduce the time a customer waits for a first reply | Improve the support experience |
| Outcome-linked | Success is a business result | A key result of "ship X": activity or output [S1] | Key result: the share of requests resolved on first contact rises from its current baseline | Key result: launch the new help portal |
| Customer-anchored | States a customer problem and the target customer | A rambling list of features and capabilities [S14] | Small-team administrators re-enter the same details in three places each week | Customers need better reports, exports, alerts and dashboards |
| Strategy-traceable | Maps to an assigned objective and the product strategy [S17] | A stakeholder request with no "why" [S5] | Serves the assigned objective "reduce monthly churn" under a strategy focused on retention | The regional lead asked for it |
| Impactable | The team can move it and measure it [S4] | Outside the team's levers, or not instrumented | The team owns the checkout flow and has its event data | A team with no access to supplier systems is asked to cut supplier lead times |
| Not metric-driven | Chosen for importance, with new KPIs if needed [S4] | Chosen because a KPI already exists ("letting the tail wag the dog") [S1] | Customers abandon early, and no measure of that exists yet, so one is defined | Raise page views per visit because it is on the dashboard |

Notes:

- **Form** (*synthesis*): verb + measurable thing + for whom, e.g. "Reduce the time for a user to produce their first monthly report" [S4].
- **Altitude**: problems exist "at different levels of granularity". "Problems around optimizing existing metrics are usually the easiest to articulate… In other scenarios, getting to clarity can be quite challenging, but often that's where the major opportunities are." [S4]
- **Feature team vs. product team** (secondary: a reader reply on a 2019 tweet; illustrative only): feature team "O: Improve activation revenue; KR: Ship new onboarding workflow in Q4"; product team "KR: Achieve 30% improvement from Sept baseline in December cohort activation rate." [S39]
- **A statement is premature** if it cannot cite customer evidence and business context (*synthesis*, from the four deep-knowledge areas) [S7].

## Cagan's example objectives

From "Team Objectives – Empowerment" (2020) and "Outcomes Are Hard" (2025). Each is qualitative; the measure sits in the key results [S1][S4].

- Reduce the frequency of parcels delivered to the wrong address [S1]
- Increase the percentage of shipments delivered with next-day delivery [S4]
- Reduce the subscriber churn rate [S4]
- Decrease the time it takes a job seeker to find a new job [S1][S4]
- Reduce the cost to acquire a new customer [S4]
- Increase the percentage of new customers that successfully create an account [S1]
- Help customers solve issues without having to contact us [S4]
- Make it easier for patients to reliably share data with their doctors [S4]
- Connect job seekers with more suitable jobs [S4]
- Demonstrate product/market fit for an existing product in a new market [S1]

**Worked example with a backstop** (Cagan) [S1]:

- Objective: Reduce the frequency of parcels delivered to the wrong address.
- KR1: reduce percentage of incorrect deliveries.
- KR2: "while ensuring that total deliveries continues to grow."

### Problem framing in Cagan's case stories

*Transformed* (2024) lays every innovation story out as Company Background → The Problem to Solve → Discovering the Solution → The Results [S40][S41]. The full problem statements and result metrics are not public in previews; do not invent them.

- **Kaiser Permanente** (primary preview): began its product-model transformation in 2019 around "reimagining the patient health journey"; the pandemic then forced care delivery to change. The preview cuts off before the problem is stated, so any specific problem is not Cagan's text [S40].
- **CarMax** (primary preview): leaders "saw consumer expectations beginning to change, especially around the desire for an online shopping and buying experience", plus digital-native competitors. An industry and qualitative insight turned into a problem [S42]. A secondary write-up adds trust and margin constraints for remote large purchases, which are viability constraints [S43].
- **Trainline** (secondary only): customers "consistently perceived rail tickets as being too expensive": a customer-perception problem, not a feature request [S44].

## Discovered-candidate criteria

Ten criteria for a candidate problem that `problem-discovery` writes from evidence (synthesis). They are kept apart from the statement criteria above: a candidate is a rough first draft tied to evidence, not a finished statement. Most bases are non-Cagan; Cagan's own is the last row. The examples are illustrative, not drawn from sources, and invented for this reference. An unknown quantity is written `[unknown: flagged]`, never estimated.

| Criterion | Good | Bad | Basis |
|---|---|---|---|
| More than one way to address it | Approvers can't tell which requests are urgent | We need a priority flag on requests | Torres's test (non-Cagan) [S59] |
| Grounded in observed past behavior | In 4 of 6 interview notes, admins describe re-keying invoices from email | Users would probably like automation | Torres (non-Cagan) [S59]; *Mom Test* (non-Cagan; secondary) [S102] |
| Specific who, when and context | New branch managers, in their first month-end close | Users find reporting hard | Torres digest (non-Cagan; secondary) [S96] |
| States a need, not a feeling or a category | Callers can't find out whether their application was received | Communication problems; users are frustrated | Torres digest (non-Cagan; secondary) [S97]; Kepner-Tregoe summary (non-Cagan; secondary) [S108] |
| Solution-free, with a direction (optional form) | Minimize the time it takes to confirm an application was received | Add an SMS confirmation | Ulwick (non-Cagan) [S98] |
| Present-tense state of the system (operational) | Purchase orders wait [unknown: flagged] days for a second signature | Implement e-signature | TOCICO (non-Cagan; secondary) [S109] |
| Underlying problem, not symptom | Parent: customers can't predict their monthly bill. Children: billing tickets, downgrade spikes. | Three separate top-level cards, one per ticket category | Torres (non-Cagan) [S59]; Card (non-Cagan) [S110] |
| Purpose and product levels both tagged | Purpose: residents need to know if they're eligible before starting | Only: the eligibility page is confusing | Young (non-Cagan) [S105] |
| Reframed, not just restated | Waiting for the lift feels long, alongside the lift is slow | Only: the lift is slow | Wedell-Wedellsborg (non-Cagan) [S111] |
| Assertion kept separate from evidence | A VP says onboarding is broken; support data shows two related tickets, so evidence is thin | Onboarding is broken (CEO), with no evidence noted | Cagan, "Last Customer Visited" [S95] |
