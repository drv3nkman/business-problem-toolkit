# Discovery lenses

Lenses, prompts and writing rules for `problem-discovery`. Only the first section is Cagan's; everything after it is (non-Cagan) practitioner or government work, labelled where used. "Synthesis" is this plugin's reading across the sources, "plugin decision" is a choice this plugin makes, and Cagan quotes are named as his. Sources marked secondary were reached through summaries. Citations `[S<n>]` resolve to `sources.md`.

## Cagan lenses

The first four are Cagan's insight types [S23]; see `insight-sources.md`.

1. **Quantitative:** funnel, retention, sales and usage data.
2. **Qualitative:** especially generative research, "did we uncover any new opportunities that we weren't pursuing?" [S23]
3. **Technology:** what is newly possible, which may reveal long-standing problems solvable in new ways [S23].
4. **Industry:** competitors, trends, other industries and regions [S23].
5. **Customer misbehavior and workarounds:** customers using the product for problems it wasn't built for; Cagan: "learn what problem they are trying to solve" [S89].
6. **Context gaps:** the distance between the product vision and today, and scorecard misses. Cagan names the product vision and the scorecard as the two main sources of opportunities [S15]; reading them as gaps is a plugin decision.

Items 5 and 6 are additions to Cagan's four. Cagan's quote on item 5 is his; the lens built on it is a plugin decision.

## Non-Cagan lenses

Each lens below is non-Cagan and is labelled so in output.

### Switch forces (non-Cagan)

Moesta and Spiek, forces of progress [S100][S101]:

- Four forces act on a switch. **Push** is the problem with the current situation, **Pull** the attraction of the new, **Anxiety** fear of the new, **Habit** the comfort of the current. In their words, "When push and pull beat anxiety and habit, people change." [S100]
- The switch interview walks a person back through an actual switch, step by step [S100].
- Use (synthesis): sort "why people use or don't use" answers into push, anxiety and habit. Push is the problem in its rawest form; anxiety and habit explain non-adoption; churn is a switch away. Use it to read churn and win/loss material, not as a required study.

### Job map (non-Cagan)

Ulwick, outcome-driven innovation [S98][S99]:

- A need statement has four parts: a direction of improvement (such as minimize), a metric, the object of control and a contextual clarifier. Statements should be stable over time and free of solutions [S98].
- The job map breaks the core job into steps that don't depend on any solution: define, locate, prepare, confirm, execute, monitor, modify, conclude [S99]. Ulwick typically captures several outcomes per step and more than 100 per job.
- Use (synthesis): the sentence form is optional, and the map is a checklist: which step of the job does this evidence say goes badly? The outcome inventory and the scoring are out of scope; scoring is in `sizing-methods.md`.

### Operational: undesirable effects and IS / IS NOT (non-Cagan)

- **Kepner-Tregoe** starts from a deviation (what should be happening versus what is) and specifies it as IS / IS NOT across what, where, when and extent, finding causes from data rather than assumptions [S107]. A secondary summary adds: break vague categories such as "communication problems" into specifics [S108].
- **Theory of Constraints, undesirable effect (UDE)** (secondary: a search excerpt of the TOCICO Dictionary, 2007, and a matching copy) [S109]: a negative aspect of current reality, judged against the system's goal, and "a visible symptom of an underlying root cause". A good UDE is a present-tense complaint about the state of the system, not an action. Later TOC writing (Dettmer) narrowed it to a failure to meet a critical success factor or the goal.
- Use (synthesis): IS / IS NOT sharpens a candidate's scope without anyone needing to find the cause yet; UDE wording is the writing rule for internal and operational candidates. Neither is used to prove causes.

### Purpose vs. product level (non-Cagan)

Indi Young [S105]:

- The problem space is people's purposes, thinking, reactions and guiding principles, described without reference to any solution; the solution space is working with your own ideas. Problem-space research stays useful over time because it isn't tied to a solution cycle.
- Secondary podcast notes report her view that journey maps belong to the solution space [S106].
- Use (synthesis): a candidate about the person's purpose is durable; one about friction with our product is narrower. Plugin decision: tag both and drop neither.

