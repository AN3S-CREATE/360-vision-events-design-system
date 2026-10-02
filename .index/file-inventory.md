# File inventory

Last verified: 2026-10-02, against the files on disk after the package rebuild stamped 08:35:51Z. Status values: `Active`, `Generated`, `Experimental`, `Deprecated`, `Dead`.

| Path | Purpose | Key symbols / contents | Status |
|---|---|---|---|
| `design-system/DESIGN.md` | Human spec for designers and developers | §1 Brand name · §2 Source URL and redirect chain (with package files and value conventions) · §3 Colour · §4 Typography · §5 Spacing and radius (layout, shadow, motion) · §6 Components actually seen · §7 Voice, with quotes · §8 Usage rules · §9 Open gaps · Definition of done (criteria 1–7, all PASS) · Optional extras | Generated; do not edit by hand |
| `design-system/tokens.json` | DTCG-style tokens | 113 tokens in groups `color` (21), `font` (44), `space` (19), `size` (4), `breakpoint` (3), `z` (2), `blur` (2), `radius` (6), `shadow` (3), `gradient` (2), `motion` (7). `$extensions.mode`: 110 observed, 3 absent (`color.success`, `color.warning`, `color.info`). Root `$extensions` holds `name_rule`, `value_conventions`, `usage_count_rule` and `color_mode` (dark) | Generated; do not edit by hand |
| `design-system/tokens.css` | CSS custom properties mirroring tokens.json one-for-one | `:root { --<path with . → -> }`, e.g. `--color-brand: #ff4000`. Absent tokens are `initial`. Each line carries a comment with its mode and observation IDs | Generated; do not edit by hand |
| `design-system/evidence.json` | Audit trail | Top-level keys: `schema`, `stamp`, `status`, `operator`, `start_url`, `final_url`, `redirect_chain`, `local_brand_files`, `pages` (9), `fetch` (requests, hosts_contacted, not_fetched), `observations_summary` (per-dimension counts), `observations` (738; ID prefixes `col-`, `typ-`, `spc-`, `cmp-`, `voc-`, `*-miss-`, `orc-`), `decisions` (D01–D24), `assumptions` (A1–A5), `flags`, `quality_assurance`, `token_trace`, `extras`, `events` | Generated; do not edit by hand |
| `design-system/preview.html` | Optional extra: one-page component preview | Links `tokens.css` and the site's Google Fonts request. Shows swatches, type, spacing, radius, shadow, the header, all button variants, eyebrows, pills and chips, cards, the form, both CTA-band variants, the footer and the floating button. Opens from disk in any desktop browser; the in-app browser pane needs the static server in `.claude/launch.json` | Generated; do not edit by hand |
| `design-system/assets/logo-horiz-ON-DARK.png` | Byte-identical copy of the site's header logo | 1176×452 RGBA PNG; `#ff4000` mark | Active (observed asset) |
| `design-system/assets/favicon.png` | Byte-identical copy of the site's favicon | 64×64 PNG | Active (observed asset) |
| `README.md` | Repository front page: what the system is, contents, how to use it in CSS, Tailwind/shadcn and Claude | — | Active |
| `skill/360-vision-events-design-system/` (9 files) | Claude skill source: `SKILL.md` (brand rules, voice, gaps, working method), `assets/design-system/` (copies of tokens, preview, logo, favicon), `assets/shadcn-theme.css` (the site's `:root` vars + a Tailwind v4 adapter), `references/DESIGN.md`, `evals/evals.json` (3 test prompts) | Installed copy (without evals) at `~/.claude/skills/360-vision-events-design-system/` | Active |
| `.claude/launch.json` | Dev tooling: static server for the preview | Config `design-system-preview`: `python -m http.server 8765 --bind 127.0.0.1 --directory design-system` (run from the repository root) | Active |
| `dist/360-vision-events-design-system.skill` | Packaged Claude skill (zip) of the design system, for claude.ai "Save skill" / upload | SKILL.md + assets/design-system (tokens.css, tokens.json, preview.html, logo, favicon) + assets/shadcn-theme.css + references/DESIGN.md. Same content is installed for Claude Code at `~/.claude/skills/360-vision-events-design-system/` | Generated |
| `.index/*` (6 files) | This context index | README, file-inventory, architecture, key-decisions, dead-code, context-refresh-log | Active |

Plus `README.md` and the 9 skill-source files: 25 files in all, tracked in git (remote `origin` = https://github.com/AN3S-CREATE/360-vision-events-design-system, public, created by the user).

## Not in this repository

The pipeline that produced `design-system/` ran in the session's temporary scratchpad and is not versioned here (tech debt TD-01 in `dead-code.md`):

- **Scripts:** `build.py`, `check.py`, `preview.py` and `DESIGN.template.md`.
- **Inputs:** `obs-{color,type,space,component,voice}.json`, `flags.json`, `fetchlog.clean.json`, `secret_hashes.json`, `acceptance.md`, and the raw captures (`raw/*.html`, `styles.css`, the PNGs and `*.headers`).

Most of the inputs can be reconstructed from `evidence.json`, which holds all observations, flags and the fetch log.
