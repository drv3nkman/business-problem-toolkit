---
id:                                # P-NNN, matching the filename prefix
problem:                           # "<verb + measurable thing + for whom, solution-free>"
type:                              # customer | business | both
who:                               # "<affected segment>"
altitude:                          # team | multi-team | company
origin:                            # a list, most specific kind first: - kind: <kind>  /  ref: "<inputs/ file + location, or original text>"
                                   # kind: quantitative | qualitative | technology | industry | vision-gap | scorecard-gap | request | switch | support | workaround | process | constraint | stakeholder
level:                             # purpose | product
parent:                            # P-00X, only when merged under a broader problem
children: []
distinct_sources:                  # whole number: distinct sources, not mentions
evidence_grade:                    # "<rung> (provisional)"; discovery sets it, problem-evidence finalizes it
discovered_in:                     # discovery/sweep-<date>.md
confidence:                        # very-low | low | medium | high
quick_size:                        # empty until opportunity-sizing runs; discovery never sizes
  reach:
  frequency:
  severity:
  value_per_period: { low: , base: , high: , unit: , basis: }   # basis: user-estimate | data
  urgency:                         # asap | soon | whenever
status:                            # candidate | shortlisted | chosen | not-now | assessed | framed | assigned
not_now: { reason: , revisit_when: }
candidate_solutions: []
links: { statement: , sizing: , assessment: , objectives: }
updated:                           # YYYY-MM-DD
---

*Derived template — Cagan publishes no problem-statement template.*

## Problem

<Who has the problem, in what situation, and the unmet need, pain point or desire. No feature, technology or vendor names. Write operational problems as the present-tense state of the system. Not a bare feeling ("users are frustrated") and not a bare category ("communication problems").>

## Observations

<!-- One row per observation. Verbatim: an exact excerpt from the cited source (no paraphrase). Location: row, page, timestamp or section. Evidence kind: the origin kind, or direct observation, self-report, stakeholder assertion or aggregate number. If you cannot quote a source, remove the row and mark the claim **Assumption:** instead. -->

| Source | Location | Verbatim | Evidence kind |
|---|---|---|---|
| <inputs/ file> | <location in the file> | <verbatim, quoted exactly> | <evidence kind> |

## Interpretation

<What the observations suggest, kept apart from the observations. Distinct from other cards. Write an unknown quantity as `[unknown: flagged]`; never estimate it.>

## What we'd need to learn next

- <The missing who, how often (flagged, never estimated), where it does and does not occur, and the cheapest next source.>

## Where it does / doesn't occur

<Optional pair: where the problem does occur, and where it does not. If you have not looked yet, write a short "not yet examined" note.>

## Evidence

<!-- Filled by problem-evidence, which replaces the line below with a table and a verdict line, in this form: | Claim | Evidence | Insight type | Ladder rung | (one row per claim; insight type: customer, data, business or market; ladder rung: copy a rung name exactly as written in references/evidence-ladder.md (non-Cagan)), then a line  Evidence verdict: ready to frame  or  Evidence verdict: frame with flagged assumptions  (readiness to frame, never worth). -->

_Pending: run problem-evidence._

## Viability screen

<!-- Optional. viability-constraints (screen mode) replaces the line below with a yes/no list of deal-breakers for this problem, each with who to consult. Never evaluate a solution here. -->

_Pending: run viability-constraints (screen mode)._

## Notes

<Anything worth keeping that fits nowhere else.>

## History

- <YYYY-MM-DD> <event: created, status change, solution attempt>
