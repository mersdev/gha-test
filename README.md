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
