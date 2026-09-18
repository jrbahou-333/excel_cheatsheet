# Aether Excel Handbook

An interactive Excel formula handbook for Aether staff: formula fundamentals, reading complex formulas, text and number formats, logic, lookups (VLOOKUP → INDEX/MATCH → XLOOKUP), Tables and PivotTables, SUMIFS and dynamic arrays, and error fixing. Includes a paste-in formula formatter, a number-format builder, an XLOOKUP explorer and live mini-spreadsheets.

Everything is in one file — `index.html` — with no build step and no dependencies beyond Google Fonts (it falls back to system fonts offline).

## Live site

Hosted free on GitHub Pages: **https://jrbahou-333.github.io/excel_cheatsheet/**

To enable it the first time (one-off, repo admin): **Settings → Pages → Build and deployment → Source: GitHub Actions**. The workflow in `.github/workflows/pages.yml` then publishes `index.html` on every push to `main`, usually within a minute. Share the URL above with the team; no login is needed.

If the handbook must not be public, the alternative is Cloudflare Pages (free): make the repo private, connect it in the Cloudflare dashboard with no build command and `/` as the output directory, and optionally add Cloudflare Access to restrict viewing to `@aether-uk.com` accounts.

## Updating the handbook

1. Edit `index.html` (content is plain HTML; interactive grid data lives in the `SHEETS` and `STEPPERS` objects in the first `<script>` block).
2. Open the file in a browser to check it.
3. Commit and push to `main` — GitHub Pages redeploys automatically.

Brand colours are CSS variables at the top of the `<style>` block (`--brand`, `--brand-light`, `--navy`). The logo is an inline SVG in the header marked `<!-- LOGO -->`; replace it with the official file if preferred.

## Offline use

`index.html` can also be emailed or put on a shared drive and opened by double-clicking. Use the **Print** button in the header to save a PDF copy.
