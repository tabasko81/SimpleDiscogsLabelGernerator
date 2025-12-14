# Simple Discogs Label Generator

`discogs_labels_standalone.html` is a single-file, standalone web app that runs locally in your browser. You paste your Discogs personal access token, load your collection, and generate clean, printable HTML labels for releases.
The goal here is to keep the workflow lightweight and practical for collectors, sellers/resellers, and enthusiasts.

## What it does

- Loads your Discogs collection (folder `0`, “All”)
- Lets you filter and select releases quickly
- Generates printable labels with:
  - Artist, title, year
  - Tracklist (optional; slower)
  - Label + catalog number (when available)
  - Genres and styles (sub-genres) in the footer (when available)
  - Cover art (from Discogs image URLs)
- Works without installing Python, TeX, or running a server

## Requirements

- A modern browser (Chrome/Chromium, Firefox, Edge, Safari)
- A Discogs personal access token

No other dependencies are required.

## Quick start

1. Open `discogs_labels_standalone.html` in your browser (double click it).
2. Paste your Discogs token.
3. Click **Verify token + Load collection**.
4. Filter and select releases.
5. Click **Generate labels**.
6. Print with **Ctrl+P** or click **Export HTML** to download a labels-only HTML file.

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

- `discogs_labels_standalone.html`: the entire application


