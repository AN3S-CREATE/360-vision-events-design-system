---
name: 360-vision-events-design-system
description: >-
  The 360 Vision Events brand design system. It was read from the live site 360-vision-events.co.za and records only what the site actually uses. Dark canvas #0b0b0c, brand orange #ff4000, Space Grotesk headings and Inter Tight body, plus ready-made CSS tokens, component patterns, the logo and the brand's copy voice. Use this skill whenever you create, style, write or review anything for 360 Vision Events (also written 360VE or "360 Vision"). That includes web pages, landing sections, HTML emails, proposals, quotations, proforma invoices and other A4 commercial documents, slides, social posts, UI components, Tailwind/shadcn themes, event one-pagers, and on-brand copy or CTAs. Use it even when the user only says "use our brand", "make it look like our site" or "match our style" while working on 360 Vision Events material.
---

# 360 Vision Events design system

This skill holds the 360 Vision Events (South African corporate and brand event production) design system. It was extracted from the live website and records only what the site actually shows. Every value traces to the site's own CSS or markup. Where the site has no answer, the system says so rather than guessing.

That's the most important thing to carry into your work. **Build with what is here, and name gaps instead of inventing brand.** For example, the brand has no light theme, no success/warning colours, and only one fully vector logo (the P09 wordmark, ON-LIGHT); there are no ON-DARK SVGs. If a task needs one of these, use the closest observed pattern and tell the user it's a gap they may want to decide on.

## What's bundled

