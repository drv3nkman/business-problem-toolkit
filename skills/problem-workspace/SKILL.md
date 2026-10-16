---
name: problem-workspace
description: Use when creating, finding, importing documents (interviews, notes, exports) into, checking the status of or progress on ("where are we on this initiative?"), or repairing a problem-work folder (workspace.md manifest, cards, backlog). Not for capturing vision, objectives or strategy — use strategic-context.
---

# problem-workspace

Owns the working folder every other problem-definition skill reads and writes: `problem-work/<initiative-slug>/`. Its **Locate** procedure is Step 1 of every other skill.

## When to use

- Starting an initiative: no `problem-work/` folder or manifest yet (**Create**).
- Another skill needs the workspace: they all begin with **Locate**.
- The user hands over documents to keep with the initiative (**Import**).
- The user asks where things stand ("where are we on the order desk work?", "what's the status?"): stage and how many problems are in each status (**Status**). Use this skill even when the request never says "workspace"; answering from a quick look at the files skips the counts and the next step.
- Folders or files are missing, the backlog and the cards disagree, or someone hand-edited a card (**Repair**).

## When not to use

- Capturing vision, objectives, scorecard or strategy: use strategic-context.
- Finding problems in notes or data: use problem-discovery. Import only copies files; it does not read them.
- Changing what a card says or what status a problem should have. The skill that owns that decision does it.

## Inputs

- **Create:** an initiative name (required) and, optionally, a location and a mode (`team`, `leader` or `mixed`). Do not stop to ask for what the request already gives. If mode is not given, use `team` and say so in the report.
- **Import:** the files or folders to copy in.
- **Locate, Status, Repair:** nothing; the workspace is found from the current folder.

## Steps

Run every shell command as one simple command per call: no `&&`, `;`, pipes or loops, and no `cp -p`. List several folders or use a glob instead (`mkdir -p a b c`, `cp src/* dest/`). If the shell is unavailable, use Read and Write.

### 1. Locate

1. Look for `workspace.md` with Glob, ignoring `_templates/` copies. Search in this order and stop at the first level that has any: the current folder; one level down (`*/workspace.md` and `problem-work/*/workspace.md`). Never search above the project folder.
2. One match: that is the workspace. Several: if the request names an initiative, use it; otherwise list them and ask which.
3. No match: what happens next depends on what the request brought. **Pasted text alone** (a statement, a request, an objective or a list typed into the chat, and nothing else): go **chat-only** at once, without an offer, and say in one line that a workspace can be created on request. **Files, a folder, card IDs or an ask to save:** say no workspace was found and offer to create one (ask for the initiative name). A decline is chat-only. Chat-only means: the first output line is `> **Chat-only mode:** nothing is being saved.`, the same content is given in the conversation, and no file or folder is written anywhere. It lasts until the user asks to save or to create a workspace: then run Create and carry on in workspace mode from that reply, writing only what that reply and later ones produce (earlier chat-only output is not written back unless the user asks).
4. Hand back the workspace path, the manifest's `stage` and `mode`, and whether `_templates/` exists.

When the request is Create, Locate only checks that this initiative does not already have a folder. If it does, report that workspace and stop. Other initiatives beside it do not block a new one.

### Create

1. **Location.** Default: `problem-work/` at the root of the user's project folder (`${CLAUDE_PROJECT_DIR}` in Claude Code, the connected folder in Cowork), or a folder the user names. Never the plugin's install directory. The initiative folder is `<location>/<slug>/`, where `<slug>` is the initiative name in lowercase, hyphen-separated ASCII.
2. **Folders.** One command: `mkdir -p` for `<slug>/inputs`, `discovery`, `cards`, `sizing`, `assessments`, `statements`, `objectives` and `_templates`.
3. **Templates.** Copy every file from `${CLAUDE_PLUGIN_ROOT}/templates/` into `<slug>/_templates/` (one `cp` with a glob), so all twelve are there. Later skills start new files from these copies.
4. **README.** If `<location>/README.md` does not exist, copy `_templates/workspace-readme.md` to it unchanged. If it exists, leave it.
5. **Manifest.** Write `<slug>/workspace.md` from `_templates/workspace.md`: set `initiative`, `created` and `updated` (today, YYYY-MM-DD), `mode`, `stage: foundation` and `checkpoints_since_decision: 0`; fill the title; list `- [Inputs](inputs/)` under `## Artifacts`; set the `**Next suggested step:**` line to `strategic-context`; keep every other line. Creating a workspace is not a decision, so the decision log gets no line.
6. If the request names documents to bring in, run **Import** now.
7. Report what was created (a short tree), the mode used, and any file not imported.

### Import

