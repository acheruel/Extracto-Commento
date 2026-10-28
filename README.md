# Extracto Commento — PDF comments to Excel

Version 0.8.5 · October 28, 2026 · [Version française](README_FR.md)

Extract the comments from your PDFs, review them in a table and download an Excel workbook. **Everything runs in your browser: no document is ever uploaded.**

**[Open Extracto Commento](https://acheruel.github.io/Extracto-Commento/)** — or click **Try an example** to test it with a synthetic PDF.

## Features

- **One PDF** or **Multiple PDFs → one Excel** (select or drag and drop, files can be added during analysis).
- Supported annotations: notes, text boxes, highlights, strikeouts and lines. Highlights without a note and empty lines are skipped; text under highlights and strikeouts is estimated from the PDF geometry.
- Review table with search, author / type / page / file filters; the export always contains every retained comment.
- Excel columns: No, (File), Page, Author, Date, Comment, plus a *Files* sheet in batch mode.
- Partial results (unreadable pages or files) must be acknowledged before export and are flagged in the workbook.
- French / English interface (FR/EN toggle in the header).
- Target: up to 300 MB and 500 pages per PDF on desktop — see [VALIDATION.md](VALIDATION.md).

**Limitations:** flattened annotations cannot be recovered, password-protected PDFs must be unlocked first, and editor-specific extras (Bluebeam, Foxit, Adobe measurements…) are not guaranteed. Always check results against the original PDF.

## Run locally

Double-click **Lancer.cmd** (Windows, requires Node.js) and open <http://127.0.0.1:8765>, or serve the folder with any static server: `node server.mjs --open`. Do not open `index.html` directly — ES modules and workers require HTTP.

## Tests

```bash
npm install
npm test            # browser smoke tests (Chrome by default)
npm run test:stress # adds a 300 MB / 500-page synthetic PDF
```

Use `TEST_BROWSER=msedge` for Edge or `CHROME_PATH=/path/to/chrome` for a specific Chromium binary.

## Files

`index.html` / `styles.css` (interface) · `app.js` (state, filters, translations) · `extract.js` (PDF.js reading) · `format.js` (labels, dates) · `export-worker.js` (Excel generation) · `vendor/` (PDF.js 5.6.205 Apache-2.0, ExcelJS 4.4.0 MIT — see [THIRD_PARTY.md](THIRD_PARTY.md)).

Author: Anthony Chéruel. Published with GitHub Pages from the `main` branch.
