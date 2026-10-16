# problem-work

This folder holds your problem-definition work. Each sub-folder is one initiative: a set of candidate problems, the evidence behind them, and the problems you chose to frame. Open `workspace.md` inside an initiative folder first. It lists every artifact, keeps a dated log of decisions, and names the next suggested step.

## What is in an initiative folder

```
problem-work/
  README.md                      this file
  <initiative-slug>/
    workspace.md                 the manifest: artifact index, decision log, next step
    context.md                   strategic context: vision, objectives, focus areas, gaps
    backlog.md                   the list of candidate problems, one row per card
    inputs/                      raw material you gave us (never changed)
    discovery/                   discovery sweep records: what was read, who is missing, why we stopped
    cards/                       one card per candidate problem: P-001-<slug>.md
    sizing/                      quick comparisons and deep sizing briefs
    assessments/                 opportunity assessments (leader mode)
    statements/                  one problem statement per framed problem, plus customer letters
    objectives/                  team objectives, one file per period
    _templates/                  the shapes every file above is written from (copied from the plugin)
```

`context.md` and `backlog.md` appear once the skill that makes them has run. A fresh workspace is the folders and `workspace.md`.

## How files are treated

Every file belongs to one of three groups. The group decides what may change.

- **Never edited after they are written.** `context.md`, everything in `discovery/`, `sizing/`, `assessments/`, `objectives/` and `inputs/`, and customer letters in `statements/` (a statement's `-v2` redraft is not in this group). To revise one, a skill writes a new copy next to it with `-v2` (then `-v3`, and so on) and adds a line to the decision log. The old file stays as it was.
- **Only added to.** Problem cards and the problem statements in `statements/`, redrafts (`-v2`) included. Their front-matter (status, dates, links) may be updated. Every line already in the body stays, in order. The only lines that may be replaced are the "pending" placeholder lines in a statement, once the skill they name has run.
- **Kept up to date.** `workspace.md` and `backlog.md` change as work progresses. Two parts are still only added to: the `## Decision log` section of `workspace.md` and the `## Focus decisions` section of `backlog.md`.

Files are never deleted. If two runs land on the same day, the second gets `-v2` rather than replacing the first.

## IDs

Problem IDs look like `P-001`: `P-`, then three digits. An ID belongs to one problem for good. IDs are never reused, even when a card is merged into another or set aside as not-now. The next new card takes the highest ID ever used plus one, so gaps in the numbering are normal.

## The templates

`_templates/` is a copy of the plugin's templates, made when the workspace was created. Skills start new files from these copies. Edit a copy if you want your own wording or sections to carry through to later files. The plugin's own originals are read-only and are replaced whenever the plugin updates.

Every template except this README carries the line *Derived template — Cagan publishes no problem-statement template.* Marty Cagan publishes question sets and criteria, not a problem-statement format, so the shapes here are derived from his guidance. Methods that do not come from Cagan, such as sizing and the evidence ladder, are labelled non-Cagan.

## Rules of thumb

- Open `workspace.md` to see where things stand and what to do next.
- Put your own material in `inputs/`. Skills read it and never change it.
- A decision is a log line, not a rewrite: add it to `## Decision log` and leave earlier lines alone.
- If a card and the backlog disagree, ask for a repair. It reconciles them without overwriting anything.
