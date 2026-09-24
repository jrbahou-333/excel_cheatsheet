# Aether Excel Handbook

An interactive Excel formula handbook for Aether staff: formula fundamentals, reading complex formulas, text functions and dates, logic, lookups (VLOOKUP → INDEX/MATCH → XLOOKUP), Tables and PivotTables, SUMIFS and dynamic arrays, and error fixing with Evaluate Formula. Includes a paste-in formula formatter, an XLOOKUP explorer, step-through walk-throughs and live mini-spreadsheets.

Everything is in one file — `index.html` — with no build step and no dependencies beyond Google Fonts (it falls back to system fonts offline). `assets/logo-white.png` is the source of the header logo, which is embedded in the page.

## Repository

Lives in Bitbucket at `aetheruk/aether_excel_handbook` (OGI project), migrated from GitHub with its history intact. The original GitHub repository, `jrbahou-333/excel_cheatsheet`, is no longer updated.

## Hosting on Cloudflare Pages

Cloudflare Pages can't connect to Bitbucket repositories directly, so `bitbucket-pipelines.yml` uploads the page to Cloudflare on every push to `main` instead. One-off setup:

1. **Cloudflare project** — in [dash.cloudflare.com](https://dash.cloudflare.com): **Workers & Pages → Create → Pages → Upload assets**. Name the project (e.g. `aether-excel-handbook`), drag in `index.html`, and deploy. The site appears at `https://<project-name>.pages.dev`.
2. **API token** — My Profile → API Tokens → Create Token → Custom token with the permission **Account → Cloudflare Pages → Edit**. Copy it.
3. **Bitbucket variables** — in the repo: **Repository settings → Pipelines → Settings**, turn Pipelines on. Then **Repository variables**, add:
   - `CLOUDFLARE_API_TOKEN` — the token from step 2, with **Secured** ticked
   - `CLOUDFLARE_ACCOUNT_ID` — shown in the Cloudflare dashboard sidebar
   - `CLOUDFLARE_PROJECT` — the project name from step 1
4. Push any change to `main` (or run the pipeline manually) — from then on every push redeploys automatically.

Optional extras:

- **Custom domain** — in the Pages project → Custom domains → add e.g. `excel.aether-uk.com`, then create the CNAME record Cloudflare shows you.
- **Restrict to staff** — Zero Trust → Access → Applications → add a self-hosted application for the Pages hostname, with a policy allowing emails ending in `@aether-uk.com`.

## Offline use

`index.html` also works as a plain file — put it in Teams or a shared drive and double-click to open. Everything (search, live grids, the formatter) runs locally with no server. The **Print** button in the header saves a PDF copy.

## Updating the handbook

1. Edit `index.html`. Content is plain HTML; the data behind the interactive grids and walk-throughs lives in the `SHEETS` and `STEPPERS` objects in the first `<script>` block.
2. Open the file in a browser to check it.
3. Commit and push to `main` — the pipeline redeploys it.

Brand colours are CSS variables at the top of the `<style>` block (`--brand`, `--brand-light`, `--navy`).
