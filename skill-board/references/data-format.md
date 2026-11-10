# BOARD data format

The template has one `BOARD` object to edit. Everything else is rendering logic.

| Field | Required | Description |
|---|---|---|
| `workspace` | Yes | Workspace name at the top left |
| `title` | Yes | Main title, `Skill Board` by default |
| `subtitle` | No | One line under the title |
| `repo` | No | Prefix for the location shown in the detail panel, such as a repository name. If empty, only `path` is shown |
| `footnote` | No | Small note at the bottom right. For public examples, use something like "Fictional example" |
| `labels` | Yes | Every fixed piece of interface text. Translate it as a whole into any language |
| `groups` | No | Filter tabs at the top. Each group is `{id, name, columns:[columnId…]}`. Remove the field to filter by single column instead |
| `columns` | Yes | Columns: `{id, name, badge}`. `badge` is a small tag in the column header (an abbreviation, owner or system name) and can be omitted |
| `stages` | Yes | Rows, in order: `{id, name}`. The numbers 01, 02… are generated automatically |
| `skills` | Yes | See below |
| `notes` | No | Cell notes: `{"columnId|stageId": "note"}`, for special cases in the workflow |

## Skill entries

| Field | Required | Description |
|---|---|---|
| `id` | Yes | Unique identifier, also the default display name |
| `name` | No | Display name. Used instead of `id` when present |
| `col` | Yes | The column `id`. Use `"others"` for skills shared across columns |
| `stage` | Yes | A stage `id`, or an array of stage ids |
| `desc` | Recommended | What it does, in one or two sentences |
| `prompts` | Recommended | Array of example prompts. The first one is used by the "Copy prompt" button |
| `files` | No | Files the skill contains |
| `path` | No | Path inside the repository |
| `versions` | No | `[[date, note], …]` in date order |

When a field is empty, its section in the detail panel is hidden, so fill in only what is useful.

## Minimal example

```js
const BOARD = {
  workspace: "My Workspace", title: "Skill Board", subtitle: "Skills by area and stage",
  repo: "", footnote: "",
  labels: { all:"All", search:"Find a skill", others:"Others", othersEmpty:"Cross-team skills will appear here",
            skills:"skills", columns:"areas", stages:"stages",
            what:"What it does", prompts:"Example prompts", files:"Files", location:"Location", versions:"Versions",
            copy:"Copy prompt", copied:"Copied", copyFail:"Copy failed. Please select it manually." },
  columns: [ {id:"a",name:"Product"}, {id:"b",name:"Marketing"} ],
  stages:  [ {id:"plan",name:"Plan"}, {id:"do",name:"Execute"}, {id:"review",name:"Review"} ],
  skills:  [ {id:"PRD writer",col:"a",stage:"plan",desc:"Turns discussions into a product requirements doc.",prompts:["Write a PRD from these meeting notes"]} ],
  notes: {}
};
```
