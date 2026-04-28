# Progress

## In Progress

- Resolving data-model open questions. Q1 + Q2 decided; Q3 (tax/tip), Q4 (currency) pending.

## Next

- Decide Q3 tax/tip distribution, Q4 currency.
- Sketch core SwiftData schema once those are settled (receipt → line items → allocations → persons).
- Spike VisionKit + Vision against real receipts to inform the OCR open question.

## Done

- 2026-04-28 — Decision `003-splitting-granularity`: line item → set of diners, equal split within set. No share counts. Door left open for fractional shares if/when needed.
- 2026-04-28 — Decision `002-diner-durability`: hybrid (durable `Person` under the hood, ephemeral input feel). Guardrail: not a debt tracker — no balance/settlement entities or UX.
- 2026-04-28 — Canonised product principle in `problem.md`: casual yet essential; every action compounds the vibe.
- 2026-04-27 — Xcode project scaffolded at `even/`, `.gitignore` added, user-state untracked.
