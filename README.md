# MyMoney — iPhone-compatible PWA (Windows-friendly)

## Features
- Add/edit/delete income, expense and internal transfer records.
- Monthly balance, spending, budgets, category breakdown and transaction search.
- CSV transaction import with preview, basic heuristics and duplicate detection.
- Local browser storage and JSON backup/restore.
- Installable progressive web app; offline asset cache.

## Run on Windows
1. Extract the ZIP.
2. In the extracted directory, run `python -m http.server 8000` (Python required), then open http://localhost:8000 on your PC.
3. To use on iPhone, host these static files on a HTTPS website (e.g., GitHub Pages or Cloudflare Pages). Open the HTTPS URL in Safari and choose Share > Add to Home Screen.
4. IMPORTANT: Local browser storage on PC and iPhone are separate. Data is NOT synchronized across devices. Use JSON export/import for manual migration.

## Import
CSV template in app. Required: `date`, `description`, and either `amount` or `debit`/`credit`; optional `type`. Format YYYY-MM-DD or DD/MM/YYYY. Positive amounts without a `type` are assumed to be income, negative amounts expense. This is NOT universally correct for bank statements; always inspect preview. Automatic classification is heuristic. TNG/CIMB exports may need column mapping or CSV conversion; PDFs are not yet parsed.

## Security and integration limitations
- No bank credentials or email credentials are collected.
- No Gmail OAuth, email polling, bank API, PDF extraction, server-side encrypted storage, or background synchronization has been implemented.
- Never publish Gmail OAuth secrets or bank tokens in this client app.
- To add email sync: implement a trusted backend, Google OAuth authorization code flow with PKCE, encrypted token storage, minimal Gmail readonly scope, periodic Gmail API polling or push, source-specific parsers, deduplication, user review and revocation. Verify Google API scope compliance and provider terms first.
- LocalStorage is not encrypted and may be cleared by the browser; do not store sensitive full statements or bank account numbers in notes. Back up regularly.
- Transfers are identified heuristically and can be manually corrected.

This is a functional prototype, not a verified bank-integrated product. It has not been tested on a physical iPhone.
