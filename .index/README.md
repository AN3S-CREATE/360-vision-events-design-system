# .index — project context index

The persistent context map for this repository, maintained under the global rule CONTEXT-INDEX-001. Read it before substantive work so changes respect the existing structure and decisions.

## What this repository is

An evidence-locked design system for **360 Vision Events**, read from the live public site. `https://360visionevents.co.za` returns a 302 to `https://360-vision-events.co.za/`. The deliverable is the package in `design-system/`. It records only what the site actually shows, and every token is marked observed, inferred or absent.

## Files in this index

| File | Purpose | Update when |
|---|---|---|
| `README.md` | This guide | The index structure or process changes |
| `file-inventory.md` | Every repository file: path, purpose, key symbols, status | Any file is created, edited, moved or deleted |
| `architecture.md` | How the package is produced and how its parts relate | The pipeline, token model or file layout changes |
| `key-decisions.md` | ADR-style log of technical and process decisions | A significant decision is made |
| `dead-code.md` | Unused or legacy items and light tech debt, with evidence | Dead code or debt is found or resolved |
| `context-refresh-log.md` | Log of full or partial index refreshes | After every meaningful refresh |

## Reading order

1. `file-inventory.md`
2. `architecture.md`
3. Only when relevant: `key-decisions.md` and `dead-code.md` (refactors, re-runs of the brief, tech-debt work).

## Maintenance rules

- **Write from the real files.** Every entry comes from reading the actual files; never write from memory.
- **Regenerated files.** `design-system/*` is regenerated as a set. After a re-run, refresh the inventory and log the refresh.
- **Tracing.** `design-system/evidence.json` is the audit trail for every token value. Look decisions up there by ID (D01–D28).
- **Write scope.** The original brief limited writes to `design-system/`. On 2026-10-02 the user accepted this index and `.claude/launch.json` as additions. Ask before adding anything else outside `design-system/`.
- **No secrets or personal data.** Never store secrets or personal data here. The package withholds phone digits, addresses and personal names (decision D16).
- **Git.** This folder is a git repository (`origin` = github.com/AN3S-CREATE/360-vision-events-design-system, public). Commit `.index/` with the package. Commits and pushes happen only when the user asks.
