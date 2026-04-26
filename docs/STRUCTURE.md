# Documentation Structure — Even

This file defines the rules, folder purposes, and conventions for Even's documentation.
It follows the Prismo canon structure convention.

---

## Guiding Principle

Just enough structured, retrievable documentation — never more.
Every doc should earn its place. If removing it would not hurt, it should not exist.

---

## Indexing Boundaries

- `decisions/`, `runbooks/`, `architecture/`, `context/` — **indexed and trusted**
- `proposed-ideas/` — **indexed**; ideas with reasoning not yet adopted
- `STRUCTURE.md` — indexed; shapes retrieval behavior

---

## Folders

### `context/`

Purpose: Live state of the project. What is true right now.

- `progress.md` — what is done, in progress, and next
- `recent-changes.md` — rolling log of meaningful changes (last ~10)
- `constraints.md` — active limitations affecting design or behavior

### `decisions/`

Purpose: Record why something was decided. One file per decision.
Naming: `NNN-short-slug.md` (e.g. `001-receipt-parsing.md`)

### `runbooks/`

Purpose: Step-by-step procedures for repeatable tasks.

### `architecture/`

Purpose: Intended design of the system — what it is meant to look like.

### `proposed-ideas/`

Purpose: Ideas worth capturing with reasoning, not yet adopted.
Naming: `NNN-short-slug.md`, same numbering as decisions.

### `open-questions.md`

Purpose: Flat list of unresolved questions not yet mature enough to become decisions.

---

## Naming Conventions

- Filenames: lowercase, hyphen-separated
- Decision/idea files: `NNN-short-slug.md`, zero-padded to three digits
- No spaces in filenames
