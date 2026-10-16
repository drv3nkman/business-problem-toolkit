# Business Problem Toolkit

A plugin for Claude Code and Cowork that helps you find, choose and frame business problems before you design a solution. It has 15 focused skills and a router (`define-problem`). The skills turn a vague sense that "something's wrong", a pile of notes or tickets, a list of candidate problems, a feature request or an assigned objective into 2–3 well-framed problems. Each framed problem gets an outcome-based key result with a backstop and constraints recorded up front; chains that start from a vague sense of trouble or a candidate list end with a team assignment. The work is saved as Markdown files in a `problem-work/` folder in your project. The router pauses after every step so you can confirm, edit, skip or keep going. The plugin never ranks a single "most important" problem and never acts as a gatekeeper. It is generic and industry-neutral.

## Install

### Claude Code

From a Claude Code session:

```
/plugin marketplace add drv3nkman/business-problem-toolkit
/plugin install business-problem-toolkit@business-problem-toolkit
```

The same from a shell:

```
claude plugin marketplace add drv3nkman/business-problem-toolkit
claude plugin install business-problem-toolkit@business-problem-toolkit
```

The repository is its own marketplace, named `business-problem-toolkit`, with this one plugin in it. Skills are namespaced by the plugin name, for example `business-problem-toolkit:define-problem`.

To update to a newer release: `/plugin marketplace update business-problem-toolkit`, then `/reload-plugins`.

The skills read their shared files (`references/`, `templates/`) from the installed plugin folder, which is outside your project, so Claude Code asks for permission to read them. Allow it: if you refuse, or in headless `claude -p` runs that cannot ask, the reads are refused and the skill works without its reference files (and says so). To avoid the prompt, add a Read allow rule for the install folder to your settings, for example in `~/.claude/settings.json`:

```json
{ "permissions": { "allow": ["Read(~/.claude/plugins/cache/business-problem-toolkit/**)"] } }
```

(`~/.claude` is your Claude Code config folder; use your own if you set `CLAUDE_CONFIG_DIR`.) An allow rule of this form was checked in a headless run, where it let the reads through. Whether an interactive session asks once per session or once per file, and whether its "don't ask again" option covers the whole folder, has not been tested.

### Cowork (and claude.ai)

In claude.ai go to **Customize > Plugins > Add > Add marketplace** and enter `drv3nkman/business-problem-toolkit`, then install **Business Problem Toolkit** from it. Plugins added there are available in Cowork too.

If you can't add a marketplace, upload the plugin instead: download `business-problem-toolkit-<version>.zip` from the repository's [Releases](https://github.com/drv3nkman/business-problem-toolkit/releases) page and upload it under **Customize > Plugins > Add > Upload plugin**.

## Starting points

Describe your situation and `define-problem` picks a chain. If the start is unclear, it asks one multiple-choice question. If you name a single step ("critique this statement", "reframe this request"), that skill runs directly. A single feature request on its own ("Sales wants an accounting-software sync built.") is one step: reframe-request runs directly, not chain C.

| Start | Example prompt | What runs |
|---|---|---|
| A. Find new problems | "Something's off with retention and I have a pile of notes and tickets." | strategic-context (full) → problem-discovery (sweep or elicit) → [reframe-request on the request list the sweep found] → problem-evidence → viability-constraints (screen) → opportunity-backlog (view) → opportunity-sizing (quick) → problem-focus → [opportunity-assessment for a new product or market bet] → Define chain → [customer-letter if more than one card was framed, or asked for] → team-objectives |
| B. Choose from known candidates | "Here's our list of problems — which should we pursue?" | strategic-context (full) → opportunity-backlog (load or import) → problem-evidence → viability-constraints (screen) → opportunity-sizing (quick) → problem-focus → … as A |
| C. Handed a feature, request or roadmap | "We have a pile of feature requests from sales and support — help me turn them into problems and take it all the way through to framing." | reframe-request → problem-evidence → Define chain |
| D. Assigned problem (team mode) | "Our team was given the objective 'reduce cost to serve per order'." | strategic-context (light) → Define chain → [customer-letter if more than one card was framed, or asked for] |
| E. Review an existing statement | "Review this problem statement: Reduce the time new customers wait for a first reply to a support request." | problem-review |

"Define chain" means problem-statement → success-measures → viability-constraints (full) → problem-review, run once per card.

Steps in square brackets are optional: the router offers them with their condition and runs them only on Confirm (or, under Keep going, when the condition is plainly met). Chains A and B end with a team assignment; C and D end with a reviewed statement (and, if asked, a customer letter).

To resume, open the same project folder and say "pick up where we left off". The router reads the manifest and carries on from the recorded next step. If you decline to create a workspace, the chain runs **chat-only**: nothing is written, and every reply starts with `> **Chat-only mode:** nothing is being saved.`

## Workspace layout

`problem-workspace` creates this in your project folder. The plugin never writes into its own install folder.

```
problem-work/
  README.md                     how the folder works
  <initiative-slug>/
    workspace.md                manifest: stage, artifact index, decision log, next suggested step
    context.md                  strategic context
    _templates/                 copies of the plugin templates (skills fill artifacts from here)
    inputs/                     your raw material: notes, exports, request lists, strategy docs
    discovery/sweep-<date>.md   discovery record: inputs read, who's missing, lenses, clusters, stop reason
    cards/P-001-<slug>.md       one card per candidate problem
    backlog.md                  the opportunity backlog
    sizing/                     quick-<date>.md comparisons and deep sizing briefs
    assessments/                opportunity assessments
    statements/P-001.md         problem statement, success measures and constraints
    statements/P-001-letter.md  customer letter
    objectives/<period>.md      team objectives
```

No file is deleted, and no saved artifact is overwritten. A revision of a write-once file (such as `context.md`, a sizing brief or an assessment) is saved as `-v2`, `-v3` and so on. Statements, their `-v2` redrafts and card bodies are only ever appended to (a card's front-matter and a `_Pending:` placeholder line are the only parts updated in place). The two living files, `workspace.md` and `backlog.md`, are updated in place; their decision log and focus decisions are append-only.

## Provenance

The method draws on Marty Cagan's writing on product discovery and problem framing, condensed in `references/` with citations to `references/sources.md`. It is not Cagan's own tool, and Cagan publishes no problem-statement template. Every template here is a **derived template** and says so. Methods from outside Cagan are labelled **(non-Cagan)** where they are used: most of the sizing, the evidence ladder, ODI, Cost of Delay, the switch-interview and job-map discovery lenses, and the Mom Test style prompts. The discovery stopping rules and timebox are heuristics, not sourced rules.

## Data

Everything the plugin writes stays in the `problem-work/` folder in your project. The plugin has no connectors and sends nothing anywhere.

## License

MIT. See [LICENSE](LICENSE).