## Elicitation prompts

For Elicit mode, when there are no inputs or the user wants to talk it through. Non-Cagan.

- *The Mom Test* (Fitzpatrick; reached through summaries only) (secondary) [S102][S103][S104]: talk about the person's life, not your idea; ask about specifics in the past, not opinions about the future; listen more than you talk. Compliments and opinions are not evidence, statements about future behavior are over-optimistic, and generic answers ("always", "usually", "would") get anchored back to the last specific time it happened.
- Torres (non-Cagan) wants opportunities to come from story-based interviews about specific past behavior, prompted with "tell me about a time when…" [S59]. Opportunities invented from scratch bring in the team's own biases.
- Plugin wording, past-tense and specific:
  - "Tell me about the last time [situation]. What happened, step by step?"
  - "What did you do next? What had you tried before?"
  - "When did you stop, or decide not to start? What was going on that day?"
  - "What were you using before, and what kept you with it?"
  - "Where did work wait or get redone last week?"
  - "When was the last time that happened?" (for any "always", "usually" or "would")
- Plugin decision: ask for, never require, in this order: raw verbatims of any kind; something from people who left or never started; one operational trace of where work waits or gets redone.
- Torres treats sales calls, support tickets and other secondhand material as inspiration for what to explore in upcoming interviews, since it usually lacks context [S59]. Document-derived candidates are output with "what we'd need to learn next".

## Candidate-writing rules

Spec §7.3, verbatim in substance (plugin decisions). The sources for the individual rules are (non-Cagan) practitioner work, named per rule:

1. Name **who**, the **situation** and the **unmet need**, pain point or desire. Torres defines an opportunity as an unmet customer need, pain point or desire [S59]; a good one is specific to a time, a context and a customer (secondary digest [S96]).
2. Pass the "more than one way to address this?" test: "Is there more than one way to address this opportunity?" If not, it is a solution (Torres, non-Cagan [S59]). Move it to candidate solutions.
3. No feature, technology or vendor names.
4. No bare feelings ("users are frustrated") and no bare categories ("communication problems") (Torres digest, secondary [S97]; Kepner-Tregoe summary, secondary [S108]).
5. Write operational problems as the present-tense state of the system (TOC UDE, non-Cagan; secondary [S109]).
6. Ulwick's outcome form (direction, metric, object, clarifier) is optional (non-Cagan [S98]).
7. Every candidate cites at least one verbatim excerpt with file and location, or is marked `**Assumption:**` (synthesis).
8. Unknown quantities are written `[unknown: flagged]` and never estimated (guardrail 3). Anything about size goes to the learn-next list.

## Reframing prompts

Wedell-Wedellsborg, "Are You Solving the Right Problems?" (*HBR*, 2017) [S111], non-Cagan:

- Most of the 106 C-suite executives he surveyed said their organizations were bad at diagnosing problems and that this was costly.
- The aim is to "see if there is a better problem to solve", not to find the one real problem. This fits "frame fast, never gatekeep".
- His seven practices:

1. Establish legitimacy.
2. Bring in outsiders.
3. Get people's definitions in writing.
4. Ask what's missing.
5. Consider multiple categories.
6. Analyze positive exceptions.
7. Question the objective.

- Plugin decision: the quick pass asks three questions, namely practices 4, 6 and 7: what's missing, where the problem doesn't happen, and whether the objective is right. Add any better framing as a sibling candidate and do not replace the original. Practices 1, 2, 3 and 5 need other people, so they are optional prompts for a group, not a workshop.

## Merging and clustering