1. Copy, never move: the originals stay where they are. Copy every file whatever its type (Markdown, CSV, images, PDFs); never convert it.
2. `inputs/` is write-once, so never overwrite. First Glob `<slug>/inputs/` (all depths) and compare names with what is being imported.
   - No collision: copy with `cp -n <file> <slug>/inputs/` (or `cp -rn <folder>/. <slug>/inputs/` for a folder with no collisions). `-n` refuses to replace anything, so a missed collision still cannot overwrite.
   - Collision: do not copy it over the old file. Copy it as `<name>-v2.<ext>` (`-v3` if that exists) with one `cp -n <file> <slug>/inputs/<name>-v2.<ext>`, and append one line to `## Decision log` in `workspace.md`: `- YYYY-MM-DD — revision — inputs/<name> — re-imported as <name>-v2.<ext>; original kept`. Also set `updated`.
   - Report each collision (old name, new name). If a copy was skipped by `-n`, say so.
3. Do not open, summarise or judge the files; reading them is the job of strategic-context and problem-discovery. List each file with its type and say they are copied, not read.
4. Report anything that could not be copied and why.

### Status

Read-only: write nothing. Read `workspace.md` (stage, mode, updated, the last three decision-log lines) and the front-matter of every `cards/P-*.md`.

1. State the initiative, stage and last-updated date.
2. Give the count for all seven statuses, zeros included, then the total: `candidate N · shortlisted N · chosen N · not-now N · assessed N · framed N · assigned N`. Name the IDs under each non-zero status. Count from the cards, not from the backlog or the log.
3. List what exists (context, sweeps, backlog, statements, objectives) in one line.
4. Mention a mismatch, a card that will not parse, or a missing folder in one line each and point to Repair. Do not fix it and do not comment on the substance of the problems.

### Repair

Cards are the source of truth for status. Never overwrite or delete; only add what is missing and bring backlog rows into line.

1. **Folders and templates.** `mkdir -p` any of the eight folders that are missing. Copy missing templates from `${CLAUDE_PLUGIN_ROOT}/templates/` into `<slug>/_templates/` with `cp -n` and a glob (`-n` never replaces an existing copy). If the parent folder is named `problem-work` and has no `README.md`, copy `_templates/workspace-readme.md` there.
2. **Manifest.** Missing: write one as in Create (initiative from the folder name, stage from the artifacts present, empty decision log) and say earlier decisions cannot be recovered. Present but missing front-matter keys: add only the missing keys. Present but unparseable: report the parse error and leave it.
3. **Check each card.** Read its front-matter and confirm it parses as YAML (quotes closed, indentation sound), `id` matches the file name, and `status` is one of the seven values. A card that fails is **invalid**: report the file and the exact problem ("line 3: unclosed quote", "status 'in progress' is not a status") and leave the file byte-identical. Do not guess its status or touch its backlog row.
4. **Reconcile `backlog.md`** (if it exists; Repair does not create it). For each valid card there must be exactly one row with the same ID and the card's status. Change only the Status cell of a wrong row. Add a missing row using the table's columns, `—` for blanks. A row with no card, or a duplicate row, is reported, not removed. Never touch `## Focus decisions`.
5. Report three lists: fixed, needs you (each invalid card with its error and what to correct by hand; rows without cards), left as they were.

## Output

- **Create:** the folder tree (Create, above) plus `_templates/`, `README.md` and `workspace.md`; imported files in `inputs/`.
- **Import:** the copied files in `inputs/` (new names for collisions) and a `revision` line in the decision log for each.
- **Status:** a chat report only.
- **Repair:** added folders and files, edited Status cells in `backlog.md`, and the three-list report.
- Every response, including chat-only, ends with a line `**Next suggested step:** <skill or action>`, never "Next step" and never a closing question. After Create or Import: strategic-context (or problem-discovery if the user wants to skip strategy; it will flag the missing context). After Status: the manifest's own next-step line, or from `stage` (foundation: strategic-context; identify: problem-discovery; choose: problem-focus; define: problem-statement; handoff: team-objectives). When Repair left an invalid card: fix that card by hand, then run problem-workspace Repair again.

## References

None. This skill uses templates only: read `${CLAUDE_PLUGIN_ROOT}/templates/` (listed in Create step 3) and keep the workspace copies in `_templates/`.

## Guardrails

- Never write to the plugin's install directory. Plugin content is read-only and replaced on update; every file this skill makes lands in the user's project folder.
- Never overwrite or delete a file. A name collision gets `-v2` plus a decision-log `revision` line. Only the Status cells of backlog rows, missing manifest keys, `updated` and new decision-log lines ever change in an existing file.
- An invalid card or manifest is reported with its parse error, never repaired in place, never guessed at.
- Flag, don't invent: no decision-log lines, statuses, counts or file contents that no file supports. Report counts as read from the cards.
- IDs are stable and never reused: `P-NNN`, next ID is the highest ever used plus one; gaps (a merged card) are normal.
- Chat-only means no file anywhere, and starts with the notice line.
- Never name "the most important problem"; Status reports counts, not rankings.
