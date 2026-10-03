# Document templates — quotation and proforma invoice

Two print templates that rebuild the structure of the brand owner's earlier quotation and proforma invoice in the site's dark design system. Both open in a browser, fill in as plain HTML and print to an A4 PDF from Chrome or Edge.

| File | What it is |
|---|---|
| `document.css` | Shared document styles: modes, A4 page model, running header and footer, every `doc-` component, toolbar and print rules. Loads after `../tokens.css`. |
| `quotation.html` | Quotation template, filled with sample content. |
| `proforma-invoice.html` | Proforma invoice template, filled with the same sample event, so the two read as a matched pair. |
| `README.md` | This guide. |
| `.gitignore` | Keeps filled copies and their PDFs (`*.filled.html`, `*.pdf`, `filled/`) out of git. |

Everything shipped here is **sample content**: bracket placeholders such as `[Client company]` and round illustrative amounts, marked with a "Sample · Template" badge. No real client, banking or personal data belongs in this folder (see [Privacy](#privacy)).

## Quick start

1. Open `quotation.html` or `proforma-invoice.html` in Chrome or Edge, straight from disk.
2. Use the toolbar to switch between **Dark** and **Paper**, and to **Print / Save as PDF**. It sits above the sheet's right edge, or beside the sheet on screens wide enough to have a gutter; it never covers the page.
3. In the print dialog choose: **Destination** Save as PDF · **Paper size** A4 · **Margins** None · **Options** Background graphics on (and the browser's own headers and footers off).

The toolbar is screen-only and never prints. The page reads `?mode=paper` (or `#paper`) from its URL, so `quotation.html?mode=paper` opens in paper mode.

## Modes

| Mode | Set by | Look |
|---|---|---|
| Dark (default, the new look) | `<html class="doc-mode-dark">` | Page `--color-bg`, panels `--color-surface`, text `--color-text`, muted `--color-text-muted`, orange `--color-brand`. Backgrounds print through `print-color-adjust: exact`. Header logo: `../assets/logo-horiz-ON-DARK.png`. |
| Paper (print variant, saves ink) | `<html class="doc-mode-paper">` or `?mode=paper` | White paper, ink `#0b0b0c` (the brand's bg colour), muted `#5f5f64`, hairlines `--color-bg` at 14% (table-header and subtotal rules at 22%), panels tinted `#f5f5f4` (`--color-text`, aliased as `--doc-paper-panel`). Header logo: `../assets/logo-pack-2026/svg/p09-wordmark-360vision-on-light.svg`. |

**Paper mode is a proposal, not an observed value.** The live site declares no light theme (DESIGN.md §9), so the paper values are derived from the owner's own light documents and ON-LIGHT logos. They are declared once, as `--doc-paper-*` properties at the top of `document.css`.

**Owner decision: one lockup or two.** As specified, dark mode uses the horizontal lockup (ring mark, divider, VISION/EVENTS) and paper mode uses the P09 wordmark ("360VISION" over EVENTS, no ring). At the same 9 mm height they differ in width (about 23 mm against 32 mm), so the two modes carry slightly different identities. If one lockup is wanted in both, paper mode can use `../assets/logo-pack-2026/svg/p03-primary-horizontal-divider-on-light.svg` instead; its ring is a bitmap a touch lighter than `#ff4000` (DESIGN.md §9), which does not show at 9 mm. Neither file is ever recoloured.

**Contrast, both modes (WCAG 2.x, normal text ≥ 4.5:1):**

| Pair | Dark | Paper |
|---|---|---|
| Ink on page | 18.0:1 | 19.7:1 |
| Muted on page | 5.7:1 | 6.3:1 |
| Muted on panel | 5.05:1 | 5.8:1 |
| Orange text on page / panel | 5.6:1 / 4.95:1 | not used for small text |

`#ff4000` on white is only 3.5:1, so in paper mode orange is kept to rules, bars, the 2px markers and the 24px section numbers (bold display ≥ 18.66px needs 3:1). Small eyebrow text switches to ink with a short orange marker in front.

## Page model

- `@page { size: A4; margin: 0 }`. Side margins are 16 mm; 12 mm above the header and below the footer.
- **Running header and footer on every printed page.** The document sits inside one frame table (`.doc-frame`) whose `thead` and `tfoot` hold empty spacers the height of the header and footer; Chrome and Edge repeat those on every page. The real header and footer are `position: fixed` in print, so they also print on every page. On screen they sit in the flow and the spacers are hidden.
- Line-item tables repeat their column header after a page break. Rows, panels, the totals box, the acceptance block and the payment/banking block (with its closing line) never split; section headings, group header rows and sub-heads stay with what follows; a subtotal row stays with the last item above it; a spec list never leaves a single row alone at a page edge. The air between line-item groups sits under each subtotal, so a group that opens a new page sits flush under the repeated header.
- A group that breaks across pages continues under the repeated column header without repeating its group row; its subtotal row names the group.
- On screen the document is a 210 mm sheet on a slightly darker backdrop. On phones the layout becomes one column and the line-item table scrolls sideways inside its own wrapper (`.doc-lines-wrap`).

The technique relies on Chromium print behaviour. Firefox and Safari may not repeat the header and footer; use Chrome or Edge for PDFs.

## Quotation — structure

| # | Section | Fields | Optional |
|---|---|---|---|
| 1 | Title block | Badge · eyebrow "Official event proposal & quotation" · H1 "Quotation." · meta list: Reference, Date of issue, Date of event, Client vendor no., Tax basis | Client vendor no. |
| 2 | Event title | H2 "[Guest count]-guest [event type] — [Client company]" · muted subline (tax format) · rule | — |
| 3 | Parties | **Prepared for:** client company, client vendor no., tax basis, region · **Prepared by:** "[Contact name] · 360 Vision Events (PTY) Ltd", role, "[Phone] · [E-mail]" | Client vendor no. |
| 4 | Project details and total | Key/value: Project title ("[Client company] · [Event title]"), Date of event, Venue, Service provider, Reference, Production cycle · amount hero: "Total commercial investment", amount, tax note | — |
| 5 | 01 Brief and commercial terms. | 1–2 brief paragraphs · "Commercial terms & inclusions": Total commercial investment, Taxation terms, Scope inclusions, Site exclusions / venue provisions | — (the brief is 1–2 paragraphs) |
| 6 | 02 Service and infrastructure specification. | Sub-sections A, B, C ("A · [Category]") with spec rows (item · description); a sub-section may use a bullet list instead (C does) | — (as many sub-sections and rows as the job needs) |
| 7 | 03 Quotation schedule. | Line-item table (# · Qty · Description · Unit rate · Total) in groups, each with a group header row and a subtotal row · totals box: one row per group, Subtotal, VAT, "Total commercial investment (non-VAT)" or "(incl. VAT)" | Subtotal (shown only when VAT is charged) |
| 8 | 04 Client acceptance. | Total restated · sign-and-return instruction with `[E-mail]` · signature grid: Client acceptance (signature), Full name, Designation, Date, Purchase order number · "Service provider details": Company, Client vendor no., Bank, Account name, Account number ("On file · stated on the proforma invoice"), Branch code, Contact · terms sentence · "Thank you for your business." | Client vendor no. |

## Proforma invoice — structure

| # | Section | Fields | Optional |
|---|---|---|---|
| 1 | Title block | Badge · eyebrow "Issued for PO processing & payment authorisation" · H1 "Proforma invoice." · meta list: Proforma no., Date of issue, Quotation ref., Client vendor no., Client PO no. ("To be inserted on receipt"), Payment terms ("100% before the event") | Client vendor no. |
| 2 | Parties | **Bill to:** client company, client vendor no., tax basis, region · **From:** 360 Vision Events (PTY) Ltd, "[Contact name] · [Role]", "[Phone] · [E-mail]" | Client vendor no. |
| 3 | RE line | "RE: [Client company] · [Event title] — [Date of event] · Turnkey event production as per quotation [Quote reference]" | — |
| 4 | Event details and amount due | Key/value: Project title ("[Client company] · [Event title]"), Date of event, Venue, Guests, Production cycle, Power, Tax basis · amount hero "Amount due" with the payment-reference note | — |
| 5 | Coverage | "This proforma covers" · "Excluded · venue provisions" | — |
| 6 | Line items | Same table and groups as the quotation | — |
| 7 | Totals box | Subtotal, VAT, "Total due" | — |
| 8 | Payment and banking | **Payment:** the amount to pay (the grand total) with the EFT instruction, payment terms, where to send proof of payment and the PO, not-a-tax-invoice note · **Banking details:** Account name, Bank, Branch code, Account no., Account type, SWIFT, Reference, Client vendor no. · "Thank you for your business." under the banking panel | Client vendor no. |

Block titles are real headings, styled as eyebrows: in the quotation the event title and sections 01–04 are `h2` and the panel titles and A/B/C sub-sections are `h3`; in the proforma every block title is an `h2` under the `h1`. Keep the heading level when you add a block, so the PDF's heading outline stays intact.

## Filling in a template

1. **Work on a copy that git ignores.** Save it next to the template (the relative `../tokens.css` and `../assets/` links must keep working) under a name ending in `.filled.html`, such as `quote-client-name.filled.html`. This folder's `.gitignore` already ignores `*.filled.html`, every `*.pdf` and a `filled/` folder, so filled copies and the PDFs you print stay out of git; `git check-ignore -v <file>` confirms it for a given file. If you use the templates anywhere else (for example the copy bundled with the Claude skill), keep this `.gitignore` next to them, or add the same three patterns to your project's own `.gitignore`, before you fill anything in. Or fill the template in the browser's developer tools, print to PDF and discard the edits.
2. **Replace every `[Bracket placeholder]`.** Search the file for `[`. Typical fields: `[Client company]`, `[Vendor number]`, `[Region]`, `[Contact name]`, `[Role]`, `[Phone]`, `[E-mail]`, `[Quote reference]`, `[Proforma number]`, `[Date of issue]`, `[Date of event]`, `[Venue]`, `[Town]`, `[Province]`, `[Bank]`, `[Account name]`, `[Account number]`, `[Account type]`, `[Branch code]`, `[SWIFT code]`, `[Registration number]`, `[Business address]`.
3. **Remove what does not apply.** Rows and lines marked `data-optional` can be deleted whole.
4. **Remove the sample badge** (`<span class="doc-badge">`) before sending a real document.
5. **Write in the house voice** (DESIGN.md §7): UK/South African spelling, sentence case (uppercase comes from CSS), spaced em dashes and middots, no exclamation marks, section headings that end with a full stop, and no invented claims or figures.

### Line items

Each group is a `<tbody class="doc-line-group" data-group="N">` holding a group header row, item rows and a subtotal row. An item row carries its quantity and unit rate as data:

```html
<tr class="doc-line-item" data-qty="2" data-rate="25000">
  <td class="doc-line-ref">1.1</td>
  <td class="doc-num doc-qty" data-line-qty>2</td>
  <th scope="row">Stretch tent structure, rigged</th>
  <td class="doc-num doc-line-rate" data-line-rate>R&nbsp;25&nbsp;000.00</td>
  <td class="doc-num" data-line-total>R&nbsp;50&nbsp;000.00</td>
</tr>
```

The description is the row header (`<th scope="row">`), styled as a plain cell, so a screen reader names the item when it reads a rate or total. `data-rate` is in rand, without spaces or "R" (`6500`, `20`, `1250.50`). To add a group, copy a whole `tbody`, give it the next `data-group` number, and add a matching `data-group-subtotal="N"` row to the quotation's totals box.

### VAT

Set it once on the root element:

- `<html … data-vat="none">`: the VAT row reads "Not applicable · all-inclusive, non-VAT" and the total equals the subtotal.
- `<html … data-vat="15">`: adds 15% VAT, shows the VAT amount and adds it to the total. The quotation's totals box then also shows the subtotal the VAT is charged on.

Every tax wording that depends on this (tax basis, sublines, notes, the VAT label, the "(non-VAT)" / "(incl. VAT)" qualifier on the grand total) carries a `data-vat-text` element with `data-vat-none` and `data-vat-rated` wording; `{rate}` is replaced by the rate. Rows marked `data-vat-only` are hidden by CSS unless VAT is charged.

## How totals work

A small inline script (no dependencies) runs on load and works in cents, so there are no floating-point errors:

1. Row total = `data-qty` × `data-rate`, rounded to the cent; it also rewrites the row's quantity and unit rate.
2. Group subtotal = sum of its rows, written to every `[data-group-subtotal="N"]` (the table's subtotal row and the quotation's totals box).
3. Subtotal = sum of the groups (`[data-subtotal]`).
4. VAT = subtotal × rate ÷ 100, rounded to the cent (`[data-vat-amount]`), or the not-applicable wording.
5. Grand total = subtotal + VAT, written to every `[data-grand-total]`: the amount hero, the totals box, the quotation's commercial terms and acceptance line, and the proforma's payment line.

Amounts are formatted the South African way, as in the old documents: `R 12 345.00`, with non-breaking spaces after "R" and between thousands, and a point before the cents.

The HTML also ships the correct values pre-rendered, so the document reads correctly with JavaScript off. If you change quantities or rates, either let the script recompute (any modern browser, including the print path) or update the visible figures too.

**Sample figures (data-vat="none"):** Tentage & seating R 100 000.00 + Technical production, audio & staging R 80 000.00 + Production staff & event management R 40 000.00 = R 220 000.00. With `data-vat="15"`: VAT R 33 000.00, total R 253 000.00.

## Class inventory

| Component | Classes |
|---|---|
| Modes | `doc-mode-dark`, `doc-mode-paper` (on `<html>`) |
| Page model | `doc-sheet`, `doc-frame`, `doc-header-space`, `doc-footer-space` |
| Header | `doc-header`, `doc-header-row`, `doc-logo`, `doc-logo--dark`, `doc-logo--paper`, `doc-header-tagline`, `doc-header-subline`, `doc-accent-rule` |
| Footer | `doc-footer`, `doc-footer-row` |
| Type | `doc-eyebrow`, `doc-eyebrow-display`, `doc-badge`, `doc-title`, `doc-muted`, `doc-note`, `doc-nowrap`, `doc-sr-only` (screen-reader-only text) |
| Title block | `doc-title-block`, `doc-meta`, `doc-meta-row` |
| Event title | `doc-event`, `doc-event-title`, `doc-event-subline`, `doc-rule` |
| Layout | `doc-grid-2`, `doc-block`, `doc-keep`, `doc-panel` |
| Parties | `doc-party-name`, `doc-party-lines` |
| Key/value list | `doc-kv`, `doc-kv-row` |
| Amount hero | `doc-amount`, `doc-amount-value`, `doc-amount-note` |
| RE line | `doc-re` |
| Sections | `doc-section`, `doc-section-title`, `doc-section-num`, `doc-subhead`, `doc-prose` |
| Spec and definition rows | `doc-spec`, `doc-spec-row` |
| Bullet list | `doc-bullets` |
| Line-item table | `doc-lines-wrap`, `doc-lines`, `doc-col-ref`, `doc-col-qty`, `doc-col-money`, `doc-line-group`, `doc-line-group-head`, `doc-line-item`, `doc-line-ref`, `doc-qty`, `doc-line-rate`, `doc-num`, `doc-line-subtotal` |
| Totals box | `doc-totals`, `doc-totals-row`, `doc-totals-row--grand` |
| Acceptance | `doc-accept`, `doc-accept-total`, `doc-accept-note`, `doc-signatures`, `doc-sign`, `doc-sign--full`, `doc-sign-label`, `doc-terms`, `doc-closing` |
| Toolbar (screen only) | `doc-toolbar`, `doc-toolbar-modes`, `doc-toolbar-chip`, `doc-toolbar-print`, `doc-toolbar-note` |

Data hooks: `data-vat`, `data-group`, `data-qty`, `data-rate`, `data-line-qty`, `data-line-rate`, `data-line-total`, `data-group-subtotal`, `data-subtotal`, `data-vat-amount`, `data-grand-total`, `data-vat-text` (+ `data-vat-none`, `data-vat-rated`), `data-vat-only`, `data-optional`, `data-set-mode`, `data-print`.

**Design-system fidelity.** Colours, families, sizes, spaces, radii and shadows come from `tokens.css` variables. Print-only values (A4 geometry in mm, two print type sizes, column widths, two marker offsets, the paper-mode colours and the screen backdrops) are declared once as `--doc-*` properties at the top of `document.css`, each with its reason. Reused site patterns: the tracked eyebrow and display eyebrow, `--color-border` hairlines (`--color-input` for the table-header and subtotal rules), surface panels at `--radius-lg`, the 2px brand accent bar, the CTA-band `--color-brand-border`, and the CONCEPT · MOCK badge (as "Sample · Template"). Fonts are the site's own Google Fonts request.

Deliberate exceptions, so they are not mistaken for drift:

- **Literal colours.** `#ffffff` (paper ground) and `#5f5f64` (paper muted) are paper-mode proposals; `#000` appears once, in the screen-only dark backdrop (`--doc-dark-backdrop`), and is the same black the `--shadow-*` tokens are built from.
- **Plain key/value and totals labels.** The site sets `<dt>` labels in tracked caps (caps-18). The documents keep that for the title-block meta list, the table header and the eyebrows, but set key/value labels (Project details, Event details, Service provider details, Banking details) and totals labels in muted sentence case, untracked, as the old documents did: long labels such as "Technical production, audio & staging" stay on one line in the narrow label columns and read faster in print. Signature-line labels follow the same rule, so no tracked label is ever left in mixed case.
- **Signature lines** are drawn in the muted text colour, not a hairline, so they are firm enough to sign on when printed.

## Privacy

This repository is public. **Never commit real client, personal or banking details**, and never commit a filled-in copy of either template:

- client names, vendor numbers, venues and addresses;
- personal names, phone numbers and e-mail addresses;
- the company registration number and street address;
- bank, account name, account number, branch code and SWIFT;
- quote and proforma references, prices, totals and event dates.

Keep filled copies and their PDFs outside version control (see [Filling in a template](#filling-in-a-template)); this folder's `.gitignore` ignores `*.filled.html`, `*.pdf` and `filled/`, but it cannot protect a filled copy saved under the template's own name, so never type real details into `quotation.html` or `proforma-invoice.html` themselves. Only "360 Vision Events (PTY) Ltd" and the domain `360-vision-events.co.za`, which are already public in the design system, appear in the templates.

## What changed from the old layout

- **Paper:** US Letter → A4 (210 × 297 mm), with 16 mm side margins.
- **Type:** condensed display caps and Karla → Space Grotesk (bold, -.03em) for display and Inter Tight for body, with Inter only for the badge; the site's own font request.
- **Colour:** a light page by default → the dark site look by default, with an optional ink-saving paper mode.
- **Header:** the segmented orange-to-grey bar → one 2px brand accent bar that continues as a hairline; the tagline is now "Corporate & brand event production" over "Audio · Lighting · Visual · Digital experience".
- **Headings:** uppercase tracked section titles → short sentence-case display headings that end with a full stop, numbered in brand orange ("01 Brief and commercial terms.").
- **Blocks:** plain text blocks → surface panels for the parties, provider details and banking; the total gets an amount hero with a brand top edge.
- **Line items:** orange tracked group titles → panel-tinted group rows with a 2px brand marker; numbers in tabular figures.
- **Pagination:** running header and footer on every page, a repeating table header, and break rules that keep headings and group header rows with the rows that follow and a subtotal with its last item.
- **Totals:** typed figures → computed from quantity × rate, with a switchable VAT mode; pre-rendered values kept for readers without JavaScript.
- **Contacts:** several personal addresses and numbers in the body → one `[Phone]` and `[E-mail]` placeholder per slot.
- **Closing line:** "Thank you for your business." in the display eyebrow style.
- **Sample marking:** a "Sample · Template" badge in the title block, reusing the site's CONCEPT · MOCK badge.
