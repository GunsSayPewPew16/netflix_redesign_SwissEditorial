# NETFLIX — Swiss Editorial Edition

A Netflix streaming redesign experiment built on the **International Typographic Style (Swiss Style)** — extreme grid alignment, high-contrast Helvetica typography, horizontal dividers, and minimal photography.

Single-file static site: `index.html` (HTML + Tailwind CDN + vanilla JS, no build step).

## Features

- Editorial **hero section** with giant typographic title, quote badge, and technical spec grid
- **Catalog rails**: Top Picks, Continue Watching, Recommended — filterable by Drama / Action / Anime / Thriller
- **Tabs**: Home, Shows, Movies, My List (personal archive)
- **Detail modal** with metadata, resume progress, content advisory, credits, and episode listings with a season switcher
- **Simulated playback overlay** with animated equalizer and transport controls
- Live clock, paper-grain texture, custom Swiss scrollbar, and full My List state management

## Run locally

No dependencies — just open `index.html` in a browser, or serve it:

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

## Design system

| Token | Value |
|---|---|
| Palette | Cream `#EAE8E1` · Charcoal `#111111` · Swiss Red `#E50914` |
| Typeface | Helvetica Neue / Helvetica / Arial |
| Grid | 12-column rigid grid with stark 1–2px black dividers |

© 2026 — Redesign archive, designed in the style of Emform & Swiss graphic posters.