| Need | Use |
|---|---|
| Any visual output (HTML, email, slides, UI) | `assets/design-system/tokens.css` — CSS custom properties. Link it or inline the variables you use |
| Exact component markup and styling | `assets/design-system/preview.html` — every component styled only with the tokens. Copy patterns from it |
| Tailwind / shadcn projects | `assets/shadcn-theme.css` — the site's own `:root` variables (it is a Tailwind v4 + shadcn build) |
| Design-token tooling (Figma Tokens, Style Dictionary) | `assets/design-system/tokens.json` (DTCG-style: values are the site's CSS strings and absent tokens are `null`, so adapt them before strict DTCG tools) |
| Logo for web UI on the dark canvas | `assets/design-system/assets/logo-horiz-ON-DARK.png`: the site's own header logo. It is 1176×452, transparent, and its orange is exactly `#ff4000` |
| Official logo pack (print, social, decks, light backgrounds) | `assets/design-system/assets/logo-pack-2026/`: 11 PNGs, with ON-DARK and ON-LIGHT versions of P03/P05/P12 horizontal (P12 is ON-DARK only), P06 stacked, P07 mark and P09 360VISION wordmark. Its `README.md` maps the files |
| Scalable / vector logo (light backgrounds) | `assets/design-system/assets/logo-pack-2026/svg/`: transparent SVGs in ON-LIGHT only. `p09-wordmark-360vision-on-light.svg` is fully vector, with "360" exactly `#ff4000`. P03/P05/P06/P07 have vector lettering but a bitmap aperture ring (400–850 px), so keep them at or below roughly that size |
| Favicon / app icon | `assets/design-system/assets/favicon.png` (ring + "360"), or `p07-mark-360-*` from the pack |
| Quotation or proforma invoice (A4, print to PDF) | `assets/design-system/templates/`: `quotation.html` and `proforma-invoice.html` on the shared `document.css`. Copy a template, fill in its `[placeholders]` and line items, and keep its structure. `templates/README.md` lists every section and field |
| Full rationale, class strings, quotes, gaps | `references/DESIGN.md`. Read the relevant section when you need more than the summary below |

## Quick reference

### Colour (dark only)

| Token | Value | Role |
|---|---|---|
| `--color-bg` | `#0b0b0c` | Page canvas |
| `--color-surface` | `#1a1a1c` | Cards, bands, panels |
| `--color-surface-2` | `#242426` | Secondary-button fill only |
| `--color-text` | `#f5f5f4` | Body and heading text |
| `--color-text-muted` | `#8a8a8e` | Supporting copy, nav links, card bodies, placeholders |
| `--color-brand` | `#ff4000` | CTA fills, eyebrows, links, focus ring. Exactly the logo's orange |
| `--color-on-brand` | `#0b0b0c` | Text on orange: dark, never white |
| `--color-brand-hover` | `color-mix(in oklab, #ff4000 90%, transparent)` | Primary button hover |
| `--color-border` | `oklch(100% 0 0/.12)` | 1px hairline on cards, chips, dividers |
| `--color-input` | `oklch(100% 0 0/.16)` | Form fields, outline buttons |
| `--color-brand-border` | `color-mix(in oklab, #ff4000 35%, transparent)` | CTA-band outline |
| `--color-destructive` | `oklch(60% .22 25)` | Declared by the site but never shown; only for error states, and see the failing pairs below |

**Contrast:**
- text on bg: 18:1
- muted text on bg: 5.7:1
- orange on bg: 5.6:1
- dark text on orange: 5.6:1
- white on orange: only 3.5:1, which is why the site uses dark text there

**Pairs below WCAG AA** (4.5:1 for normal text, 3:1 for UI boundaries):
- **Destructive** (≈`#e62b34`): white on it 4.41:1; as text on bg 4.46:1 and on surface 3.94:1. Use it only for large text, icons and borders, where 3:1 is enough. Keep small error text in `--color-text` with a destructive icon or border beside it, and never let colour be the only signal. This applies to shadcn's destructive variant too.
- **Muted text on the CTA tint:** at the orange end of `--gradient-cta-tint` (≈`#372320`) muted text is 4.29:1. Keep muted copy off the first ~15% of the band, or use `--color-text`.
- **Orange on `--color-surface-2`:** 4.42:1. The site never puts orange text there; don't start.
- **Input border:** `--color-input` is 1.54:1 on bg (1.64:1 on surface) and is a transparent field's only edge. Whether that fails WCAG 1.4.11 is a judgement call; a label above every field helps.

### Typography

- **Display:** `--font-family-display` = `"Space Grotesk", "Helvetica Neue", sans-serif`. Used for h1–h3, with letter-spacing `-.03em`.
- **Body:** `--font-family-body` = `"Inter Tight", system-ui, sans-serif`.
- **Clean:** `--font-family-clean` = `Inter, system-ui, sans-serif`. Some inner-page heroes use it; prefer display for new work unless you're matching those pages.
- **Load:** use the site's Google Fonts request: `https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Space+Grotesk:wght@500;700&family=Inter+Tight:wght@400;500;600&display=swap`
- **Scale:** Tailwind steps: xs .75rem, sm .875rem, base 1rem, lg 1.125rem, xl 1.25rem, 2xl 1.5rem, 3xl 1.875rem, 4xl 2.25rem, 5xl 3rem, 6xl 3.75rem, 7xl 4.5rem.
- **Hero h1:** 5xl, rising to 7xl from 40rem, bold, line-height .95.
- **Section h2:** 3xl bold. Some sections rise to 4xl or 5xl from 40rem, CTA-band and form h2s stay 3xl, and a few use 4xl at every width.
- **Body copy:** sm or base, muted.
- **Eyebrows / kickers:** `text-xs`, uppercase, wide tracking (.18–.35em), brand orange. Write their source text in sentence case and let CSS uppercase it.

### Spacing, radius, elevation, motion

| Area | Values |
|---|---|
| Spacing | base `.25rem` (4px) steps. Most used: 8, 16, 20, 12, 24, 4px |
| Layout | `max-width: 72rem` container with a fixed `20px` gutter. Sections `py-20` (80px); home `py-24` |
| Breakpoints | 40rem, 48rem, 64rem |
| Radius | `.5rem` base: sm 4px (badges), md 6px (buttons, inputs, service cards), lg 8px (image cards, panels, CTA bands), xl 12px (teaser cards), full (pills) |
| Shadow | `--shadow-sm` (subtle black) on buttons and inputs. `--shadow-lift`, `0 24px 60px -24px` orange at 35%, on hover-lifted cards and the floating button |
| Focus | The site's value: a 1px orange ring with no offset (`--shadow-focus-ring`), drawn as a box-shadow with `outline: none`. On orange buttons it barely shows, and in Windows forced-colours mode there is no indicator at all. **Proposal for new work** (say you used it): on filled orange controls use the site's floating-button ring, `box-shadow: 0 0 0 2px var(--color-bg), 0 0 0 4px var(--color-ring)`, and swap `outline: none` for `outline: 2px solid transparent` so forced-colours mode still draws an outline |
| Motion | colour changes .15s; card lift .3s `cubic-bezier(.22,1,.36,1)` with a 6px rise; image zoom .5s at scale 1.02; scroll reveal .7s ease-out over a 24px rise |

## Core rules (and why)

1. **Dark canvas only.** The live site declares one dark palette and nothing else. Pages sit on `--color-bg`; cards, bands and panels sit on `--color-surface`. If a deliverable must be light (e.g. a printed letter), say it's outside the observed system rather than inventing a light palette.
2. **Orange is a signal, not a field.** Use it for the main CTA, eyebrows, links, focus and hover accents, and thin accent bars. Large areas only ever get a 14% tint (`--gradient-cta-tint`) or a 35–45% hairline. Big orange blocks would read as a different brand.
3. **Dark text on orange.** `--color-on-brand` (#0b0b0c) passes contrast; white does not.
4. **One hue.** The site's "accent" is the same orange. Don't add a second accent colour, success greens, gradients from other hues, or stock icon colours. Icons are 16px line icons (lucide-style, `stroke="currentColor"`).
5. **Hairlines over shadows.** Separate things with the 1px translucent border, not drop shadows. The only notable shadow is the orange `--shadow-lift` on hover.
6. **Buttons:**
   - `rounded-md`, `text-sm` medium weight, 8px gap, 16px icons.
   - **Primary** (orange) is the main CTA, usually WhatsApp.
   - **Outline** (`--color-input` border on the canvas; fills orange on hover) is the alternative.
   - **Secondary** (`--color-surface-2`) is used for form submits next to a WhatsApp link.
   - Heights: 32px (header), 36px, 40px (standard CTA), 48px (hero).
7. **Cards:**
   - `--color-surface` with a 1px `--color-border`.
   - Interactive cards lift 6px on hover, gain `--shadow-lift`, and their border turns 45% orange.
   - Case-study cards put the photo full-bleed under a bottom-up `--gradient-scrim`, with an orange uppercase kicker, a bold title and "View case study →".
8. **Imagery:** real event production photography, `object-cover`, always under a dark scrim where text overlaps. Ratios 16/10 and 4/3. If you show a concept render rather than a real job, label it, the way the site labels its mock-ups "CONCEPT · MOCK".
9. **Logo:**
   - **Web UI:** use the transparent site logo, or a pack file whose solid background matches the ground.
   - **Light media:** use the pack's ON-LIGHT files, which are only for genuinely light material such as print or partner decks. The UI itself stays dark.
   - **Pack backgrounds:** pack files are 2000×2000 on solid `#000000`/`#ffffff`, so an ON-DARK file shows a faint box on the `#0b0b0c` canvas. Crop it or match the ground.
   - **Never alter the marks.** Don't recolour, redraw or trace them to SVG.

For component recipes (header, buttons, eyebrows, pills and filter chips, badge, cards, form controls, CTA bands, footer, floating WhatsApp button), open `assets/design-system/preview.html` and reuse its CSS. It is the shortest correct path to on-brand markup.

## Voice

The site's voice is short, confident and production-floor practical:

- **Staccato headlines with full stops.** "Brief the floor team." "See the work. Then brief the team." "Floor notes. Not brochure filler."
- **The mantra:** "ONE team. ONE Concept. ONE Event. ONE Invoice." (also written with middots: "ONE team · ONE Concept · ONE Event · ONE Invoice").
- **CTAs:** sentence-case imperatives of 2–4 words, with WhatsApp first. "WhatsApp the floor team", "Send a brief", "Book a date", "View case study →".
- **Core vocabulary:** *floor* ("floor team", "on the floor"), *brief*, *production path*, "X, not Y" contrasts ("Proof, not brochure.").
- **UK/South African spelling:** décor, colour, programme, catalogue, centrepieces, finalised. R (rand) amounts, Gauteng, "across South Africa", "Working nationwide".
- **Punctuation:** spaced em dashes and middot separators. No exclamation marks.
- **Scope line when relevant:** "Corporate and brand only — not weddings or private parties."
- **Name:** "360 Vision Events" in copy. The legal form "360 Vision Events (PTY) Ltd trading as 360 Vision Events" only in legal or footer lines.
- **Don't invent proof.** The site prides itself on factual captions: no invented metrics, guest counts, awards, testimonials or client logos. Use facts the user gives you.
  - Claims visible on the site (15+ years, Level 2 BEE) may be reused as stated there, but suggest the user confirm they are current.
  - Client names appear as text pills, not logos.

## Commercial documents

Quotations and proforma invoices share one structure, rebuilt from the brand owner's own documents. `assets/design-system/templates/README.md` lists every field.

- **Every A4 page** has a running header (logo, "Corporate & brand event production", the services line, a 2px brand bar) and a footer (legal line, contact placeholders, domain).
- **Quotation:** title block with the reference list → event title → prepared for / prepared by → project details beside the total → 01 Brief and commercial terms → 02 Service and infrastructure specification → 03 Quotation schedule (grouped line items, subtotals, totals box) → 04 Client acceptance (signature lines, service provider details).
- **Proforma invoice:** title block → bill to / from → RE line → event details beside the amount due → what it covers and excludes → line items and totals → payment and banking details. It states that it is not a tax invoice.
- **Amounts** use the South African format "R 12 345.00". The inline script recalculates totals from each row's `data-qty` and `data-rate`. Set `data-vat` on `<html>` to charge VAT.
- **Modes:** dark is the default. `?mode=paper` gives the ink-saving print version; its light values are proposals (see Known gaps).
- **Real details:** never invent client, banking, registration or contact details. Put the real ones only in the user's own filled-in copy, never in a shared or public file. Leave a `[placeholder]` when you don't have a value.

## Contact details

- **Generic channels:** use `info@360-vision-events.co.za` and the domain `360-vision-events.co.za`.
- **Phone, WhatsApp and address:** ask the user for the numbers or address to show rather than pulling personal-looking numbers or street addresses from anywhere.
- **Placeholders:** for a WhatsApp link, leave a clearly marked placeholder if you don't have the number.

## Known gaps (don't fake these; flag them)

- **No light theme**, and no success, warning or info colours.
- **Form states not observed:** no error, helper, required or success styling was seen.
- **No visible active nav state:** on the live site the active link renders muted because of CSS order. If the user wants one, propose it as a new decision.
- **Logo:** only the P09 wordmark is fully vector. The P03/P05/P06/P07 SVGs use a bitmap ring that is slightly lighter (about `#ff4e23`–`#ff5636`) than their `#ff4000` lettering. "EVENTS" grey is `#737373` in P03/P05/P06 (P07 is the mark only) and `#828282` in P09. There are no ON-DARK or P12 SVGs.
- **Logo provenance:** Canva's content credentials record the pack as AI-assisted composites made with "Canva AI". The PNGs were stripped of their metadata, including a personal author name; only the pHYs resolution chunk is kept (D29). The P03/P05/P06/P07 SVGs still carry the signed credential, so platforms that read it may label posts that use them as AI-generated. Mention this if the user is choosing files for social media.
- **Pack orange varies by file:** `#e22500` to `#ff3e00`, and the P09 wordmark is `#f14624`. The UI brand colour stays the site's `#ff4000`. When a design must match the orange in the logo, P12 (`#ff3e00`) is closest. Mention the inconsistency if it matters for the task.
- **Font loading:** Space Grotesk 400/600 are used but not loaded (the browser substitutes 500/700). If you control font loading, requesting `Space+Grotesk:wght@400;500;600;700` is a reasonable fix to suggest, not something the site does today.
- **Print and light media:** the site has no light theme. The document templates' paper mode uses proposed values (ink `#0b0b0c`, muted `#5f5f64`, orange only for rules, bars and large figures, because `#ff4000` on white is 3.5:1). Flag them as proposals.
- **Reduced motion:** no `prefers-reduced-motion` handling. Adding it in new work is fine; say you added it.

## Working method

1. Decide which bundled file fits the task (see the table at the top). For visual work, start from `tokens.css` and `preview.html`; for copy, follow the Voice section.
2. Use token variables (`var(--color-brand)`), not raw hex, so the output stays tied to the system. Use raw values only where a token cannot be used, e.g. inline styles in HTML email, where many clients ignore CSS variables. In that case use the exact hex values above.
3. When the task needs something the system doesn't define, pick the nearest observed pattern, then tell the user in one line what you had to extend.
4. Before finishing, check:
   - dark canvas;
   - orange used sparingly, with dark text on it;
   - Space Grotesk and Inter Tight;
   - hairline borders;
   - sentence-case CTAs, full-stop headlines and UK spelling;
   - no invented claims or contact details.
