# 007 — Payment Direction

Date: 2026-04-30

## Decision

Payment is a future consideration, not an MVP concern.

When it lands: **Even owns payment intent, not necessarily payment execution.** Integrations over ownership.

## What this means

- Even calculates what each person owes — that is the intent
- Execution (moving money) is handed off to external payment methods, not internalised
- Even is not a wallet, not a bank-like interface

## Non-negotiables when payment lands

- Must not become a fintech-first product
- Must not introduce stress, friction, or risk perception
- The closing ritual feeling (`problem.md`, decision 006) must be preserved

## What to avoid

- Becoming a wallet
- Becoming a bank-like interface
- Payment flows that make the split feel like a financial transaction rather than a natural conclusion

## Why

Payment infrastructure is heavy — compliance, trust, liability, UX weight. Even's defensibility is in the emotional dynamic of the bill moment, not in owning rails. Integrating into existing payment methods preserves the product feel while letting money move.

## Revisit when

- The split-and-pay loop becomes a real product need (users asking for it, or it being a blocker to retention)
- A payment integration partner is identified that can be dropped in without breaking the casual feel
