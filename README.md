# 360 Vision Events — Design System

An evidence-locked design system for **360 Vision Events**, read from the live site [360-vision-events.co.za](https://360-vision-events.co.za). It records only what the site actually uses: dark canvas `#0b0b0c`, brand orange `#ff4000`, Space Grotesk headings, Inter Tight body text, and a 0.25rem spacing scale. Every token traces back to the site's own CSS or markup. Anything the site doesn't define (a light theme, status colours, form states, a fully vector logo set) is listed as a gap rather than invented.

## What's here

| Path | What it is |
|---|---|
| [`design-system/DESIGN.md`](design-system/DESIGN.md) | The spec. **Start here:** brand name, colour, typography, spacing and radius, components, voice, usage rules, open gaps |
| [`design-system/tokens.css`](design-system/tokens.css) | 113 CSS custom properties (`--color-brand`, `--font-family-display`, `--space-4`, …) |
| [`design-system/tokens.json`](design-system/tokens.json) | The same tokens, DTCG-style (`$type`, `$value`, `$extensions`). Values stay as the site's own CSS strings (`oklch()`, `color-mix()`, `calc()`, shadow strings) and absent tokens are `null`, so adapt them before strict DTCG tools such as Style Dictionary or Tokens Studio |
| [`design-system/preview.html`](design-system/preview.html) | One-page component preview: swatches, type, buttons, cards, form, CTA bands |
| [`design-system/evidence.json`](design-system/evidence.json) | Audit trail: fetch log, 738 observations, decisions, and the source of every token |
| [`design-system/assets/`](design-system/assets/) | The site's logo PNG and favicon, unchanged |
| [`design-system/assets/logo-pack-2026/`](design-system/assets/logo-pack-2026/) | The official 2026 logo pack: 11 PNGs (horizontal, stacked, mark, wordmark; on-dark and on-light) plus 5 on-light SVGs in `svg/` (P09 wordmark fully vector), with a README on backgrounds, vector vs bitmap parts, orange values and file provenance |
| [`design-system/templates/`](design-system/templates/) | A4 quotation and proforma-invoice templates in the brand's look (dark, plus an ink-saving paper mode), with a structure README. Fill in a copy and save as PDF |
| [`skill/360-vision-events-design-system/`](skill/360-vision-events-design-system/) | Claude skill source: brand rules, voice and the bundled files |
| [`dist/360-vision-events-design-system.skill`](dist/360-vision-events-design-system.skill) | The packaged skill, ready to upload |
| [`.index/`](.index/) | Project context index (file inventory, architecture, decisions, tech debt) |

## Use it

**In CSS:** load the site's fonts, link the tokens and use the variables (`tokens.css` defines the font stacks but loads no fonts):

```html
<link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Space+Grotesk:wght@500;700&family=Inter+Tight:wght@400;500;600&display=swap">
<link rel="stylesheet" href="design-system/tokens.css">
<style>
  body { background: var(--color-bg); color: var(--color-text); font-family: var(--font-family-body); }
  .cta { background: var(--color-brand); color: var(--color-on-brand); border-radius: var(--radius-md); }
</style>
```

**In Tailwind v4 or shadcn/ui:** copy [`skill/360-vision-events-design-system/assets/shadcn-theme.css`](skill/360-vision-events-design-system/assets/shadcn-theme.css). It holds the site's own `:root` variables plus a Tailwind `@theme inline` mapping, so import it after `@import "tailwindcss";`. The mapping covers colours, radii and the body and display font families. It leaves out the site's heading rule (h1–h3 in Space Grotesk with `-.03em` tracking), `.font-clean` and `.card-lift`; copy those from `preview.html` if you need them.

**In Claude:**
- **Claude Code:** copy `skill/360-vision-events-design-system/` into `~/.claude/skills/` (or a project's `.claude/skills/`) without its `evals/` folder. You can also unzip `dist/360-vision-events-design-system.skill` there. Claude then applies the brand whenever you ask for 360 Vision Events work. Copy it again after pulling updates.
- **Claude app (claude.ai or desktop):** Settings → Capabilities → Skills → upload `dist/360-vision-events-design-system.skill`.

**Quotes and proforma invoices:** copy `design-system/templates/quotation.html` or `proforma-invoice.html` to a `*.filled.html` name in the same folder, so its styles and logo still load. Git ignores `*.filled.html`, `*.pdf` and `filled/` anywhere in this repository. Fill in the `[placeholders]` and line items, then print to PDF from Chrome or Edge (A4, margins none, background graphics on). Add `?mode=paper` to the address for the ink-saving version. See [`design-system/templates/README.md`](design-system/templates/README.md).

**Preview:** open `design-system/preview.html` in any desktop browser. Or serve the folder with `python -m http.server 8765 --bind 127.0.0.1 --directory design-system` and visit <http://127.0.0.1:8765/preview.html>.

## How it was made

1. **Fetch:** the homepage and the 8 main-nav pages were read with GET requests. `360visionevents.co.za` redirects to `360-vision-events.co.za`.
2. **Extract:** colour, type, spacing, components and voice were each extracted, and each extraction was checked by an independent verifier.
3. **Audit:** the finished package was audited twice more against the raw pages.
4. **Accept:** all seven acceptance criteria pass; see the Definition of done in `DESIGN.md`.

Phone numbers, addresses and personal names are withheld throughout, including in image metadata (decision D29).
