# TaxVault — Indian ITR Checklist, Documents & Tax Estimation Dashboard

**Author:** Sethuraman  
**Project Type:** Offline browser-based Indian tax filing helper  
**Primary File:** `index.html` / `index-fixed-v2.html`  
**Status:** Personal tax dashboard / filing preparation assistant

---

## Overview

TaxVault is an offline, browser-based Indian income tax filing helper for individuals, NRIs, RNORs, and business/profession users.

It helps users organize tax documents, scan uploaded documents, estimate tax under the old and new tax regimes, review multiple bank statement credits, and prepare for Indian ITR filing.

> **Disclaimer:** TaxVault provides estimated tax calculations and document review assistance only. It is not a substitute for a Chartered Accountant, tax consultant, or the official Income Tax e-Filing Portal.

---

## Key Features

### Dashboard

- Financial year-wise workspace
- Estimated tax summary
- Recommended tax regime display
- Document completion progress
- Recent activity tracking
- Visual charts for:
  - Income
  - Deductions
  - Tax
  - Document status

---

## Tax Computation

TaxVault supports tax estimation for:

- Resident individuals
- RNOR users
- NRI users
- Salary income
- Foreign salary
- Interest income
- Rental income
- Dividend income
- Short-term capital gains
- Long-term capital gains
- Business / profession income
- Deductions under:
  - Section 80C
  - Section 80CCD(1B)
  - Section 80D
  - Section 24(b)
  - HRA
  - LTA
  - Section 80G
  - Section 80TTA / 80TTB
- TDS
- Advance tax
- Self-assessment tax

---

## NRI / RNOR Support

TaxVault includes residency-based logic.

### NRI

- Indian-source income is taxable.
- Foreign salary is excluded from Indian taxable income.
- Rebate under Section 87A is not applied.
- Section 80TTA is not applied.

### RNOR

- Foreign income is excluded unless connected with a business controlled from India.
- Indian-source income remains taxable.

### Resident / ROR

- Worldwide income is taxable.
- Normal deductions and rebate logic are applied.

---

## Multiple Bank Statement Auto-Fill

TaxVault can scan and review multiple uploaded bank statements from different banks.

Supported examples include:

- Axis Bank statements
- SBI statements
- Union Bank statements
- NRO account statements
- Savings account statements
- Current account statements

### Auto-Fill Path

```text
Tax Computation → Auto-Fill from All Documents
```

When Auto-Fill is clicked, TaxVault attempts to detect:

- Total bank credits across all uploaded bank statements
- Credits above ₹12 lakh for review
- Estimated taxable bank credits
- Cash deposits for review
- Bank interest income
- Possible salary / business / rent receipts

---

## Important Indian Tax Logic

TaxVault does **not** treat total bank credits as taxable income automatically.

```text
Bank credits ≠ taxable income
```

Only the income component is taxable.

Examples:

| Bank Credit Type | Tax Treatment |
|---|---|
| Salary | Taxable |
| Business receipt | Taxable |
| Professional / freelance receipt | Taxable |
| Rent received | Taxable |
| Bank interest | Taxable as interest income |
| Mutual fund redemption | Only capital gain portion is taxable |
| Self transfer | Not taxable |
| Family transfer / eligible gift | Generally not taxable |
| Refund / reversal | Generally not taxable |
| Cash deposit | Review source; not taxable automatically |

---

## ₹12 Lakh Credit Review

TaxVault includes a review field for:

```text
Bank Credits Above ₹12L Review
```

This is only a warning/review metric.

It does **not** mean that the amount above ₹12 lakh is taxable.

The taxable amount is calculated separately under:

```text
Estimated Taxable Bank Credits
```

and:

```text
Taxable Bank Credits Manually Confirmed
```

---

## Multi-Bank Consolidation Logic

When multiple bank statements are uploaded, TaxVault consolidates all detected credit rows into one combined review row:

```text
All bank statements — consolidated FY credit review
```

Individual bank statements are marked as included in the consolidated review to avoid double counting.

This prevents the same bank document set from applying totals multiple times during Auto-Fill.

---

## Document Vault

TaxVault stores documents locally in the browser using:

- LocalStorage for metadata
- IndexedDB for files

No uploaded document is sent to a server.

Supported document categories include:

- Form 16
- Form 26AS
- AIS / TIS
- Salary slips
- Bank statements
- NRE / NRO / FCNR statements
- Mutual fund statements
- Capital gains reports
- Demat statements
- FD statements
- Insurance documents
- Home loan documents
- Rent receipts
- Foreign salary documents
- Passport / travel proof
- DTAA / Form 10F
- Tax Residency Certificate

