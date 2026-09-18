# Aether Excel Handbook

An interactive Excel formula handbook for Aether staff: formula fundamentals, reading complex formulas, text and number formats, logic, lookups (VLOOKUP → INDEX/MATCH → XLOOKUP), Tables and PivotTables, SUMIFS and dynamic arrays, and error fixing. Includes a paste-in formula formatter, a number-format builder, an XLOOKUP explorer and live mini-spreadsheets.

Everything is in one file — `index.html` — with no build step and no dependencies beyond Google Fonts (it falls back to system fonts offline).

## Hosting

The handbook is a single static file, so any static host works. **Cloudflare Pages** is the chosen route — free, gives a real URL that updates on every push, and can be restricted to Aether staff.

One-off setup:

1. Sign in at [dash.cloudflare.com](https://dash.cloudflare.com) → **Workers & Pages** → **Create** → **Pages** → **Connect to Git**.
2. Authorise GitHub and pick `jrbahou-333/excel_cheatsheet`.
3. Build settings — leave everything empty:
   - Framework preset: **None**
   - Build command: *(blank)*
   - Build output directory: `/`
   - Production branch: `main`
4. **Save and Deploy**. The site appears at `https://<project-name>.pages.dev` within a minute, and redeploys automatically on every push to `main`.

Optional extras:

- **Custom domain** — Pages → Custom domains → add e.g. `excel.aether-uk.com`, then add the CNAME record Cloudflare shows you.
- **Restrict to staff** — Zero Trust → Access → Applications → Add a self-hosted application for the Pages hostname, with a policy allowing emails ending in `@aether-uk.com`. Staff then sign in once to view it.

Note: Bitbucket Cloud has no static-site hosting, and Confluence Cloud strips the JavaScript the interactive parts rely on, so neither can serve this page directly.

## Offline use

`index.html` also works as a plain file — email it, drop it in Teams or a shared drive, and double-click to open. Everything (search, live grids, the formatter) runs locally with no server. Use the **Print** button in the header to save a PDF copy.

## Updating the handbook

1. Edit `index.html`. Content is plain HTML; the data behind the interactive grids and walk-throughs lives in the `SHEETS` and `STEPPERS` objects in the first `<script>` block.
2. Open the file in a browser to check it.
3. Commit and push to `main` — the host redeploys automatically.

Brand colours are CSS variables at the top of the `<style>` block (`--brand`, `--brand-light`, `--navy`). The logo is an inline SVG in the header marked `<!-- LOGO -->`; replace it with the official file if preferred.
