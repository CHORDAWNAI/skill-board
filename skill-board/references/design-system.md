# Design system

Overall feel: a pale lavender-grey frosted glass, generous corner radii, plenty of white space and a clear hierarchy. Lavender is an accent only, never a large fill.

## Color (CSS variables)
| Variable | Value | Use |
|---|---|---|
| `--ink` | `#1d1d22` | Titles, body text, selected buttons |
| `--ink-2` | `#4a4b55` | Secondary text |
| `--muted` | `#8b8d98` | Captions, count units |
| `--line` | `rgba(30,30,50,.07)` | Cell dividers |
| `--lav-50` / `--lav-100` | `#f6f4fd` / `#efecfb` | Tag backgrounds, hover backgrounds |
| `--lav-200` / `--lav-300` | `#e2dcf7` / `#cfc6f1` | Skill dots, emphasis |
| `--panel` | `rgba(255,255,255,.78)` | Column panels, search box, count pills |

The page background layers two very faint radial gradients (lavender at top left, blue-grey at bottom right) over a `#ecedf2 → #e6e8ee` linear gradient.

## Shape and depth
- Outer frame `.app`: 34px radius, translucent white, `backdrop-filter: blur(24px)`, shadow `0 30px 80px rgba(60,60,90,.10)`.
- Board base `.board`: 28px radius. Column panels `.panel`: 22px radius with a very light shadow.
- Detail panel `aside`: 30px radius, slides in from the right. Its section cards `.sec`: 20px radius.
- Buttons, tags and counts are all pills (`border-radius: 999px`).

## Type
- Font variable `--font`: `Inter` for Latin text and numbers. Chinese text uses the Song-style serif `Noto Serif SC`, falling back to `Songti SC`, `STSong` and `SimSun`.
- To change fonts, edit `--font` only.
- Sizes: main title 30px / 600, column names 14px / 600, stage names 13.5px / 500, skill names 12.5px / 500, captions 11.5–13px.
- Stage numbers use tabular figures in `#b3b5bf`.

## Safe to adjust
- **Accent color:** change only the four `--lav-*` variables. Keep the light-to-dark steps and avoid high saturation.
- **Column width and row height:** columns are at least 176px wide; cells are at least 52px tall. With many columns, prefer horizontal scrolling to narrower columns.
- **Logo:** replace the SVG at the top left with your own mark, about 22px tall.

## Best left alone
- Do not fill empty cells with color or placeholder text.
- Do not spread lavender across the column panels or the whole page; it gets heavy.
- Do not remove the frosted glass and white space to fit in more. If there are too many skills, split stages or groups instead.

## Using it in images
Capture at a 1440px viewport. The board scales well into a 1080×1440 (3:4) portrait image. When sharing publicly, keep a "Fictional example" note in the sample data.