---

## Auto-Fill from Documents

TaxVault can extract values from uploaded documents using browser-side parsing.

It attempts to detect:

- Salary
- TDS
- Interest income
- Dividend income
- Rental income
- Capital gains
- 80C deductions
- 80D deductions
- NPS deduction
- Home loan interest
- Bank statement credits
- Cash deposits

After scanning, TaxVault shows a review modal where the user can:

- Check extracted values
- Edit values
- Uncheck incorrect rows
- Apply values to Tax Computation

---

## OCR Support

For scanned or image-heavy PDFs, TaxVault can use OCR fallback through Tesseract.js.

This helps with scanned bank statements where normal PDF text extraction may fail.

> OCR accuracy depends on document quality.

---

## Calculators Included

TaxVault includes built-in calculators for:

- HRA exemption
- Capital gains
- Debt mutual fund / property indexation
- Home loan deduction
- NPS benefit
- 80C utilization
- Bank / FD interest deduction
- Advance tax schedule

---

## Reports

TaxVault can generate:

- Income summary
- Investment summary
- Capital gains summary
- Deduction summary
- Annual tax report
- Filing readiness report

Export options:

- PDF
- Excel
- CSV
- JSON backup

---

## Privacy

TaxVault is designed as an offline-first personal tax workspace.

```text
Your files stay in your browser.
No server upload.
No cloud database.
No external backend.
```

Clearing browser data may delete your stored TaxVault documents, so regular backup is recommended.

---

## How to Use

### 1. Open the App

Open either:

```text
index.html
```

or the fixed version:

```text
index-fixed-v2.html
```

in your browser.

---

### 2. Select Financial Year

Choose the financial year from the top bar.

Example:

```text
FY 2025-26
```

---

### 3. Select Residency

Choose one:

```text
Resident (ROR)
RNOR
NRI
```

---

### 4. Upload Documents

Go to:

```text
Documents
```

Upload:

- Bank statements
- AIS
- Form 26AS
- Capital gains reports
- Salary documents
- Deduction proofs

---

### 5. Auto-Fill Tax Fields

Go to:

```text
Tax Computation
```

Click:

```text
Auto-Fill from All Documents
```

Review extracted values carefully before applying.

---

### 6. Compute Tax

Click:

```text
Compute Tax (Old vs New)
```

TaxVault will compare:

- Old regime
- New regime

and recommend the better option.

---

## Recommended Project Structure

```text
taxvault/
│
├── index.html
├── index-fixed-v2.html
├── README.md
└── assets/
    └── optional screenshots
```

---

## Browser Requirements

Recommended browsers:

- Google Chrome
- Microsoft Edge
- Firefox

Required browser capabilities:

- IndexedDB
- LocalStorage
- File API
- JavaScript enabled

---

## External Libraries

TaxVault uses CDN-based browser libraries:

- Chart.js
- jsPDF
- SheetJS / XLSX
- PDF.js
- Tesseract.js for OCR fallback

---

## Limitations

TaxVault is a filing assistant, not an official ITR filing engine.

Please verify:

- AIS
- Form 26AS
- TDS
- Capital gains
- Foreign income
- DTAA claims
- NRI residential status
- Bank credit sources
- Business income classification

before filing your income tax return.

---

## Recommended Verification Before Filing

Before submitting your ITR, verify:

- AIS / TIS values
- Form 26AS TDS
- Salary Form 16
- Bank interest certificates
- Mutual fund capital gains statement
- Demat capital gains statement
- NRO TDS, if applicable
- Foreign salary / DTAA documents
- Bank credit explanation for large transactions

---

## Roadmap

Planned improvements:

- Better capital gains classification
- AIS import matching
- Form 26AS parser
- NRO TDS detection
- Bank-wise credit breakdown
- Exportable tax working sheet
- ITR form recommendation
- More accurate business income detection
- Manual tagging of bank credits as taxable / non-taxable

---

## Author

**Sethuraman**

---

## License

This project is for personal tax organization and educational use.

You may modify and use it for your own filing preparation.

---

## Disclaimer

This software provides estimated calculations based on user-entered and document-extracted data.

Tax laws change frequently. Always verify calculations on the official Income Tax Department e-Filing Portal or with a qualified Chartered Accountant before filing your ITR.
