# Dead code and tech debt

This repository holds no application code, so it has no dead code. The register below tracks tech debt in the package itself. It also lists unused items observed on the source site that were deliberately not tokenised.

## Tech debt (this repository)

| ID | Item | Evidence | Priority | Recommended action |
|---|---|---|---|---|
| TD-01 | The generator pipeline is not versioned | `build.py`, `check.py`, `preview.py` and `DESIGN.template.md` produced `design-system/`. They read scratchpad inputs that no longer exist after the session: `obs-*.json`, `flags.json`, `fetchlog.clean.json`, `secret_hashes.json`, `acceptance.md` and the raw captures. Nothing in the repository can regenerate or re-verify the package | Medium | If re-runs are expected, ask the user before writing outside `design-system/`, then version the scripts and template under `tools/`. Adapt `build.py` to read observations, flags and the fetch log back from `evidence.json`, and read the personal-name redaction pattern from the captures at runtime instead of hard-coding it. Otherwise, re-run the original brief |
| TD-02 | `evidence.json` is large (~0.7 MB) | It holds all 738 observations verbatim, with snippets of 200 characters or fewer | Low | Keep it as is for its audit value. Split it by dimension only if tooling struggles |
| TD-03 | `preview.html` can't be viewed in the in-app browser pane from disk | Any desktop browser opens it from disk, because it has no scripts and only relative `<link>`/`<img>` references. The Claude Code browser pane renders `file://` pages as unstyled snapshots | Low | Use `.claude/launch.json` (`design-system-preview`), or `python -m http.server 8765 --bind 127.0.0.1 --directory design-system` and visit `http://127.0.0.1:8765/preview.html` |

## Observed on the source site but deliberately not tokenised

These are facts about the live site's CSS, not dead code in this repository. They are recorded so a future re-run does not mistake them for omissions.

| Item | Evidence (observation ID) | Status here |
|---|---|---|
| `--gradient-hero` / `.hero-surface`, `--gradient-accent` | col-022–024, col-102: declared, used by no element | Not tokenised; listed in DESIGN.md §9 |
| `--sidebar-*` referenced but never declared | col-140 | Not tokenised; listed in §9 |
| The site's undeclared `var(--color-bg)` reference | col-141: used only by the unused `.bg-(--color-bg)` utility | Not mapped. This package's `color.bg` token (from the site's `--background`) is emitted under the same CSS name `--color-bg`, so loading `tokens.css` on the site would make that utility resolve |
| Compiled but unused utilities: shadow-xs/md/lg/xl, link and destructive button styles, dialog/tabs/accordion/table utilities | col-040, spc-66, cmp-btn-12–13, cmp-abs-01–04 | Not tokenised |
| Absent components: ghost and icon-only buttons, pagination, breadcrumb, testimonial, stat cards | cmp-btn-11, cmp-btn-14, cmp-abs-05–08 | Not tokenised (nothing to record) |
| `color.destructive` / `color.on-destructive` | col-017, col-018: declared as `:root` custom properties, `usage_count` 0 | **Tokenised**, because the site declares them (observed). Marked as never rendered; form error states were not observed (§9) |
