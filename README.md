# NETFLIX — Swiss Editorial Edition

A Netflix streaming redesign experiment built on the **International Typographic Style (Swiss Style)** — extreme grid alignment, high-contrast Helvetica typography, horizontal dividers, and minimal photography.

Single-page static site: `index.html` (HTML + Tailwind CDN + vanilla JS, no build step), with the title catalog stored as editable JSON.

## Features

- 110-title catalog scraped from Netflix-official top-10 charts, cross-country JustWatch popularity charts, and Wikipedia Netflix-original lists — ranked by popularity
- **Home**: Today's Top Picks (10) + Top Series (10) + Top Cinema (10) carousels
- **Shows / Movies**: a Top 10 row plus one genre-wise carousel per genre (Action / Drama / Comedy / Crime / Anime) in the same format
- Live **search** (title / cast / genre) and quick-genre filters across every page
- Editorial **hero section** with giant typographic title, quote badge, and technical spec grid
- **Detail modal** with metadata, content advisory, credits, and episode listings when archived
- **Tabs**: Home, Shows, Movies, Games (placeholder), New & Top (featured), My List (personal archive)
- Simulated playback overlay with animated equalizer and transport controls

## Run locally

The catalog is loaded with `fetch()`, so the page must be served over HTTP:

```bash
python3 -m http.server 8000
# → http://localhost:8000
```

Opening `index.html` directly from disk will show a "CATALOG FEED OFFLINE" notice.

## Catalog JSON database

The title data lives in two files, so adding titles later is a pure JSON edit:

| File | Contents |
|---|---|
| `data/movies.json` | Feature films, ranked by popularity |
| `data/series.json` | TV series, ranked by popularity |

Both files are arrays of entry objects, merged and sorted by `rank` on load:

```json
{
  "id": "KP-001",                  // unique reference code (prefix + zero-padded rank)
  "code": "01",                    // display index shown on cards
  "rank": 1,                       // popularity position (1 = most popular)
  "title": "KPop Demon Hunters",
  "type": "movies",                // "movies" or "shows"
  "genre": "anime",                // action | drama | comedy | crime | anime
  "genreLabel": "ANIME / ANIMATION",
  "year": "2025",
  "seasons": "325.1M VIEWS",       // seasons count for series, views for films
  "rating": "U/A 13+",
  "subheading": "ALL-TIME TOP 10 FILM",
  "description": "Plot synopsis…",
  "cast": "…",
  "genresFull": "…", "characteristics": "…", "advisory": "…",
  "duration": "FEATURE FILM",
  "progressPercent": "0%", "progressText": "—",
  "isFeatured": false,             // true → also listed under New & Top
  "awards": false,                 // true → listed in the home "Award Winning Titles" row
  "seasons_data": { "1": [ … ] },  // series only: per-season episodes (num/title/desc/duration)
  "country": "US",                 // series only: production country (US row on home)
  "episodes": []                    // optional episode list for series
}
```

To add a title, append an object to the matching file (any unused `rank` slots sorts it naturally) and reload.

## Home page rows

1. **Continue Watching for {user}** — simulated sessions defined in `CONTINUE_WATCHING` in `index.html` (id, %, resume label), rendered with progress bars
2. **Your List** — the saved titles (My List)
3. **Your Next Watch** — titles sharing a genre with the saved list, round-robin across saved genres; falls back to random picks when the list is empty
4. **US TV Dramas and Sitcoms** — series with `country: "US"`
5. **Old Gems** — titles released 2015 or earlier
6. **Award Winning Titles** — entries flagged `"awards": true`

## Design system

| Token | Value |
|---|---|
| Palette | Cream `#EAE8E1` · Charcoal `#111111` · Swiss Red `#E50914` |
| Typeface | Helvetica Neue / Helvetica / Arial |
| Grid | 12-column rigid grid with stark 1–2px black dividers |

© 2026 — Redesign archive, designed in the style of Emform & Swiss graphic posters.
