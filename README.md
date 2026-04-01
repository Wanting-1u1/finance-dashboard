# Finance Dashboard

Personal + family finance dashboard. Tracks 3 personal bank accounts and the shared AMEX card.

## Live URL

https://wanting-1u1.github.io/finance-dashboard

Password-protected. Password stored in Claude memory (not saved here).

## How to Run

```bash
cd "projects/financial-dashboard"
python3 -m http.server 8080
```

Open http://localhost:8080 in your browser.

> You need a local server (not just opening the file) because Chart.js loads from CDN.

## How to Use

### Adding a New Month

Each month, download your bank statements and upload them. The dashboard pre-loaded with Jan–Feb 2026 data.

**For future months:**
1. Export transactions from CommBank app → Transaction Summary PDF
2. Export from Westpac app → Transactions Report PDF (do this for both accounts)
3. Export from AMEX portal → XLSX file

Add new transactions manually or build the PDF/XLSX upload feature (planned).

### Reviewing Flagged Transactions

A yellow banner appears when a transaction needs categorisation. Go to Monthly Review → find the flagged item → use the category dropdown to assign it.

The **Jan 2 `$778` Westpac Saving withdrawal** is flagged — it's not the regular $680 rent. Assign it once you know what it is.

### Category Editing

Every transaction table has a category dropdown. Changes save immediately to localStorage and update all charts.

## Accounts Tracked

**Personal (3 accounts — internal transfers excluded)**
| Account | BSB/Account |
|---------|------------|
| CommBank Smart Access | 062498 10951944 |
| Westpac Life (Saving) | 032-067 747279 |
| Westpac Choice (Spend) | 732-067 534254 |

**Family**
| Account | Card |
|---------|------|
| AMEX Gold | W LI (-42014) + Z XING (-42006) |

## Savings Goal

Currently set to **40%** of monthly income. Update in the code:
```javascript
const SAVINGS_GOAL_PCT = 40;
```

## Data Persistence

All transaction data + category edits are saved to browser localStorage. Data persists between sessions on the same browser. To reset to the seed data, open DevTools → Application → Local Storage → delete `finance_v1`.

## Status

- Jan 2026: ✅ loaded
- Feb 2026: ✅ loaded
- Mar 2026+: add manually or build upload feature
