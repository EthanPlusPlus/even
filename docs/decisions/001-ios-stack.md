# 001 — iOS Stack

Date: 2026-04-27

## Decision

For the Even iOS app, the starting stack is:

- **Language**: Swift
- **UI**: SwiftUI
- **Testing**: Swift Testing (Apple's macro-based framework, Xcode 16+)
- **Storage**: SwiftData — local-only, single-user

OCR/receipt parsing is **not yet decided** — see `open-questions.md`.

## Why

**Swift + SwiftUI** is Apple's current recommendation for new apps in 2026. UIKit interop is available if a specific control needs it.

**Swift Testing** has cleaner syntax, parameterised tests, and parallel-by-default. It coexists with XCTest if we ever need to fall back.

**SwiftData (MVP, single-user)** is the deliberate scope choice. The product has two possible shapes:

- *Solo operator* — one person scans the receipt, allocates everyone's items, shares a summary out-of-app.
- *Everyone at the table* — every friend opens Even, sees the live bill on their phone, taps their own items.

The "everyone at the table" shape directly attacks the pain in `problem.md`, but it requires real backend infrastructure (auth, realtime sync across different Apple IDs, server) — a much larger build. Shipping the solo-operator loop first proves the OCR + allocation UX without that cost. Adding a backend later is a normal evolution; ripping one out is not.

## Revisit when

- **Joining the Apple Developer Program** (e.g. preparing for TestFlight). Flip on **CloudKit private DB** via SwiftData's `cloudKitDatabase` config — gives users free iCloud backup + same-Apple-ID sync of their bill history at near-zero implementation cost. Deferred from MVP only because CloudKit containers require the $99/yr program even in development.
- **Multiplayer-at-the-table becomes the validated product shape.** At that point migrate from SwiftData → **Supabase** (or equivalent BaaS) for shared, realtime state across different Apple IDs. Explicitly *not* CloudKit `CKShare` — share-acceptance flow is too clunky, Apple-only locks out future Android/web, and no server-side logic.
- We hit a Swift Testing limitation that XCTest solves (unlikely; flag if it happens).
