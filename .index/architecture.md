# Architecture

## Overview

A static, evidence-locked design-system package. There is no application code. The repository holds generated artefacts, two observed brand assets, the owner's logo pack, hand-built document templates and the Claude skill built from them.

```
live site (GET only)
  https://360visionevents.co.za --302--> https://360-vision-events.co.za/
        │  9 pages (home + 8 main-nav), styles-BQycqoql.css, logo PNG, favicon
        ▼
raw captures (session scratchpad, not versioned)
        │  5 extractor agents (colour, type, spacing/radius/shadow/motion, components, voice+privacy)
        │  each re-checked by an adversarial verifier → 738 observations
        ▼
token list (single source)  ──►  tokens.json  (DTCG-style)
                            ──►  tokens.css   (same names, one-for-one)
                            ──►  DESIGN.md    (token tables + spec)
                            ──►  evidence.json (observations, decisions, token_trace, events)
                            ──►  preview.html (optional extra, uses tokens.css)
tokens.css + logos  ──►  templates/ (D28: quotation + proforma invoice, A4, hand-built on tokens.css;
                         structure from the owner's old documents, every data value withheld)
        │
        ▼
mechanical acceptance check (criteria 1–7) + independent 6-agent audit + 2-agent re-audit
```

## Token model

- **Naming:** CSS custom property = `--` + token path with `.` replaced by `-`, so `color.brand` becomes `--color-brand`.
- **Modes:** `$extensions.mode` is `observed`, `inferred` or `absent`. There are no inferred tokens. Absent tokens have `$value: null` in JSON and `initial` in CSS.
- **Provenance:** each observed token carries `$extensions.source_url`, `selector` and `observation_ids`, and `usage_count` where meaningful. Where a value was resolved from `var()`, it also carries `declared` and `resolved_vars`. The 3 absent tokens carry only `mode`, `selector` and `observation_ids` (col-133–135).
- **Value conventions:**
  - Numbers are JSON numbers, and cubic-bezier easings are 4-number arrays.
  - Colours, dimensions, durations, shadows and gradients stay as the site's own CSS strings (hex, `oklch()`, `color-mix()`, `calc()`).
- **Colour mode:** dark only. A light mode is absent on the site.
- **Groups (113 tokens):** `color` (21), `font` (44), `space` (19), `size` (4), `breakpoint` (3), `z` (2), `blur` (2), `radius` (6), `shadow` (3), `gradient` (2), `motion` (7).

## Key observed facts (for orientation)

- **Palette:** canvas `#0b0b0c`, surface `#1a1a1c`, text `#f5f5f4`, muted text `#8a8a8e`, brand/accent/ring `#ff4000`. The brand value is an exact match for the logo mark pixels.
- **Fonts:** Space Grotesk (display, h1–h3), Inter Tight (body), and Inter through `.font-clean`, which overrides 6 of the 9 page h1s.
- **Scale:** spacing base `.25rem`, radius base `.5rem`, container `72rem` with a `20px` gutter, breakpoints `40`/`48`/`64rem`.
- **Toolchain:** the site's CSS is compiled Tailwind v4.3.3, and its components are shadcn-style.

## Constraints

- **Original brief:** write only under `design-system/`; never publish, commit or deploy without explicit confirmation; GET-only egress to the user URL, its redirect host and same-site assets.
- **Privacy:** POPIA minimisation. No phone digits, addresses or personal names in any artefact (D16).
- **Idempotency:** a re-run overwrites `design-system/` only after a new `evidence.json` stamp is written.
- **Hand corrections:** until the generator is versioned (TD-01), any change to a generated file is a hand correction, logged as a decision plus an `events` entry in `evidence.json` (D29, D30).
- **Line endings:** text is stored and checked out as LF everywhere (`.gitattributes`, D30). Hash files from an LF checkout or from `git show HEAD:<path>`, never from a CRLF working tree.
- **Copies:** the package exists in five places: `design-system/`, `skill/…/assets/design-system/` (+ `references/DESIGN.md`), `dist/*.skill`, the installed `~/.claude/skills/` copy and the Claude Design artifact. All are synced by hand, so check parity after every change (TD-04).
- **Owner binaries:** strip personal metadata before committing (D29), and keep the supplied sha256 for traceability.
