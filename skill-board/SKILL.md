---
name: skill-board
description: Turn a set of AI skills into a clean, visual Skill Board, a single HTML page that maps every skill onto the user's own teams and work stages. Use when someone wants to see, organize, present or share their skills as a workflow map, or asks for a "skill board" or "skill map".
---

# Skill Board: give your skills a home, and yourself a map of your work

This skill provides a ready-made visual template. Columns are teams, business lines or types of work; rows are work stages; each skill sits where it belongs. The page supports filtering and search. Clicking a skill opens a detail panel with what it does, example prompts, files, location and version history.

The user does not need to spend time on layout. Swap in their data and they get a map of their own workflow.

**Rows, columns and language all follow the user's needs.** The Research / Writing / Design columns and six stages in the template are a fictional example, not a structure to copy. The interface can be in English, Chinese or any mix: just replace `labels`. Tell the user this before you build.

## Files
- `assets/board-template.html`: the template, a self-contained single HTML file. Only the `BOARD` data block needs editing.
- `references/data-format.md`: what each field in `BOARD` means and how to fill it in.
- `references/design-system.md`: colors, radii, shadows and type. Read it before changing any styles.

## Workflow

1. **Understand the structure before building.** Confirm with the user, or work out from material they provide:
   - The workspace name (top left) and subtitle.
   - **Columns**: teams, business lines, client types or types of work, divided the user's way. Usually 3 to 7.
   - **Rows**: work stages in their real order. Usually 4 to 12.
   - **Skills**: which column and which stage (or stages) each skill belongs to, plus a one-line description.
   If the user points you to a folder or repository of skills, read the `name` and `description` in each `SKILL.md` to infer placement. List any you cannot place and ask the user; do not force them into a cell.

2. **Copy the template and replace only the data.** Copy `assets/board-template.html` to a new file and edit only the `BOARD` object between the `BOARD DATA` markers. Leave the template logic and CSS untouched unless the user asks for style changes.

3. **Follow these content rules:**
   - Leave cells with no skill empty. The gaps are information in themselves: they show where to add next. Do not add status labels such as "planned", "testing" or "verified".
   - If a skill is used in several stages, make `stage` an array; the skill will appear in each of those cells. For a skill shared across columns, set `col` to `"others"`.
   - Keep each skill's `id` unique. Use `name` for a different display name.
   - Follow the user's language for the title, subtitle, `labels`, column names, stage names and skill names.
   - **Before anything is shared publicly** (screenshots in a post, a public repository), replace real business details with a fictional example: no clients, cases, internal paths or colleagues' names. Keep a footnote such as `"Fictional example"`.

4. **Check.** Open the file in a browser and confirm:
   - The counts at the top right are correct.
   - Every skill is in the right cell.
   - Clicking a skill opens the detail panel.
   - Filtering and search work.
   - Long names wrap cleanly.
   - With many columns, the board scrolls horizontally.
   If you can take screenshots, capture the full page and review it.

5. **Deliver.** The result is a single `.html` file. It opens with a double-click, can be hosted as a web page (GitHub Pages or any static host), or captured as an image for a post.

## License
Copyright CHORDAWN AI (半弦 AI). Personal use only, no commercial use (see LICENSE in the repository). Boards that users generate for their own work may be used freely in that work.

## Maintenance
- To add or update a skill, edit only the `skills` array and append a `[date, note]` row to its `versions` to keep the history.
- If the skills live in a Git repository, set `path` to the path inside the repository and `repo` to the repository name. The board handles navigation; the repository holds the files and versions.
