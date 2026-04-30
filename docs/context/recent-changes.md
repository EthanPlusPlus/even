# Recent Changes

Rolling log of meaningful system changes. Keep last ~10 entries.

---

- 2026-04-30 — Decision `007-payment-direction`: Even owns payment intent, not execution. Integrations over ownership. Must not become fintech-first; closing ritual feel is non-negotiable when payment lands.
- 2026-04-30 — Decision `006-product-identity`: Even is the closing ritual of a shared experience involving money, not a bill-splitting tool. Allocation screen is the product's core emotional moment (remembering, not assigning). Defensibility is in owning the bill moment's emotional dynamic. Hard constraints: no before/during, no social layer, no debt tracking.
- 2026-04-30 — Updated `problem.md`: reframed north star as "closing ritual", added emotional goal (nostalgia + recognition), added feature test ("lighter or heavier?").
- 2026-04-30 — Updated `constraints.md`: canonised time-window constraint (end-of-experience only), nostalgia-is-not-a-social-layer, debt tracker guardrail, payment processor guardrail.
- 2026-04-28 — Decision `005-currency`: `Receipt.currencyCode` (ISO 4217), MVP value always "ZAR". No picker, no global setting, no FX. Display via Foundation's currency-aware formatters. Door open for multi-currency without a migration. Closes the four-question data-model batch — schema sketch is unblocked.
- 2026-04-28 — Decision `004-tax-tip-distribution`: tip is the only ancillary charge Even computes; each diner pays subtotal × (1 + tipRate), default 10% (ZA). Per-bill rate override at start of split flow, plus global default in settings. VAT informational only (already in ZA prices). Auto-service-charge detection deferred — door left open for going global without a model rewrite.
- 2026-04-28 — Decision `003-splitting-granularity`: line items allocate to a set of diners with equal split within the set. No share counts. Migration path to fractional shares is documented but not built — door left unlocked, not installed.
- 2026-04-28 — Decision `002-diner-durability`: diners are durable `Person` entities under the hood with ephemeral-feeling input. Hard guardrail in the doc: Even is not a debt tracker — no `Balance`/`Debt`/`Settlement` entities, no aggregate "owes you" UX.
- 2026-04-28 — Canonised product principle in `problem.md` under a new `## Principles` section: "casual yet essential; every action compounds the vibe." Anchors future UX/scope decisions.
- 2026-04-27 — Captured 4 data-model open questions: diner durability, splitting granularity, tax/tip distribution, currency support. To be resolved before/alongside the SwiftData schema sketch.
- 2026-04-27 — Xcode project scaffolded at `even/` (SwiftUI + Swift Testing template). Added `.gitignore` and untracked `xcuserdata/` files that leaked into commit `fa048a6`.
- 2026-04-27 — Decision `001-ios-stack`: Swift + SwiftUI + Swift Testing + SwiftData (MVP, single-user). Multiplayer/Supabase deferred until product shape validated. CloudKit private DB to be flipped on when joining Apple Developer Program. OCR engine left as open question.
- 2026-04-27 — Added `docs/problem.md` capturing the product north star (the restaurant bill-splitting moment and root-cause analysis of why it sucks). Registered in `STRUCTURE.md`.
