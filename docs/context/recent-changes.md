# Recent Changes

Rolling log of meaningful system changes. Keep last ~10 entries.

---

- 2026-04-28 — Decision `003-splitting-granularity`: line items allocate to a set of diners with equal split within the set. No share counts. Migration path to fractional shares is documented but not built — door left unlocked, not installed.
- 2026-04-28 — Decision `002-diner-durability`: diners are durable `Person` entities under the hood with ephemeral-feeling input. Hard guardrail in the doc: Even is not a debt tracker — no `Balance`/`Debt`/`Settlement` entities, no aggregate "owes you" UX.
- 2026-04-28 — Canonised product principle in `problem.md` under a new `## Principles` section: "casual yet essential; every action compounds the vibe." Anchors future UX/scope decisions.
- 2026-04-27 — Captured 4 data-model open questions: diner durability, splitting granularity, tax/tip distribution, currency support. To be resolved before/alongside the SwiftData schema sketch.
- 2026-04-27 — Xcode project scaffolded at `even/` (SwiftUI + Swift Testing template). Added `.gitignore` and untracked `xcuserdata/` files that leaked into commit `fa048a6`.
- 2026-04-27 — Decision `001-ios-stack`: Swift + SwiftUI + Swift Testing + SwiftData (MVP, single-user). Multiplayer/Supabase deferred until product shape validated. CloudKit private DB to be flipped on when joining Apple Developer Program. OCR engine left as open question.
- 2026-04-27 — Added `docs/problem.md` capturing the product north star (the restaurant bill-splitting moment and root-cause analysis of why it sucks). Registered in `STRUCTURE.md`.
