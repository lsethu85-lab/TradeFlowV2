# Meridian LC — Document Compliance Desk

A single-file, offline-capable Letter of Credit (LC) document checking dashboard for trade finance officers, exporters, importers, freight forwarders, and banks. Verifies that presented documents comply with LC terms before presentation to the bank.

No backend, no build step, no external services — everything runs in the browser and persists to `localStorage`.

![status](https://img.shields.io/badge/status-active-brightgreen) ![type](https://img.shields.io/badge/type-single--file%20app-blue) ![license](https://img.shields.io/badge/license-MIT-lightgrey)

---

## Features

- **Dashboard** — portfolio KPIs (open cases, pending review, discrepancies, expiring LCs, etc.) and six live charts
- **LC Case Management** — create/edit cases with full LC terms (parties, financials, dates, Incoterms, ports, goods description, HS code)
- **Document Checklist** — 20 standard trade-document categories auto-generated per case, drag-and-drop upload, versioning
- **Compliance Checker** — rule-based field-level verification of documents against LC terms (amount tolerance, currency, shipment date, ports, HS code, country of origin, goods description) with an animated compliance **seal** per case
- **Discrepancy Dashboard** — severity-classified (Critical / Major / Minor), correction status tracking, one-click discrepancy advice letter generation
- **Workflow** — 11-stage status timeline from Draft through Closed
- **Task Management** — Maker / Checker / Reviewer / Approver assignments with due dates and priority
- **Calendar** — shipment, expiry, presentation deadlines and task due dates in one view
- **Reports** — 9 report types, exportable to CSV / JSON
- **Audit Trail** — full change history (user, action, entity, old/new value)
- **Analytics** — discrepancy drivers, monthly volume, shipment performance, country/currency distribution
- **Security** — PIN lock, idle session auto-lock, role-based access (Administrator / Maker / Checker / Reviewer / Viewer)
- **Dark / light mode**

## Quick start

No install required.

```bash
git clone https://github.com/<your-username>/meridian-lc-desk.git
cd meridian-lc-desk
open index.html   # or just double-click the file / drag it into a browser
```

Or serve it locally if your browser restricts local file access:

```bash
python3 -m http.server 8000
# then visit http://localhost:8000
```

On first launch you'll be asked to set a 4-digit PIN and choose a role. The app seeds three example LC cases so there's data to explore immediately — clear them from **Settings → Wipe All Data** when you're ready to start fresh.

## Tech stack

- Vanilla HTML / CSS / JavaScript — no framework, no bundler
- [Chart.js](https://www.chartjs.org/) (loaded from CDN) for analytics charts
- `localStorage` for persistence (base64-wrapped JSON envelope)

## Data & privacy

All case data, documents metadata, and audit history stay in the browser's `localStorage` on the device you're using. Nothing is transmitted anywhere. Use **Settings → Export Full Backup** to download a JSON snapshot, and **Settings → Wipe All Data** to clear everything.

## Known limitations

- **OCR / document text extraction is simulated.** The "Auto-fill from LC" button on a document is a stand-in for real OCR — it copies LC terms into the extracted-fields form so you can see the compliance-check logic run. Wiring in a real OCR service (e.g. AWS Textract, Google Document AI) is a natural next step.
- **No SWIFT MT700 parsing.** LC terms are entered manually rather than parsed from a SWIFT message.
- **Single-user, single-browser.** There's no server, so data doesn't sync across devices or users — each browser has its own local desk.
- File "uploads" store metadata (name, size, category) rather than the file bytes, so re-opening the app won't show a persisted PDF preview.

## Roadmap ideas

- [ ] Real OCR integration for invoices, B/Ls, and certificates
- [ ] SWIFT MT700/MT707 message import to auto-populate LC terms
- [ ] Multi-user sync via a lightweight backend (e.g. Supabase, Firebase)
- [ ] PDF.js-based in-app document viewer
- [ ] Configurable document checklists per LC (not all 20 categories apply to every trade)

## License

MIT — do what you like with it.