- **Torres structure** (non-Cagan) [S59]: build an experience map from the stories, map its moments to top-level opportunities, group individual opportunities under the moment where they occur, and use parent-child and sibling relationships within each branch. Start mapping after three or four stories, treat the first map as a rough draft, and revise every three or four interviews. One tree per team; company-wide views use a KPI tree or a company-wide experience map.
- **5 Whys** (Ohno, 1988; secondary, reached through Card, book not opened) [S110]: ask "why" five times.
- **Card's critique** (non-Cagan; *BMJ Quality & Safety*, 2017) [S110]: the method forces a single causal path, insists on one root cause and assumes the deepest "why" is the best place to intervene; "not simple, but simplistic". For discovery, climb from a symptom to the problem underneath, allow several parents, and don't assume the deepest level is the right altitude.
- Plugin decisions:
  - Group candidates by journey moment or job step; climb one or two "why" levels to find parents.
  - Symptoms become child cards or evidence, not top-level candidates.
  - Count distinct sources, not mentions.
  - Tag altitude: team, multi-team or company.
  - A company-level candidate may be phrased as a diagnosis (Rumelt; secondary [S112]), but is never declared "the most important problem".

## Public services and internal tools

GOV.UK Service Manual, "How the discovery phase works" (non-Cagan) [S113]:

- Before building, understand the problem: users, constraints (legislation, contracts, legacy technology, existing processes), the underlying policy intent, and opportunities to improve things. Don't start building the service during discovery.
- No set length; about 4 to 8 weeks is typical, and the purpose should set it.
- Given a predefined solution, interrogate and reframe it as a problem. The manual's example turns a request for an interactive map of contact centres into making it easier for people to find their nearest one. Reframing also means agreeing what is not part of the problem.
- Sort constraints into hard (primary legislation) and soft, and don't simply work around the soft ones.
- Research may point to alternatives to building a service, such as better content or a partnership.
- "It's not a failure to stop at the end of the discovery phase" when the research shows that is the right call.
- Supporting: "Discovery is not for validation" [S114]; most discoveries run 6–8 weeks in NSW's toolkit [S115]; four to six weeks is common at the ONS, with a case for a minimal viable discovery [S116].
- Tension: the manual also suggests quantifying what the problem currently costs. The plugin does not size during discovery, so cost goes to the learn-next list.
- Synthesis: these are team phases lasting weeks; the skill is a first pass in one sitting. What carries over is the stance: problem before solution, reframe given solutions, stopping is acceptable.
- Plugin decision: for a public service with no strategy, flag it and ask for the policy intent as a stand-in. Cagan's problem-definition guidance is written mostly for commercial products (synthesis), so internal tools use the operational lens and the same rules.

## Working from documents

The material on AI-assisted synthesis is thin and mostly vendor-sourced; the rules below are a precaution, not a proven safeguard.

- NN/g: generative AI can speed up qualitative analysis, but teams should make the tool link each insight back to the original data. It cites a Stanford study in which AI legal research tools were inaccurate 17% to 33% of the time [S120].
- A 2025 preprint on GenAI in UX research reports that product managers were less critical of GenAI output than researchers; a direct risk for this plugin's audience [S121].
- A vendor blog (secondary) describes "hallucinated themes", plausible patterns not grounded in the data, and recommends asking for the exact quote behind each theme [S122].
- A Product Talk post (Sept 2026, seen only as a teaser; unverified) suggests AI-generated opportunity trees produce too many top-level opportunities.

Synthesis, as rules for a skill that reads documents:

1. Every candidate cites a file, a location and a verbatim excerpt.
2. Keep observation (what the source says) separate from interpretation (the problem we infer).
3. Count distinct sources, not mentions.
4. Anything without a quote is marked as an assumption.
5. Keep the top level small and merge upward.

## Stopping rules

Plugin decisions and heuristics:

