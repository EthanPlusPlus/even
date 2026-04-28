# 004 — Tax / Tip / Service Charge Distribution

Date: 2026-04-28

## Decision

The only thing Even actively computes is **tip**. Each diner pays `subtotal × (1 + tipRate)`. Default tipRate = 10% (ZA convention).

- **Per-bill override** at the start of the split flow: adjust the rate, or flip "tip already included" (sets rate to 0). Surfaced obviously at the moment of splitting.
- **Global default** in app settings: tipRate, defaults to 10%.
- **VAT** is informational. ZA line prices already include VAT; if a VAT line is on the receipt, capture it for display ("VAT: R45 included") and don't redistribute.
- **Receipt-side service charge** (e.g. 10% auto-added for large tables): for MVP, treated as a normal line item the user allocates to "everyone" (falls under Q2's equal-split-within-set rule). Acknowledged limit — see below.

## Why

ZA convention is straightforward: each diner adds 10% to their own subtotal, which aggregates to a 10% tip on the total without any per-charge distribution UX moment. That stays true to the principle (`problem.md`) — no "distribute the tip across diners" screen, just "+10% on what you owe."

Equal-split as a default was rejected outright: it lets a R30-coke drinker pay the same tip share as a R400-steak eater, which doesn't match how anyone actually splits a bill in practice.

VAT distribution doesn't exist as a problem in ZA — it's already in line prices.

## What this is NOT (yet)

- **Auto-detection of receipt-side service charges with proportional distribution.** Some markets auto-add 10–20% service for large parties; the correct handling distributes proportionally to consumption (same math as tip, just with rate sourced from the receipt). For MVP we don't detect this — auto-service is rare in ZA, so the wrong-but-tolerable behaviour is treating the line as user-allocated.
- **Locale-aware default tipRate.** US is 18–20%, JP is 0%, EU varies. For MVP the global default is one number (10%); the user changes it if they want.

## Future-proofing for global expansion

The current model leaves room for both gaps without rewrites:

- `tipRate` is a per-bill value, not a constant. Sourcing it from the receipt instead of from settings is a non-breaking change — same downstream math.
- When auto-service-charge detection lands: the bill carries a service rate from the receipt; tipRate defaults to 0 for this bill; user can stack more on top. Same calculation pipeline, different source.
- Locale-aware defaults later are a settings change, not a model change.

Build the door, don't walk through it yet.

## Schema implications

- A receipt carries `tipRate: Double` (per bill).
- The "tip already included" toggle is UX surface over `tipRate = 0`. No separate boolean unless future state proves it's needed.
- No `AncillaryCharge` or `Tax` entity. VAT, if extracted, lives as display-only metadata on the receipt.

## Revisit when

- Going beyond ZA — auto-service-charge handling and locale-aware defaults become real product needs.
- A user category emerges that wants per-bill tip-distribution behaviour different from "+rate on each subtotal" (e.g. "I'm covering Dave's tip share" — currently solved by paying extra on the spot rather than in-app).
