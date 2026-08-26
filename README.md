# Malaysia National Days

Two standalone, single-file HTML pages introducing Malaysia's two key national
celebrations. Built with [Tailwind CSS](https://tailwindcss.com) via CDN — no
build step, no dependencies, just open in a browser.

## Structure

```
.
├── malaysia-independence-day/
│   └── index.html   # Hari Merdeka — 31 August 1957
└── malaysia-day/
    └── index.html    # Hari Malaysia — 16 September 1963
```

## Pages

### `malaysia-independence-day/index.html`
Explains **Hari Merdeka**, the day the Federation of Malaya gained independence
from British rule on 31 August 1957. Covers the historic "Merdeka!" chant led by
Tunku Abdul Rahman, how it differs from Malaysia Day, and how it's celebrated.

### `malaysia-day/index.html`
Explains **Hari Malaysia**, the day Malaya, Sabah, Sarawak, and Singapore united
to form Malaysia on 16 September 1963. Covers the formation history and why it
only became a nationwide public holiday in 2010.

Each page cross-links to the other via a button at the bottom.

## Usage

No install required — just open either `index.html` file directly in a browser:

```
malaysia-independence-day/index.html
malaysia-day/index.html
```

Tailwind is loaded via the CDN `<script src="https://cdn.tailwindcss.com">`,
so an internet connection is needed for styles to load.

## GitHub Actions: `.github/workflows/deploy-homepage.yml`

Deploys whichever page is **nearer in date** as the GitHub Pages homepage,
demonstrating several trigger/condition styles:

| Trigger | Condition type | Behavior |
|---|---|---|
| `schedule` (daily cron) | time-based | Re-picks the nearer holiday every day |
| `push` to `main` | path-filtered | Rebuilds when page content changes |
| `workflow_dispatch` | manual input (`auto`/`merdeka`/`malaysia-day`) | Lets you force a homepage |

**Jobs:**
1. `determine-target` — computes days-until for each holiday (or honors the
   manual override) and outputs the winner.
2. `build-merdeka` / `build-malaysia-day` — only one runs, gated by
   `if: needs.determine-target.outputs.target == '...'`.
3. `deploy` — publishes to GitHub Pages once the selected build job succeeds.
4. `notify-success` — runs only `if: success()`.
5. `notify-failure` — runs only `if: failure()`, reporting every job's result;
   this is the "stop and run a failed job" safety net.