- Stop at the timebox, or when one whole input adds no new candidate. **This is a heuristic**, an analogy to interview saturation, not a validated rule.
- Plugin-default carve-out (heuristic; checked against test-run data and left unchanged): with a handful of short, distinct inputs, read them all; the "adds nothing" stop is for long or numerous inputs of the same kind (exports, many interviews).
- Suggest a re-run after 3–4 new substantial inputs. Torres revises her map every three or four interviews and interviews at least weekly [S59].
- If nothing credible turns up, say so. Stopping there is fine; "It's not a failure to stop" [S113].
- Never stop for lack of certainty: uncertainty goes into confidence and the learn-next list, and unknown quantities are written `[unknown: flagged]`.
- Two plugin defaults, also heuristics (starting values, not validated; checked against test-run data and left unchanged): a 60–90 minute timebox for a sitting, and a small top level of ≤ 7 top-level candidates, merging upward beyond that.
- Saturation studies (secondary: reached through abstracts only). Their interview counts come from academic studies of homogeneous samples and do not transfer directly:
  - Guest, Bunce and Johnson (*Field Methods*, 2006): saturation within twelve interviews, basic metathemes by six (secondary) [S117].
  - Hennink, Kaiser and Marconi (2017): code saturation at nine, meaning saturation needed 16–24 (secondary) [S118].
  - Hagaman and Wutich (2017): 16 or fewer for common themes in one site, 20–40 for metathemes across sites (secondary) [S119].

## Situation table

Synthesis: which lenses suit which starting situation. Switch forces, operational and job-map rows are non-Cagan.

| Step | Existing product with data | New market or bet | Internal tool | Public service, no strategy |
|---|---|---|---|---|
| Frame | The team objective | The bet hypothesis; flag that there is no outcome | The cost or efficiency objective | Flag the absence; use the policy intent as a stand-in |
| Quantitative, funnel, churn | Core | Mostly absent; flag it | Usage logs, cycle times | Contact volumes, if supplied |
| Switch forces | Churn, win/loss | Non-consumption, today's workaround | Shadow tools (habit) | Offline channels, giving up |
| Misbehavior, workarounds | Core | Core: what people hack together today | Core: spreadsheets | Core: intermediaries, repeat calls |
| Operational, UDE, constraint | Secondary | Rare | Core | Core, with hard and soft constraints |
| Technology, industry | Core | Core | Secondary | Secondary: other services and departments |
| Reframing | Useful | Core | Core: who is the user? | Core: reframe given solutions |
| Learn next | Interviews to add context | Story-based interviews with the target segment | Observing operators | Research with service users, including excluded groups |

## How these methods relate to Cagan

Synthesis.

| Method | Fit with Cagan | Tension | How the skill reconciles it |
|---|---|---|---|
| Torres opportunity mapping | Close. Opportunities sit under an outcome, as problems sit under Cagan's team objectives. | Torres wants story-based interviews before mapping, which the skill can't run. | Treat documents as inspiration. Output candidates plus prompts for the next interviews. |
| Moesta forces | Matches "why are people using – or not using" and "chooses to switch." | It is a research method, and Cagan warns against long research. | Use it as a lens for reading churn and win/loss material, not as a required study. |
| Ulwick ODI | Solution-free statements support "problems, not solutions." | Collecting 100+ outcomes is heavy, and ODI goes on to scoring. | Borrow only the sentence form and the job-map checklist. |
| *The Mom Test* | Supports "customers are not the source of innovation": problems from customers, solutions from the team. | None of substance. | Use for elicitation prompts when there is no data. |
| Wedell-Wedellsborg | Fits "frame fast, never gatekeep." He also rejects hunting for the one real problem. | Little. | Use as quick reframing prompts, not a workshop. |
| GOV.UK discovery | Fits "understand the problem" before solutions. | 4–8 weeks of "don't build" reads as gatekeeping next to Cagan's entangled problem and solution. | GOV.UK describes a team phase; the skill is a first pass in one sitting. Keep "it's OK to stop." |
| Kepner-Tregoe, TOC, 5 Whys | Not Cagan; useful for internal and operational problems. | Root-cause rigor can turn into analysis paralysis. | Use IS / IS NOT and UDE wording to frame candidates, not to prove causes. |

Synthesis: Cagan's 2026 regret is aimed at PMs acting as gatekeepers and at over-investing in proving that a problem exists [S22]. The non-Cagan methods mainly improve how candidates are worded and traced; they don't need to make discovery longer. The skill satisfies both if it runs in one sitting, produces a deliberately rough first draft, never blocks the user from moving on, and turns open questions into a "what we'd need to learn next" list rather than prerequisites.
