# Playwright Dashboard

Test results dashboard for the Playwright test suite.
Hosted on GitHub Pages — updated automatically after every CI run.

## How it works

After each run in the test repository, `dashboard/scripts/process-report.js` clones
this repo, appends the new run to `data/manifest.json`, and pushes the commit.
That push triggers the GitHub Pages deploy workflow and the dashboard is live within ~30s.

## Files

```
playwright-dashboard/
├── index.html            ← the dashboard SPA (charts, table, filters)
├── data/
│   ├── manifest.json     ← run history — updated automatically by CI
│   └── runs/             ← individual JSON snapshots, one per run
└── .github/
    └── workflows/
        └── dashboard.yml ← deploys this repo to GitHub Pages on every push
```

## Setup (one-time)

1. Enable GitHub Pages:
   **Settings → Pages → Source: GitHub Actions → Save**

2. In your **test repository**, add two secrets:
   - `DASHBOARD_REPO` = `https://github.com/YOUR-ORG/PlaywrightDashboard`
   - `DASHBOARD_PAT`  = a GitHub PAT with `repo` scope

## Dashboard URL

`https://github.com/TriffC/PlaywrightDashboard`