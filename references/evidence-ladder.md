# Evidence ladder (non-Cagan)

How much to trust a piece of evidence, graded by its type. The ladder is Itamar Gilad's Confidence Meter (non-Cagan) [S53][S54]; Cagan publishes no evidence scale. Skills copy the rung names below, exactly as written, into the "Ladder rung" column of a card's Evidence table. Citations `[S<n>]` resolve to `sources.md`.

Gilad: "Confidence values are the antidote — they keep us honest about our assumptions" [S53]. McBride (non-Cagan) uses Confidence the same way, to "curb enthusiasm for exciting but ill-defined ideas" [S52].

## The ladder

Ascending: the lowest rung is first, the strongest last. The rung names and their order come from the Confidence Meter [S53] (also a secondary write-up [S55]); the "What counts" column is the plugin's gloss, not Gilad's wording. Each rung maps to one confidence band; a card's `confidence` is the band of the highest rung present.

| Rung | Band | What counts at problem stage |
|---|---|---|
| self-conviction | very-low | "I'm sure this matters": the author's own belief |
| pitch deck | very-low | A slide-deck argument for the problem, made by someone advocating it |
| thematic support | very-low | Broad trends or themes that "support" the problem without measuring it |
| others' opinions | very-low | Stakeholder, executive or colleague views, with no data behind them |
| estimates and plans | low | The team's own back-of-envelope sizing, forecasts or plans |
| anecdotal evidence | low | A few tickets, calls or stories, not a systematic sample |
| market data | medium | Industry or analyst figures, comparables, competitor facts |
| user/customer evidence | medium | Interviews, observation, support or usage data that show the problem |
| test results | high | Results of an experiment or prototype test |
| launch data | high | Measured behaviour after a real release |

## Using the ladder

- **Grade the type of evidence, not how loud it is.** Put one rung per Evidence-table row and take the highest rung present as the card's band.
- **The mapping of "pitch deck" and "thematic support" is a plugin decision.** Spec §5.3 names only self-conviction, others' opinions, estimates, plans, anecdotes, market data, user/customer evidence, test results and launch data; it does not place the pitch-deck or thematic-support rungs, so this plugin puts them with the other `very-low` rungs.
- **The bands are the output.** Gilad's numeric values (0.01 up to 10) come only from a secondary source [S55] and are not used here.
- **A user's own estimate is graded `estimates and plans` (`low`) unless data backs it.** It is never promoted just because it is stated confidently; see `sizing-methods.md`, Quick mode.
- **Low confidence is a flag, not a stop.** Record what evidence would raise the band as a "learn next" item and keep moving (guardrail 1, *Frame fast, never gatekeep*; see `guardrails.md`).
- **Verdicts.** A graded card ends with `Evidence verdict: ready to frame` or `Evidence verdict: frame with flagged assumptions`.

## Caveats

- **The top rungs usually need a solution.** Test results and launch data usually need a solution, so at problem stage a card rarely reaches `high`. Do not go looking for it, and never invent it.
- **Numeric values and rung order.** Gilad's own site was not checked for the numbers; the Votito write-up [S55] is secondary.
- **A band is a rough, revisable label,** not a measurement. It sits beside the evidence it summarises, never in place of it.
