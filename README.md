# Special Teams Tools — public site

This folder is the **public, hostable** version of the punt tools. It is a
separate git repo on purpose: it contains **only** the app shell (no student
data), so it is safe to publish on GitHub Pages / Netlify / any static host.

- `index.html` — landing page
- `shield_punt.html` — Shield Punt Designer (data-less)
- `kickoff_coverage.html` — Kickoff Coverage Designer (data-less)
- `roster_editor.html` — Roster Editor (data-less)
- `.nojekyll` — tells GitHub Pages to serve the files as-is

## Do NOT add data files here

Keep `athletes.json`, `assignments.json`, the CSVs, and the source/build files
in the parent project folder — never in this repo. Anything committed here
becomes public. Share data files (`athletes.json` / `assignments.json`) with
coaches privately; they load them with the in-app Import buttons.

## Regenerate these files

From the parent project folder:

```powershell
.\build_html.ps1                     -NoData -Html .\dist\shield_punt.html
.\build_html.ps1 -Formation kickoff  -NoData -Html .\dist\kickoff_coverage.html
.\build_roster_editor.ps1            -NoData -Html .\dist\roster_editor.html
```

## Publish (GitHub Pages)

```bash
# from this dist/ folder
git add -A && git commit -m "Update site"
git push                       # to a PUBLIC GitHub repo
# then: repo Settings → Pages → Deploy from branch → main → / (root)
```

Or drag this folder onto https://app.netlify.com/drop for an instant URL.
