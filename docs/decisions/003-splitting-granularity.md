# 003 — Splitting Granularity

Date: 2026-04-28

## Decision

A line item is allocated to **one or more diners**. When allocated to multiple, the cost splits **equally** among them. No per-diner share counts.

UX: tap item → tap one or more people → done.

## Why

Three options were on the table (see `decisions/` history): whole-item-only, fractional shares, or item-to-set-of-diners with equal split. Only the third holds the line on the casual-essential principle (`problem.md`) while still covering the realistic "Sarah and I shared the nachos but Dave didn't" case.

- Whole-item-only forces the user to lie about who actually ate what.
- Fractional shares introduce share-counting UX, which feels calculator-y and directly tugs against the principle.
- Item-to-set covers ~95% of real cases with a near-trivial model.

## What this is NOT (yet)

It does not model uneven shares within a set ("I had 2 nachos, Sarah had 1"). On a casual bill that precision is rarely worth the friction. Acknowledged limit, not an oversight.

## Schema implications

- A line item's allocation references a set of `Person`s. Cost splits equally across that set.
- No `Share` entity. No per-item weights or counts.
- Per-person subtotals (needed for proportional tax/tip in Q3) are computed by summing each line item's per-head cost across the diners assigned to it.

## Future-proofing for fractional shares

If uneven within-set shares ever become a real product need, the migration path is:
- Introduce a `Share` entity wrapping `(Person, weight)`.
- Existing allocations migrate to "everyone in the set gets weight 1" — semantically identical to today.
- UX gains a per-item "split unevenly…" escape hatch; the default flow stays as it is now.

The model today should not preclude that. It should also not pre-build it. Leave the door unlocked, don't install the door.

## Revisit when

- Real usage shows uneven within-set splitting comes up often enough that the workaround (assign the whole item to one diner and reconcile out-of-band) starts hurting.
- Multiplayer-at-the-table lands (decision 001) — concurrent edits on a shared allocation set need a conflict story regardless of share model.
