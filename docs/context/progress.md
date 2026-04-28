# Progress

## In Progress

_(nothing currently in progress)_

## Next

- Sketch core SwiftData schema. Entities: `Receipt` (with `tipRate`, `currencyCode`), `LineItem`, `Person`, `Allocation` (line item → set of persons, equal split within set).
- Spike VisionKit + Vision against real receipts to inform the OCR open question.

## Done

- 2026-04-28 — Decision `005-currency`: `Receipt.currencyCode` (ISO 4217), defaults to "ZAR" for MVP. No picker, no global setting, no FX. Door open for multi-currency without a migration.
- 2026-04-28 — All four data-model open questions resolved (Q1 diner durability, Q2 splitting granularity, Q3 tax/tip, Q4 currency). Schema sketch unblocked.
- 2026-04-28 — Decision `004-tax-tip-distribution`: tip is the only thing Even computes; each diner pays `subtotal × (1 + tipRate)`, default 10% (ZA). Per-bill override + global default. VAT is informational; auto-service-charge detection is door-left-open future work.
- 2026-04-28 — Decision `003-splitting-granularity`: line item → set of diners, equal split within set. No share counts. Door left open for fractional shares if/when needed.
- 2026-04-28 — Decision `002-diner-durability`: hybrid (durable `Person` under the hood, ephemeral input feel). Guardrail: not a debt tracker — no balance/settlement entities or UX.
- 2026-04-28 — Canonised product principle in `problem.md`: casual yet essential; every action compounds the vibe.
- 2026-04-27 — Xcode project scaffolded at `even/`, `.gitignore` added, user-state untracked.
