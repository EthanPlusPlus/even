# 002 — Diner Durability

Date: 2026-04-28

## Decision

Diners are **durable under the hood, ephemeral in feel**.

- A `Person` entity persists across receipts.
- Input UX is type-a-name. No friends-list management screen.
- Typed names dedupe to existing Persons by normalised match. No contacts permission.

## Why

Two competing needs:

- The product principle (`problem.md`) wants input to feel as casual as typing names — no roster, no setup ceremony.
- Persisting Persons under the hood unlocks frictionless recall on subsequent bills (autocomplete) and cheap "Sarah was on these 5 receipts" surfaces, without forcing the user to manage a contacts model.

Pure-ephemeral throws away cross-bill identity for no UX gain. Pure-durable adds friends-list weight for no compounding payoff at MVP scale. Hybrid satisfies both.

## Guardrail — what this is NOT

Persistence here is for **recall**, not bookkeeping. Even is not a debt tracker.

- No `Balance`, `Debt`, or `Settlement` entities.
- No "X owes you Y" totals or settle-up flows in UI, even where data could support them.
- "Sarah was on these 5 receipts" (recall) is fine; "Sarah owes you R200 across these 5 receipts" (ledger) is not.

This guardrail is load-bearing — exposing aggregate balances would shift the app's vibe from casual to administrative, breaking the principle in `problem.md`.

## Schema implications

- `Person` — top-level SwiftData entity (id, displayName, normalisedName, timestamps).
- `Allocation` references `Person` (not a name string).
- Dedupe on input: trimmed + lowercased match against existing Persons.
- Merge-conflict UX (e.g. "Sarah" vs "Sarah K" being the same human) is punted to an open question.

## Revisit when

- Allocation UX surfaces a pain that recall-style framing doesn't address.
- Multiplayer-at-the-table becomes the validated shape (per decision 001) — at that point Person identity ties to authenticated accounts, not typed names.
