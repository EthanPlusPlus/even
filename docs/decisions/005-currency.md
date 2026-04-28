# 005 — Currency

Date: 2026-04-28

## Decision

Each receipt carries a `currencyCode: String` (ISO 4217). For MVP the value is always `"ZAR"`; display uses Foundation's currency-aware formatters keyed off the code.

No global currency setting yet. No per-bill picker yet. Both surfaces light up only when multi-currency becomes real.

## Why

Hard-coding ZAR everywhere would have meant a migration (every existing receipt back-filled with a currency) plus a display-code sweep the day multi-currency becomes a product need. A static `currencyCode` field today costs effectively nothing and removes both.

Direct application of the ZA-first / global-aware pattern — door unlocked, not installed.

## What this is NOT (yet)

- **No FX conversion.** Each bill is end-to-end in one currency. Cross-bill aggregation across currencies would also conflict with Q1's "not a debt tracker" guardrail.
- **No currency picker UX.** There is no choice to expose at MVP.
- **No global default in settings.** Layered config (the saved pattern) only kicks in when there's a real choice to make.

## Schema implications

- `Receipt.currencyCode: String`, defaults to `"ZAR"`.
- All amount display goes through `Decimal.formatted(.currency(code: receipt.currencyCode))` (or equivalent). No hand-rolled "R" prefixing.
- No currency on `Person`, `LineItem`, or `Allocation` — currency lives at the receipt level only.

## Revisit when

- Multi-currency becomes a real product need (going beyond ZA, or users travelling). At that point: add a global default in settings + a per-bill override at receipt creation. No data migration required.
