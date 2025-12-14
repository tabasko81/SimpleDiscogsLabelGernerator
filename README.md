# Simple Discogs Label Generator

`SimpleDiscogsLabelGernerator.html` is a single-file, standalone web app that runs locally in your browser. You paste your Discogs personal access token, load your collection, and generate clean, printable HTML labels for releases.
The goal here is to keep the workflow lightweight and practical for collectors, sellers/resellers, and enthusiasts.

> **Inspired by:** This project was inspired by [DiscogsRecordLabelGenerator](https://github.com/LahmacunLove/DiscogsRecordLabelGenerator) by LahmacunLove. While that project uses Python, audio analysis, and LaTeX to generate labels with waveforms and BPM/key detection, this version focuses on a lightweight, browser-based approach that works entirely client-side.

## What it does

- Loads your Discogs collection (folder `0`, "All")
- Lets you filter and select releases quickly
- Generates printable labels with:
  - Artist, title, year
  - Tracklist with customizable BPM and KEY columns (optional; slower)
  - Label + catalog number (when available)
  - Genres and styles (sub-genres) in the footer (when available)
  - Cover art (from Discogs image URLs)
  - QR codes linking to Discogs release pages
  - Customizable notes field per label
- **Preview customization:**
  - Adjust font size in steps of ±1pt
  - Color picker for Artist(s) and Release text
  - Adjust spacing between labels
  - Individual BPM/KEY column toggle per label (click track table)
  - Individual notes field toggle per label (click cover image)
- Works without installing Python, TeX, or running a server

## Requirements

- A modern browser (Chrome/Chromium, Firefox, Edge, Safari)
- A Discogs personal access token

No other dependencies are required.

## Quick start

1. Open `SimpleDiscogsLabelGernerator.html` in your browser (double click it), or use the [live version](https://tabasko81.github.io/SimpleDiscogsLabelGernerator/).
2. Paste your Discogs token.
3. Click **Verify token + Load collection**.
4. Filter and select releases.
5. Click **Generate labels**.
6. Customize in the preview:
   - Adjust font size, colors, and spacing
   - Click track table to show/hide BPM/KEY columns for that label
   - Click cover image to show/hide notes field for that label
   - Edit BPM/KEY values directly in the table cells
7. Print with **Ctrl+P** or click **Export HTML** to download a labels-only HTML file.

## Main features

### Collection Management
- Load entire Discogs collection or filter by artist/title/year/label
- Quick selection with visual feedback
- Filter supports multiple terms (separated by `;`)

### Label Generation
- Clean, printable label design
- Tracklist with position, title, and duration
- Optional BPM and KEY columns (editable, toggle per label)
- Release metadata (label, catalog number, year, genres, styles)
- Cover art from Discogs
- QR codes for quick access to Discogs release pages
- Custom notes field per label (toggle per label)

### Preview Customization
- **Font size:** Adjust in ±1pt steps (default: 0, range: -10 to +10)
- **Color picker:** Customize Artist(s) and Release text colors
- **Spacing:** Adjust gap between labels in ±1 line steps
- **BPM/KEY columns:** Toggle visibility per label by clicking the track table
- **Notes field:** Toggle visibility per label by clicking the cover image

### Export
- Export to standalone HTML file with all customizations applied
- Print-ready format optimized for standard label sizes

## Filtering and selection

- Click any release row to toggle selection (no checkboxes).
- **Select visible** selects only the currently filtered results.
- The filter supports multiple terms separated by `;` (logical OR).

Example:

- `2001; 2002; Guetta`

Shows releases that match any of those terms across artist/title/year/label.

## Performance and rate limiting

Discogs enforces API rate limits (typically around 60 requests/minute). When generating labels for large collections:

- Increase **Delay between requests (ms)** if you see errors
- Consider disabling **Include tracklist** for a much faster run (it avoids one API call per release)
- For very large collections, prefer **Export HTML** after generating so you can print from the exported file

## CORS and the optional proxy

Discogs API requests from a local HTML file can be blocked by browser CORS rules. If loading fails with “Failed to fetch”:

1. Try again with no proxy first (leave the proxy field empty).
2. If CORS blocks the request, set a proxy prefix (example: `https://corsproxy.io/?`).
3. Increase **Delay between requests** (e.g. 2000–4000ms) when using a proxy.

Important: a CORS proxy can see your traffic, including your token. Only use a proxy you trust.

## Privacy and security notes

- Your token is kept in memory in the page. It is not intentionally stored to disk by the app.
- If you use a CORS proxy, your requests (and token) may be visible to that proxy.
- The exported HTML file contains:

## Discogs terms

You are responsible for using the Discogs API in compliance with Discogs’ developer terms and rate limits.

## License and attribution

Licensed under **Apache License 2.0**. You may use, modify, and redistribute this project (including commercial use), but you must retain the license and notices. In practice, this means your derivative must keep attribution to the original author:

- **Miguel da Silva**

See `LICENSE` and `NOTICE` for details.

## File layout

- `SimpleDiscogsLabelGernerator.html`: the entire application


