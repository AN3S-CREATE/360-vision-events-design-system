# 360 Vision Events — Design System (evidence-locked)

Generated 2026-10-02T14:11:01Z from the live public site. 113 tokens: 3 absent, 0 inferred, all others observed. They trace to 738 verified observations in `evidence.json`.

---

## 1. Brand name as shown on the site

- **Name in UI:** "360 Vision Events". It appears in:
  - the logo `alt` on all 9 pages;
  - the logo link `aria-label` "360 Vision Events home";
  - `meta[name=author]`;
  - JSON-LD `Organization.name`;
  - the contact-card heading on /contact.

  *(voc-bn-01, -02, -03, -05, -14)*
- **Legal form:** "360 Vision Events (PTY) Ltd trading as 360 Vision Events". It appears in JSON-LD `legalName`, the home copyright line and the compact footers. *(voc-bn-04, -07, -08)*
- **Domain:** the hyphenated `360-vision-events.co.za`, which is the canonical URL on every page. Social handles use `360visionevents`. *(voc-bn-11, voice-miss-13)*
- **Logo:** a raster PNG only, `logo-horiz-ON-DARK.png`: 1176×452, RGBA, transparent background. The same file sits in the header on every page.
  - **What it shows:** "360" inside an orange aperture/shutter ring, a thin vertical divider, "VISION" in wide caps, and "EVENTS" in letter-spaced grey caps below. *(voc-bn-09, col-144)*
  - **Pixel sample:** of the opaque pixels, `#ff4000` is 54.93% and is an exact match for `--primary`. The white "VISION" wordmark is `#ffffff` (28.25%) and the grey "EVENTS" lettering is `#a6a6a6` (2.71%). *(col-145, col-148)*
  - **Favicon:** a 64×64 PNG with the orange ring and "360" only. `#ff4000` is its most frequent exact colour (26.92% of opaque pixels); the rest are resampled near-variants such as `#ff4400` and `#ff4200`. *(col-147, col-149)*
- **Official logo pack (supplied by the brand owner, 2026):** 11 PNGs in `assets/logo-pack-2026/` *(D26)*. Each design comes in ON-DARK and ON-LIGHT versions; P12 has only ON-DARK.
  - Designs: primary horizontal with divider (P03, P05, P12), stacked full colour (P06), the 360 mark (P07), and the 360VISION wordmark (P09).
  - Format: every file is 2000×2000 on a solid ground, pure black `#000000` or white `#ffffff`. They are not transparent.
  - Orange varies by file: P12 `#ff3e00`, P07 `#ff3500`, P03 `#fb1c00`, P06 `#f51900`, P05 `#e22500`, and the P09 wordmark's "360" is `#f14624`. The UI brand colour stays the site's `#ff4000`; see §9.
  - **SVGs (`assets/logo-pack-2026/svg/`, ON-LIGHT only)** *(D27)*:
    - All five are transparent, and their vector lettering is exactly `#ff4000`.
    - The P09 wordmark is fully vector.
    - P03, P05, P06 and P07 draw the aperture ring as a masked bitmap (400–850 px, about `#ff4e23`–`#ff5636`).
- **Not declared:** `og:site_name`. *(voc-bn-10)*

## 2. Source URL and redirect chain

| Step | URL | Result |
|---|---|---|
| 1 | `https://360visionevents.co.za` (user-supplied) | `302 Found`, `Location: https://360-vision-events.co.za/`, 0 bytes |
| 2 | `https://360-vision-events.co.za/` | `200`, `text/html`, 69,623 bytes of server-rendered HTML; one stylesheet built with Tailwind CSS v4.3.3 (licence banner, orc-02) |

**Pages read.** All were same-host GETs on 2026-10-02 between 05:44 and 05:49 UTC, with no failures and no retries:
- `/` (home)
- `/work`
- `/portfolio` → `307` → `/portfolio?client=`
- `/services`
- `/insights`
- `/booking`
- `/plan-my-event`
- `/about`
- `/contact`

**Assets read:**
- `/assets/styles-BQycqoql.css` (94,546 bytes)
- the header logo PNG
- `/favicon.png`

**Not fetched:**
- **Google Fonts stylesheet:** a third-party host; its `<link>` declaration counts as evidence instead.
- **Script chunks:** 31 distinct chunks and the first-party analytics script `/~flock.js`, not loaded because the HTML and compiled CSS already contain every rendered class.
- **Routes outside the 8-page main-nav cap:** footer-only and detail pages.
- **`/follow-ups`:** linked as "Team login", so never scraped.

**Precedence applied.** The user URL serves only a redirect, so every value comes from the redirected host. The rule used is "a redirected host beats inference" (decision D02). No two sources disagreed, and no inferred value overwrote an observation.

### Package files and value conventions

| File | Purpose |
|---|---|
| `tokens.json` | DTCG-style tokens: `$type`, `$value`, `$description`, plus `$extensions` with `mode`, `source_url`, `selector`, `observation_ids`, `usage_count`, and `declared`/`resolved_vars` where a value was resolved |
| `tokens.css` | The same tokens as CSS custom properties, one-for-one. The name is `--` + token path with `.` replaced by `-`. Absent tokens are declared as `initial` |
| `evidence.json` | Fetch log, redirect chain, page list, observations, decisions, flags, token trace, quality assurance, events |
| `DESIGN.md` | This spec |
| `preview.html` | Optional extra: a one-page component preview built only from `tokens.css` variables (see Optional extras) |
| `templates/` | Optional extra: A4 quotation and proforma-invoice templates in this system's look, with a structure README *(D28)* |
| `assets/` | Byte-identical copies of the site's logo PNG and favicon (optional extra), plus `logo-pack-2026/`: the official logo files supplied by the brand owner, with a README mapping each to its official name, background and orange |

**How values are written:**
- **Numbers:** number tokens are JSON numbers. Line-height `calc()` ratios are evaluated, and the authored form is kept in `$extensions.declared`.
- **Easing:** cubic-bezier tokens are 4-number arrays.
- **CSS strings:** colour, dimension, duration, shadow and gradient values stay as the site's own CSS strings (`oklch(...)`, `color-mix(...)`, multi-layer shadows), so nothing is converted between colour spaces or units.
- **Resolved references:** where the site wrote `var(--x)`, the token holds the observed `:root` value. The original stays in `$extensions.declared` and the substitution in `$extensions.resolved_vars`.
- **Radius:** radius steps keep `calc()` because they mix rem and px.
- **Pixel sizes:** pixel equivalents assume a 16px root.
- **Usage counts:** `usage_count` counts a class across the 9 pages, including its responsive (`sm:`/`md:`/`lg:`) and `file:` variants. Interactive-state variants (`hover:`, `focus:`, `placeholder:` and so on) are left out, except for state tokens such as hover, focus and ring, and wherever `$extensions.note` names them.

## 3. Colour

One dark palette is declared in a single unlayered `:root` block of `styles.css`. There is no light theme, no `.dark` toggle and no `prefers-color-scheme` rule *(col-129–col-132)*. The HTML has no inline colours or hex values: every colour comes from the semantic variables below *(col-128, col-142)*.

**Most-used plain colour classes** (state variants such as `hover:` excluded):

| Class | Uses |
|---|---|
| `border-border` | 324 |
| `text-muted-foreground` | 257 |
| `bg-card` | 254 |
| `text-primary` | 254 |
| `text-foreground` | 42 |
| `bg-primary` | 39 |

The most-used state variants are `hover:text-foreground` (110), `hover:text-primary` (81) and `focus-visible:ring-ring` (68).

| Token | CSS variable | Value | Mode | Source selector | Uses | Notes |
|---|---|---|---|---|---|---|
| `color.bg` | `--color-bg` | `#0b0b0c` | observed | `:root { --background }` | 15 | Page canvas. Body background via --color-background; base of every image scrim. |
| `color.surface` | `--color-surface` | `#1a1a1c` | observed | `:root { --surface } (= --card, --popover)` | 266 | Raised surface: cards (bg-card), bands, CTA panels, home footer. --surface, --card and --popover share this value. (usage = bg-card 254 + bg-surface 12) |
| `color.surface-2` | `--color-surface-2` | `#242426` | observed | `:root { --surface-2 } (= --secondary, --muted)` | 2 | Secondary-button fill (the two form-submit buttons). --surface-2, --secondary and --muted share this value; no element renders it as a page or card surface. (usage = bg-secondary 2; bg-surface-2 and bg-muted compiled but unused) |
| `color.surface-2-hover` | `--color-surface-2-hover` | `color-mix(in oklab, #242426 80%, transparent)` | observed | `@media (hover:hover) .hover\:bg-secondary\/80:hover (@supports color-mix)` | 2 | Secondary (form-submit) button hover. Declared: `color-mix(in oklab, var(--secondary) 80%, transparent)`. (hover:bg-secondary/80 (state token)) |
| `color.text` | `--color-text` | `#f5f5f4` | observed | `:root { --foreground }` | 60 | Default text. Also --card-foreground, --popover-foreground, --secondary-foreground. (text-foreground 42 + file:text-foreground 18; body inherits it everywhere; hover:text-foreground 110 is a state variant, not counted) |
| `color.text-muted` | `--color-text-muted` | `#8a8a8e` | observed | `:root { --muted-foreground }` | 257 | Supporting copy, nav links, card bodies, placeholders. (text-muted-foreground 257; placeholder: 21 and data-[placeholder]: 4 are state variants, not counted) |
| `color.brand` | `--color-brand` | `#ff4000` | observed | `:root { --primary }` | 293 | Brand orange: CTA fills, eyebrows/kickers, text links, focus ring. Exactly the flat fill of the logo mark, and the favicon's most frequent exact colour. (text-primary 254 + bg-primary 39; hover:text-primary 81 and group-hover:text-primary 1 are state variants, not counted) |
| `color.brand-hover` | `--color-brand-hover` | `color-mix(in oklab, #ff4000 90%, transparent)` | observed | `@media (hover:hover) .hover\:bg-primary\/90:hover (@supports color-mix)` | 29 | Primary button hover fill (bg-primary at 90%). Declared: `color-mix(in oklab, var(--primary) 90%, transparent)`. (hover:bg-primary/90 (state token)) |
| `color.brand-border` | `--color-brand-border` | `color-mix(in oklab, #ff4000 35%, transparent)` | observed | `.border-primary\/35 (@supports color-mix)` | 7 | Orange hairline around CTA bands (border-primary/35). Declared: `color-mix(in oklab, var(--primary) 35%, transparent)`. |
| `color.brand-border-hover` | `--color-brand-border-hover` | `color-mix(in oklab, #ff4000 45%, transparent)` | observed | `.card-lift:hover (@supports color-mix)` | 105 | Card border on hover (.card-lift:hover). Declared: `color-mix(in oklab, var(--primary) 45%, transparent)`. |
| `color.accent` | `--color-accent` | `#ff4000` | observed | `:root { --accent }` | 12 | Declared --accent. Identical to color.brand; used only as the outline-button hover fill. The site has no second accent hue. (usage = hover:bg-accent 12) |
| `color.on-brand` | `--color-on-brand` | `#0b0b0c` | observed | `:root { --primary-foreground } (= --accent-foreground)` | 34 | Text/icon colour on brand orange (dark on orange). Also --accent-foreground. |
| `color.bg-overlay` | `--color-bg-overlay` | `color-mix(in oklab, #0b0b0c 80%, transparent)` | observed | `.bg-background\/80 (@supports color-mix)` | 9 | Translucent sticky-header fill (bg-background/80) under backdrop-blur. Declared: `color-mix(in oklab, var(--background) 80%, transparent)`. |
| `color.border` | `--color-border` | `oklch(100% 0 0/.12)` | observed | `:root { --border }` | 324 | Default border colour (set on * in the base layer), white at 12%; the 1px width comes from the border/border-t/border-b/border-y utilities. |
| `color.input` | `--color-input` | `oklch(100% 0 0/.16)` | observed | `:root { --input }` | 37 | Form-field and outline-button border: white at 16%. |
| `color.ring` | `--color-ring` | `#ff4000` | observed | `:root { --ring }` | 72 | Focus ring colour (focus-visible:ring-ring). (focus-visible:ring-ring 68 + focus:ring-ring 4 (state token)) |
| `color.destructive` | `--color-destructive` | `oklch(60% .22 25)` | observed | `:root { --destructive }` | 0 | Declared error/destructive colour. Compiled utilities exist but no fetched page renders it. |
| `color.on-destructive` | `--color-on-destructive` | `#fff` | observed | `:root { --destructive-foreground }` | 0 | Declared text colour on destructive. Not rendered on any fetched page. |
| `color.success` | `--color-success` | `null` | absent | `:root and utilities` |  | No success colour is declared in styles.css or used on any fetched page. |
| `color.warning` | `--color-warning` | `null` | absent | `:root and utilities` |  | No warning colour is declared in styles.css or used on any fetched page. |
| `color.info` | `--color-info` | `null` | absent | `:root and utilities` |  | No info colour is declared in styles.css or used on any fetched page. |

**Contrast of pairs that occur on the site.** These ratios are derived, not observed: they are computed (WCAG 2.x) from the observed hex values and back usage rule 3.

| Pair | Ratio |
|---|---|
| text `#f5f5f4` on bg | 18.03:1 |
| text `#f5f5f4` on surface | 15.93:1 |
| text-muted `#8a8a8e` on bg | 5.72:1 |
| text-muted `#8a8a8e` on surface | 5.05:1 |
| brand `#ff4000` on bg | 5.61:1 |
| brand `#ff4000` on surface | 4.95:1 |
| on-brand `#0b0b0c` on brand | 5.61:1 |
| white on brand (for comparison; the site never uses it) | 3.51:1 |

## 4. Typography

**Three families are rendered:**
- **Inter Tight** for body text.
- **Space Grotesk** for h1–h3, through the base rule `h1,h2,h3{font-family:var(--font-display);letter-spacing:-.03em}`, and for `.font-display` labels.
- **Inter**, from the custom `.font-clean` utility. It overrides the base heading rule on:
  - 6 of the 9 page h1s (/work, /portfolio, /services, /insights, /plan-my-event, /about);
  - 14 of 33 h2s;
  - 8 of 116 h3s.

*(typ-07, typ-09, typ-85)*

There are no `@font-face` rules. All three families load from one Google Fonts `<link>`, identical on every page: `Inter:wght@400;500;600;700`, `Space+Grotesk:wght@500;700`, `Inter+Tight:wght@400;500;600`, `display=swap` *(typ-15, typ-20)*. The base line-height is 1.5 (`html`), and body text is antialiased.

| Token | CSS variable | Value | Mode | Source selector | Uses | Notes |
|---|---|---|---|---|---|---|
| `font.family.display` | `--font-family-display` | `"Space Grotesk", "Helvetica Neue", sans-serif` | observed | `@layer theme :root,:host { --font-display }` |  | Headings h1-h3 (base rule) and .font-display labels. Loaded from Google Fonts (<link>, weights 500;700). |
| `font.family.body` | `--font-family-body` | `"Inter Tight", system-ui, sans-serif` | observed | `@layer theme :root,:host { --font-sans }` |  | Body text (base body rule via --font-sans / --default-font-family). Loaded from Google Fonts (weights 400;500;600). |
| `font.family.clean` | `--font-family-clean` | `Inter,system-ui,sans-serif` | observed | `@layer utilities .font-clean` | 43 | Third family set by the custom .font-clean utility (not a theme variable). Used on 6 of 9 hero h1s, some h2/h3s and eyebrows. Loaded from Google Fonts (weights 400;500;600;700). |
| `font.size.2xs` | `--font-size-2xs` | `.68rem` | observed | `.text-\[0\.68rem\]` | 3 | Arbitrary text-[0.68rem]; only the CONCEPT · MOCK badge on /services. |
| `font.size.xs` | `--font-size-xs` | `.75rem` | observed | `@layer theme :root,:host { --text-xs }` | 176 | Tailwind theme --text-xs. |
| `font.size.sm` | `--font-size-sm` | `.875rem` | observed | `@layer theme :root,:host { --text-sm }` | 516 | Tailwind theme --text-sm. (text-sm 477 + md:text-sm 21 + file:text-sm 18) |
| `font.size.base` | `--font-size-base` | `1rem` | observed | `@layer theme :root,:host { --text-base }` | 41 | Tailwind theme --text-base. |
| `font.size.lg` | `--font-size-lg` | `1.125rem` | observed | `@layer theme :root,:host { --text-lg }` | 10 | Tailwind theme --text-lg. (text-lg 8 + sm:text-lg 2) |
| `font.size.xl` | `--font-size-xl` | `1.25rem` | observed | `@layer theme :root,:host { --text-xl }` | 44 | Tailwind theme --text-xl. (text-xl 43 + sm:text-xl 1) |
| `font.size.2xl` | `--font-size-2xl` | `1.5rem` | observed | `@layer theme :root,:host { --text-2xl }` | 67 | Tailwind theme --text-2xl. |
| `font.size.3xl` | `--font-size-3xl` | `1.875rem` | observed | `@layer theme :root,:host { --text-3xl }` | 16 | Tailwind theme --text-3xl. |
| `font.size.4xl` | `--font-size-4xl` | `2.25rem` | observed | `@layer theme :root,:host { --text-4xl }` | 11 | Tailwind theme --text-4xl. (text-4xl 7 + sm:text-4xl 4) |
| `font.size.5xl` | `--font-size-5xl` | `3rem` | observed | `@layer theme :root,:host { --text-5xl }` | 11 | Tailwind theme --text-5xl. (text-5xl 8 + sm:text-5xl 3) |
| `font.size.6xl` | `--font-size-6xl` | `3.75rem` | observed | `@layer theme :root,:host { --text-6xl }` | 2 | Tailwind theme --text-6xl. Used only at sm (>=40rem) and up. (sm:text-6xl only) |
| `font.size.7xl` | `--font-size-7xl` | `4.5rem` | observed | `@layer theme :root,:host { --text-7xl }` | 7 | Tailwind theme --text-7xl. Used only at sm (>=40rem) and up. (sm:text-7xl only) |
| `font.line-height.xs` | `--font-line-height-xs` | `1.333333` | observed | `@layer theme :root,:host { --text-xs--line-height }` |  | Line height paired with font.size.xs (--text-xs--line-height), evaluated from the declared expression. Declared: `calc(1 / .75)`. |
| `font.line-height.sm` | `--font-line-height-sm` | `1.428571` | observed | `@layer theme :root,:host { --text-sm--line-height }` |  | Line height paired with font.size.sm (--text-sm--line-height), evaluated from the declared expression. Declared: `calc(1.25 / .875)`. |
| `font.line-height.base` | `--font-line-height-base` | `1.5` | observed | `@layer theme :root,:host { --text-base--line-height }` |  | Line height paired with font.size.base (--text-base--line-height), evaluated from the declared expression. Declared: `calc(1.5 / 1)`. |
| `font.line-height.lg` | `--font-line-height-lg` | `1.555556` | observed | `@layer theme :root,:host { --text-lg--line-height }` |  | Line height paired with font.size.lg (--text-lg--line-height), evaluated from the declared expression. Declared: `calc(1.75 / 1.125)`. |
| `font.line-height.xl` | `--font-line-height-xl` | `1.4` | observed | `@layer theme :root,:host { --text-xl--line-height }` |  | Line height paired with font.size.xl (--text-xl--line-height), evaluated from the declared expression. Declared: `calc(1.75 / 1.25)`. |
| `font.line-height.2xl` | `--font-line-height-2xl` | `1.333333` | observed | `@layer theme :root,:host { --text-2xl--line-height }` |  | Line height paired with font.size.2xl (--text-2xl--line-height), evaluated from the declared expression. Declared: `calc(2 / 1.5)`. |
| `font.line-height.3xl` | `--font-line-height-3xl` | `1.2` | observed | `@layer theme :root,:host { --text-3xl--line-height }` |  | Line height paired with font.size.3xl (--text-3xl--line-height), evaluated from the declared expression. Declared: `calc(2.25 / 1.875)`. |
| `font.line-height.4xl` | `--font-line-height-4xl` | `1.111111` | observed | `@layer theme :root,:host { --text-4xl--line-height }` |  | Line height paired with font.size.4xl (--text-4xl--line-height), evaluated from the declared expression. Declared: `calc(2.5 / 2.25)`. |
| `font.line-height.5xl` | `--font-line-height-5xl` | `1` | observed | `@layer theme :root,:host { --text-5xl--line-height }` |  | Line height paired with font.size.5xl (--text-5xl--line-height), evaluated from the declared expression. |
| `font.line-height.6xl` | `--font-line-height-6xl` | `1` | observed | `@layer theme :root,:host { --text-6xl--line-height }` |  | Line height paired with font.size.6xl (--text-6xl--line-height), evaluated from the declared expression. |
| `font.line-height.7xl` | `--font-line-height-7xl` | `1` | observed | `@layer theme :root,:host { --text-7xl--line-height }` |  | Line height paired with font.size.7xl (--text-7xl--line-height), evaluated from the declared expression. |
| `font.leading.display` | `--font-leading-display` | `0.95` | observed | `.leading-\[0\.95\]{--tw-leading:.95;line-height:.95}` | 6 | leading-[0.95]: 6 of 9 page h1s. |
| `font.leading.none` | `--font-leading-none` | `1` | observed | `.leading-none{--tw-leading:1;line-height:1}` | 28 | leading-none: labels, /booking and /contact h1. |
| `font.leading.tight` | `--font-leading-tight` | `1.25` | observed | `@layer theme :root,:host { --leading-tight } (via .leading-tight)` | 4 | leading-tight (--leading-tight). |
| `font.leading.snug` | `--font-leading-snug` | `1.375` | observed | `@layer theme :root,:host { --leading-snug } (via .leading-snug)` | 1 | leading-snug (--leading-snug). |
| `font.leading.normal` | `--font-leading-normal` | `1.5` | observed | `@layer base { html,:host }` |  | Document default line-height (html, preflight). |
| `font.leading.relaxed` | `--font-leading-relaxed` | `1.625` | observed | `@layer theme :root,:host { --leading-relaxed } (via .leading-relaxed)` | 25 | leading-relaxed (--leading-relaxed): CTA and footer copy. |
| `font.weight.regular` | `--font-weight-regular` | `400` | observed | `@layer theme :root,:host { --font-weight-normal }` | 1 | Theme --font-weight-normal, applied by .font-normal. |
| `font.weight.medium` | `--font-weight-medium` | `500` | observed | `@layer theme :root,:host { --font-weight-medium }` | 140 | Theme --font-weight-medium, applied by .font-medium. (font-medium 122 + file:font-medium 18) |
| `font.weight.semibold` | `--font-weight-semibold` | `600` | observed | `@layer theme :root,:host { --font-weight-semibold }` | 230 | Theme --font-weight-semibold, applied by .font-semibold. |
| `font.weight.bold` | `--font-weight-bold` | `700` | observed | `@layer theme :root,:host { --font-weight-bold }` | 98 | Theme --font-weight-bold, applied by .font-bold. |
| `font.tracking.heading` | `--font-tracking-heading` | `-.03em` | observed | `@layer base h1,h2,h3` | 158 | Base letter-spacing for h1, h2, h3. |
| `font.tracking.caps-12` | `--font-tracking-caps-12` | `.12em` | observed | `.tracking-\[0\.12em\]{--tw-tracking:.12em;letter-spacing:.12em}` | 95 | tracking-[0.12em], always with uppercase. Client-name pills. |
| `font.tracking.caps-16` | `--font-tracking-caps-16` | `.16em` | observed | `.tracking-\[0\.16em\]{--tw-tracking:.16em;letter-spacing:.16em}` | 3 | tracking-[0.16em], always with uppercase. CONCEPT · MOCK badge. |
| `font.tracking.caps-18` | `--font-tracking-caps-18` | `.18em` | observed | `.tracking-\[0\.18em\]{--tw-tracking:.18em;letter-spacing:.18em}` | 75 | tracking-[0.18em], always with uppercase. Case-card client kickers and dt labels. |
| `font.tracking.caps-20` | `--font-tracking-caps-20` | `.2em` | observed | `.tracking-\[0\.2em\]{--tw-tracking:.2em;letter-spacing:.2em}` | 12 | tracking-[0.2em], always with uppercase. Footer column headings, insight dates. |
| `font.tracking.caps-22` | `--font-tracking-caps-22` | `.22em` | observed | `.tracking-\[0\.22em\]{--tw-tracking:.22em;letter-spacing:.22em}` | 12 | tracking-[0.22em], always with uppercase. Section and CTA-band eyebrows. |
| `font.tracking.caps-25` | `--font-tracking-caps-25` | `.25em` | observed | `.tracking-\[0\.25em\]{--tw-tracking:.25em;letter-spacing:.25em}` | 46 | tracking-[0.25em], always with uppercase. Inner-page hero eyebrows, home card kickers. |
| `font.tracking.caps-35` | `--font-tracking-caps-35` | `.35em` | observed | `.tracking-\[0\.35em\]{--tw-tracking:.35em;letter-spacing:.35em}` | 7 | tracking-[0.35em], always with uppercase. Display hero eyebrow and client-strip eyebrow. |

**Observed text styles** (the typographic classes from each element's class attribute; layout classes such as `mt-*` and `max-w-*` are left out):

| Role | Classes | Where | Uses |
|---|---|---|---|
| Hero h1, display | `text-5xl leading-[0.95] font-bold sm:text-7xl` (home); `text-5xl leading-none font-bold sm:text-7xl` (/contact); `… sm:text-6xl` (/booking) | /, /booking, /contact | 3 |
| Hero h1, clean | `font-clean text-5xl font-bold leading-[0.95] sm:text-7xl`; /plan-my-event uses `font-clean text-4xl font-bold sm:text-6xl` | /work, /portfolio, /services, /insights, /about, /plan-my-event | 6 |
| Section h2 | `text-3xl font-bold` (+ `sm:text-4xl`/`sm:text-5xl`) or `text-4xl font-bold` | all pages | 22 |
| Case-card title | `mt-1 text-2xl font-bold` (/work, /portfolio) · `text-xl font-semibold` (home) | /work, /portfolio, / | 62 + 34 |
| Hero eyebrow, display | `font-display text-xs tracking-[0.35em] text-primary uppercase` | /, /booking, /contact, client strips | 7 |
| Hero eyebrow, clean | `font-clean text-xs font-semibold tracking-[0.25em] text-primary uppercase` | inner pages | 6 |
| Card kicker | `text-xs font-semibold tracking-[0.18em] text-primary uppercase` | /work, /portfolio | 62 |
| Client pill | `font-display text-sm tracking-[0.12em] uppercase` | client strips | 95 |
| Nav link | `text-sm text-muted-foreground transition-colors hover:text-foreground` | header | 64 + 8 active |
| Button label | `text-sm font-medium` (header CTA `text-xs`) | all pages | 42 |
| Lead paragraph | `text-base`–`text-lg text-muted-foreground` (max-w-2xl) | heroes | 9 |
| Card body | `text-sm text-muted-foreground` | cards | 57 |
| Form label | `text-sm font-medium leading-none` | forms | 26 |

**Labels.** Letter-spaced labels always pair `uppercase` with one of seven `tracking-[…]` values. Most generic eyebrows are authored in sentence case and uppercased by CSS. The exceptions are the Title Case home hero eyebrow ("Corporate & Brand Event Production") and the all-caps "CONCEPT · MOCK" badge; client names are proper nouns *(voc-vp-22)*. No italic is used anywhere *(typ-64)*.

## 5. Spacing and radius

*Layout, elevation and motion are kept in this section because the brief allows only the listed sections.*

### Spacing and layout

The spacing base is `--spacing:.25rem`, and every utility compiles to `calc(var(--spacing) * N)`. 18 multipliers are in use across 1,370 spacing-class uses; the six most frequent cover 1,102 of them. The HTML has no arbitrary spacing values *(spc-04, spc-15)*.

| Multiplier | Size | Uses |
|---|---|---|
| 2 | 8px | 278 |
| 4 | 16px | 244 |
| 5 | 20px | 185 |
| 3 | 12px | 175 |
| 6 | 24px | 124 |
| 1 | 4px | 96 |

**Layout:**
- **Container:** every content wrapper is `mx-auto max-w-6xl px-5`, a 72rem container with a fixed 20px gutter.
- **Section padding:**
  - Default content sections use `py-20`. Home sections use `py-24`, and the home hero `py-24 sm:py-32`.
  - The first block on /work, /portfolio, /services and /insights uses `py-16 lg:py-24`.
  - /booking and /about use `py-16 sm:py-20`, /plan-my-event `py-20 sm:py-28`, and /contact `py-20 sm:py-24`.
- **Header:** sticky, `h-16`, `bg-background/80 backdrop-blur-xl`, `z-40`.
- **Breakpoints:** 40, 48 and 64rem. The 80rem and 96rem breakpoints exist only for the unused `.container`.
- **Hover gating:** Tailwind `hover:` utilities sit inside `@media (hover:hover)`. The custom `.card-lift:hover` (105 cards) is not gated.

*(spc-21, spc-22, spc-27, spc-29, spc-31–spc-36, spc-83)*

**Image ratios.** Images use `aspect-[16/10]` (12) and `aspect-[4/3]` (5). These are not tokenised because DTCG has no ratio type *(spc-115)*.

| Token | CSS variable | Value | Mode | Source selector | Uses | Notes |
|---|---|---|---|---|---|---|
| `space.unit` | `--space-unit` | `.25rem` | observed | `@layer theme :root,:host { --spacing }` |  | Tailwind --spacing base; every spacing utility is calc(var(--spacing) * N). |
| `space.1` | `--space-1` | `.25rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 96 | calc(var(--spacing) * 1) = 4px at a 16px root. |
| `space.1-5` | `--space-1-5` | `.375rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 32 | calc(var(--spacing) * 1.5) = 6px at a 16px root. |
| `space.2` | `--space-2` | `.5rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 278 | calc(var(--spacing) * 2) = 8px at a 16px root. |
| `space.2-5` | `--space-2-5` | `.625rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 3 | calc(var(--spacing) * 2.5) = 10px at a 16px root. |
| `space.3` | `--space-3` | `.75rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 175 | calc(var(--spacing) * 3) = 12px at a 16px root. |
| `space.4` | `--space-4` | `1rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 244 | calc(var(--spacing) * 4) = 16px at a 16px root. |
| `space.5` | `--space-5` | `1.25rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 185 | calc(var(--spacing) * 5) = 20px at a 16px root. |
| `space.6` | `--space-6` | `1.5rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 124 | calc(var(--spacing) * 6) = 24px at a 16px root. |
| `space.7` | `--space-7` | `1.75rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 31 | calc(var(--spacing) * 7) = 28px at a 16px root. |
| `space.8` | `--space-8` | `2rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 60 | calc(var(--spacing) * 8) = 32px at a 16px root. |
| `space.9` | `--space-9` | `2.25rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 11 | calc(var(--spacing) * 9) = 36px at a 16px root. |
| `space.10` | `--space-10` | `2.5rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 26 | calc(var(--spacing) * 10) = 40px at a 16px root. |
| `space.14` | `--space-14` | `3.5rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 4 | calc(var(--spacing) * 14) = 56px at a 16px root. |
| `space.16` | `--space-16` | `4rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 17 | calc(var(--spacing) * 16) = 64px at a 16px root. |
| `space.20` | `--space-20` | `5rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 18 | calc(var(--spacing) * 20) = 80px at a 16px root. |
| `space.24` | `--space-24` | `6rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 64 | calc(var(--spacing) * 24) = 96px at a 16px root. |
| `space.28` | `--space-28` | `7rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 1 | calc(var(--spacing) * 28) = 112px at a 16px root. |
| `space.32` | `--space-32` | `8rem` | observed | `p-/m-/gap-/space-* utilities in HTML class attributes` | 1 | calc(var(--spacing) * 32) = 128px at a 16px root. |
| `size.container` | `--size-container` | `72rem` | observed | `@layer theme :root,:host { --container-6xl } (via .max-w-6xl)` | 56 | Content container: every wrapper is mx-auto max-w-6xl px-5 (56 of 56). |
| `size.gutter` | `--size-gutter` | `1.25rem` | observed | `header > div / section / footer > div (.px-5)` | 56 | Page gutter px-5 on every content wrapper, constant at all breakpoints. (56 wrappers (all also mx-auto max-w-6xl); px-5 occurs 59 times in total, the other 3 are padding on min-h-12 CTA buttons) |
| `size.header-height` | `--size-header-height` | `4rem` | observed | `header > div.h-16` | 9 | Sticky header row (h-16). |
| `size.icon` | `--size-icon` | `1rem` | observed | `.size-4 / .\[\&_svg\]\:size-4 svg` | 108 | Icon size: size-4 on lucide icons and [&_svg]:size-4 inside every button. (size-4 65 + [&_svg]:size-4 43) |
| `breakpoint.sm` | `--breakpoint-sm` | `40rem` | observed | `@media (width>=40rem)` | 119 | @media (width>=40rem) — sm: variants. |
| `breakpoint.md` | `--breakpoint-md` | `48rem` | observed | `@media (width>=48rem)` | 45 | @media (width>=48rem) — md: variants. |
| `breakpoint.lg` | `--breakpoint-lg` | `64rem` | observed | `@media (width>=64rem)` | 31 | @media (width>=64rem) — lg: variants. |
| `z.header` | `--z-header` | `40` | observed | `.z-40` |  | Sticky header (z-40). |
| `z.floating` | `--z-floating` | `50` | observed | `.z-50` |  | Floating WhatsApp button (z-50). |
| `blur.header` | `--blur-header` | `24px` | observed | `@layer theme :root,:host { --blur-xl } (via .backdrop-blur-xl)` | 9 | backdrop-blur-xl behind the translucent sticky header (--blur-xl). |
| `blur.glass` | `--blur-glass` | `8px` | observed | `@layer theme :root,:host { --blur-sm } (via .backdrop-blur-sm)` | 1 | backdrop-blur-sm on the glass outline button over a photo (--blur-sm). |

### Radius

All radius steps derive from `--radius:.5rem`. There are no `--radius-*` variables *(spc-51)*.

| Token | CSS variable | Value | Mode | Source selector | Uses | Notes |
|---|---|---|---|---|---|---|
| `radius.base` | `--radius-base` | `.5rem` | observed | `:root { --radius }` |  | Declared --radius; all rounded-* steps are offsets of it. |
| `radius.sm` | `--radius-sm` | `calc(.5rem - 4px)` | observed | `.rounded-sm` | 3 | rounded-sm (4px at 16px root): badge. Declared: `calc(var(--radius) - 4px)`. |
| `radius.md` | `--radius-md` | `calc(.5rem - 2px)` | observed | `.rounded-md` | 113 | rounded-md (6px): buttons, inputs, service/insight cards. Declared: `calc(var(--radius) - 2px)`. |
| `radius.lg` | `--radius-lg` | `.5rem` | observed | `.rounded-lg` | 87 | rounded-lg (= --radius, 8px): case-study cards, panels, CTA bands. Declared: `var(--radius)`. |
| `radius.xl` | `--radius-xl` | `calc(.5rem + 4px)` | observed | `.rounded-xl` | 34 | rounded-xl (12px): home teaser cards only. Declared: `calc(var(--radius) + 4px)`. |
| `radius.full` | `--radius-full` | `2147483647px` | observed | `.rounded-full` | 136 | rounded-full: pills, chips, floating button, social icons. |

### Shadow, focus and gradients

**Shadows.** The dark UI uses one black micro-shadow on buttons and inputs, and one brand-orange glow for hover lift and the floating button.

**Borders and focus.** Focus is a 1px orange ring. Borders are 1px only; there are no `divide-*` utilities and no `<hr>` *(spc-70, spc-75, cmp-misc-03)*.

**Hero overlays.** These scrims are not tokenised because their values vary per page *(cmp-hero-01–04)*:
- Four heroes (home, /booking, /contact, /about) each layer two arbitrary `--background` scrims, one at 90deg and one at 0deg. /booking and /contact share the same pair.
- /plan-my-event uses one vertical veil: `bg-gradient-to-b from-background/80 via-background/85 to-background`.

| Token | CSS variable | Value | Mode | Source selector | Uses | Notes |
|---|---|---|---|---|---|---|
| `shadow.sm` | `--shadow-sm` | `0 1px 3px 0 #0000001a, 0 1px 2px -1px #0000001a` | observed | `.shadow, .shadow-sm` | 68 | Tailwind shadow and shadow-sm compile to the same value (black 10%) — buttons and inputs. (usage = shadow 29 + shadow-sm 39) |
| `shadow.lift` | `--shadow-lift` | `0 24px 60px -24px color-mix(in oklab, #ff4000 35%, transparent)` | observed | `@supports (color:color-mix(in lab, red, red)) { :root { --shadow-lift } }` | 109 | Brand glow: .card-lift:hover and the floating WhatsApp button (shadow-[var(--shadow-lift)]). Declared: `0 24px 60px -24px color-mix(in oklab, var(--primary) 35%, transparent)`. (usage = card-lift 105 + floating button 4) |
| `shadow.focus-ring` | `--shadow-focus-ring` | `0 0 0 1px #ff4000` | observed | `.focus-visible\:ring-1:focus-visible + .focus-visible\:ring-ring:focus-visible` | 64 | Default focus-visible ring on buttons and fields: ring-1 in --ring, no offset. |
| `gradient.scrim` | `--gradient-scrim` | `linear-gradient(0deg,#0b0b0c,transparent)` | observed | `.bg-\[linear-gradient\(0deg\,var\(--background\)\,transparent\)\]` | 57 | Bottom-up canvas scrim: 56 case-card captions and 1 /services image caption. Declared: `linear-gradient(0deg,var(--background),transparent)`. |
| `gradient.cta-tint` | `--gradient-cta-tint` | `linear-gradient(110deg,color-mix(in oklab,#ff4000 14%,#1a1a1c),#1a1a1c 56%)` | observed | `arbitrary bg-[linear-gradient(110deg,...)] (@supports color-mix)` | 2 | Orange-tinted CTA band background (primary 14% into surface). Declared: `linear-gradient(110deg,color-mix(in oklab,var(--primary) 14%,var(--surface)),var(--surface) 56%)`. |

### Motion

| Token | CSS variable | Value | Mode | Source selector | Uses | Notes |
|---|---|---|---|---|---|---|
| `motion.duration.fast` | `--motion-duration-fast` | `.15s` | observed | `@layer theme { --default-transition-duration }` | 183 | Tailwind default transition duration: colour changes on links and buttons, and the arrow nudge. (transition-colors 178 + transition-transform without a duration-* class 5) |
| `motion.duration.base` | `--motion-duration-base` | `.3s` | observed | `:root { --transition-smooth }` |  | --transition-smooth (card-lift) and duration-300 (floating button). |
| `motion.duration.slow` | `--motion-duration-slow` | `.5s` | observed | `.duration-500` | 60 | duration-500: case-card image zoom. |
| `motion.duration.reveal` | `--motion-duration-reveal` | `.7s` | observed | `.duration-700` | 166 | duration-700: scroll-reveal wrappers. |
| `motion.easing.standard` | `--motion-easing-standard` | `[0.4, 0, 0.2, 1]` | observed | `@layer theme { --default-transition-timing-function }` |  | Default transition timing function. |
| `motion.easing.out` | `--motion-easing-out` | `[0, 0, 0.2, 1]` | observed | `@layer theme { --ease-out }` | 166 | --ease-out: scroll-reveal. |
| `motion.easing.smooth` | `--motion-easing-smooth` | `[0.22, 1, 0.36, 1]` | observed | `:root { --transition-smooth }` |  | From --transition-smooth: card-lift. |

**Observed patterns:**
- **Scroll reveal:** 166 wrappers use `translate-y-6 opacity-0 transition-[opacity,transform] duration-700 ease-out` and become `data-[visible=true]:translate-y-0 opacity-100`, a 24px rise over .7s. Each wrapper also has an inline `transition-delay` *(spc-84, spc-85)*:
  - Home hero: 0/80/160/240ms.
  - Home project grid: +100ms per card with no cap, reaching 3000ms.
  - /work and /portfolio grids: alternating 0/80ms.
  - /services: 0/50/100 and 0/100/200ms.
  - /booking, /contact, /plan-my-event and /about: a 120ms second step.
- **Card lift:** `.card-lift:hover` moves a card up 6px and adds `shadow.lift` and the 45% orange border, over `.3s cubic-bezier(.22, 1, .36, 1)` *(cmp-card-17)*.
- **Image zoom:** `group-hover:scale-[1.02]` over `.5s` (60) *(spc-93)*.
- **Arrow nudge:** `group-hover:translate-x-1` (4px) at the default `.15s` (5) *(spc-94)*.
- **Floating-button lift:** `hover:-translate-y-1` (4px) with `duration-300` (4) *(spc-95)*.
- **Not present:** `prefers-reduced-motion` handling, and `animate-*` classes in the HTML *(spc-101, spc-102)*.

## 6. Components actually seen

All four core component types (button, nav, card, form) were seen. Other components that appear on the pages are listed after them, because this section covers every component actually seen. Class strings are verbatim, and "…" marks where classes have been left out. Counts are across the 9 pages.

### Button

**Base classes.** 33 of 43 buttons and button-styled links carry the full base below *(cmp-btn-01)*:

`inline-flex items-center justify-center gap-2 whitespace-nowrap text-sm font-medium cursor-pointer transition-colors focus-visible:outline-none focus-visible:ring-1 focus-visible:ring-ring disabled:pointer-events-none disabled:opacity-50 disabled:cursor-not-allowed [&_svg]:pointer-events-none [&_svg]:size-4 [&_svg]:shrink-0`

The other 10 differ slightly:
- The 9 header CTAs drop `inline-flex`/`text-sm` and use `hidden sm:inline-flex … text-xs`.
- The date-picker trigger drops `justify-center`/`font-medium`.

| Variant · size | Added classes | Uses | Example label |
|---|---|---|---|
| Primary · lg | `bg-primary text-primary-foreground shadow hover:bg-primary/90 h-10 rounded-md px-8` | 16 | "WhatsApp the floor team"; /plan-my-event submit (`w-full`) |
| Primary · sm (header) | `… h-8 rounded-md px-3 text-xs hidden sm:inline-flex` | 9 | "Send a brief" |
| Primary · xl (custom) | `… rounded-md h-auto min-h-12 px-5 py-3` | 3 | WhatsApp hero CTA (/booking, /contact) |
| Primary · default | `… h-9 px-4 py-2` | 1 | "Send a brief" (/services) |
| Outline · lg | `border border-input bg-background shadow-sm hover:bg-accent hover:text-accent-foreground h-10 rounded-md px-8` | 9 | "Send a brief", "Plan my event" |
| Outline · default | outline + `h-9 px-4 py-2` | 1 | "Browse all production stills" (/work) |
| Outline · glass | outline + `bg-background/30 backdrop-blur-sm h-12`, over a photo | 1 | "Or leave a brief" (/contact) |
| Secondary · lg | `bg-secondary text-secondary-foreground shadow-sm hover:bg-secondary/80 h-10 rounded-md px-8` | 2 | "Request this date", "Send a brief" (form submits) |
| Outline · date-picker trigger | `justify-start text-left font-normal h-9` | 1 | "Pick a date" |

**Icons and gap.** Icons are 16px (`size.icon`), separated from the label by an 8px gap (`gap-2`). Three WhatsApp/arrow CTAs add `mr-2`/`ml-2` on the icon, making the gap 16px.

**States:**
- **Hover:** primary drops to 90% opacity. Outline fills orange, because `--accent` = `--primary`. Secondary drops to 80%.
- **Focus-visible:** a 1px orange ring.
- **Disabled:** 50% opacity.

**Not rendered:** ghost, link, destructive and icon-only variants *(cmp-btn-11–14)*.

### Navigation

- **Header** *(cmp-nav-01–05)*:
  - The same header appears on all 9 pages: `sticky top-0 z-40 border-b border-border bg-background/80 backdrop-blur-xl`.
  - Contents, in order: the logo PNG (`h-12`), 8 desktop links (`hidden … gap-8 md:flex`), the "Send a brief" primary-sm button, and a `size-9 rounded-md border` menu toggle below md.
  - The active link gets `text-foreground` and `aria-current="page"`, but `.text-muted-foreground` comes later in the stylesheet and wins, so it still renders muted. There is no visible active state, underline or indicator *(cmp-nav-04)*.
- **Mobile menu panel:** not server-rendered, so not observed *(cmp-nav-06)*.
- **Footers** *(cmp-ftr-01–06)*:
  - Home has a three-column footer on `bg-surface`, with round `size-9` social icon buttons that turn orange on hover.
  - The 8 inner pages have a compact two-column `text-xs` footer on the canvas.

### Card

- **Base:** `rounded-* border border-border bg-card`, mostly with the `.card-lift` hover.
- **Case-study cards** (62; 31 each on /work and /portfolio), base classes `card-lift group relative flex min-h-72 flex-col justify-end overflow-hidden rounded-lg border border-border bg-card` *(cmp-card-01, -02)*:
  - 56 have a full-bleed `object-cover` photo under the `gradient.scrim` caption (`p-5 pt-24`), with a kicker, a `text-2xl font-bold` title and "View case study →".
  - 6 are text-only, with a `relative p-6` caption.
- **Home teaser cards** (34): `card-lift block h-full rounded-xl border border-border bg-card p-6` *(cmp-card-03, -04)*.
- **Service pillar cards** (5): `rounded-md`, a 16/10 image on top, a 2px × 32px orange accent bar and a "Deep page" link *(cmp-card-05)*.
- **Supporting service cards** (12): `h-full rounded-md border border-border bg-card p-5`, with no hover *(cmp-card-06)*.
- **Concept cards** (3, /services): `flex h-full flex-col overflow-hidden rounded-md border border-border bg-card`, no hover, carrying the CONCEPT · MOCK badge *(cmp-card-07)*.
- **Insight cards** (4): `p-7`, with a stretched link and a `<time>` kicker *(cmp-card-08)*.
- **Contact-detail cards and asides** (/booking, /contact): `rounded-lg border border-border bg-card p-6`. Form panels use `p-5 sm:p-7` *(cmp-card-13–15)*.

### Form

Forms appear on /booking, /contact and /plan-my-event, built from shadcn-style controls *(cmp-form-01–16)*:

| Control | Classes | Uses |
|---|---|---|
| Input | `flex h-9 w-full rounded-md border border-input bg-transparent px-3 py-1 text-base shadow-sm transition-colors file:border-0 file:bg-transparent file:text-sm file:font-medium file:text-foreground placeholder:text-muted-foreground focus-visible:outline-none focus-visible:ring-1 focus-visible:ring-ring disabled:cursor-not-allowed disabled:opacity-50 md:text-sm` | 18 |
| Textarea | `flex min-h-[60px] w-full rounded-md border border-input bg-transparent px-3 py-2 text-base shadow-sm … md:text-sm` | 3 |
| Select trigger (Radix) | `flex h-9 w-full items-center justify-between … rounded-md border border-input bg-transparent px-3 py-2 text-sm shadow-sm … focus:ring-1 focus:ring-ring` | 4 |
| Label | `text-sm font-medium leading-none peer-disabled:cursor-not-allowed peer-disabled:opacity-70` | 26 |
| Field / row | `space-y-2` per field; `grid gap-5 sm:grid-cols-2` per row; `space-y-5` per form | — |

- **/booking and /contact:**
  - The form sits in a `… rounded-lg border border-border bg-card p-5 sm:p-7` panel.
  - The submit is the **secondary** button.
  - A primary "WhatsApp instead" link sits beside it (`flex flex-col gap-3 sm:flex-row`).
- **/plan-my-event:**
  - The form itself is the panel: `space-y-5 rounded-md border border-border bg-card p-6 sm:p-8`.
  - The submit is a full-width **primary** button, "Map my production pathway".
- **Not in the SSR markup:** required markers, helper or error text, checkboxes or radios, fieldsets, and success states *(cmp-form-09–11, -14)*.

### Other components seen

- **Eyebrow / kicker:** `text-xs uppercase` plus `tracking-[…]`, in `text-primary` (or `text-muted-foreground` in CTA bands). Seven variants, 141 uses, plus 4 `<time>` date kickers on /insights *(cmp-eyebrow-01–07, component-miss-05)*.
- **Pills and chips** *(cmp-chip-01–05)*:
  - **Client-name pills** (95): `rounded-full border border-border bg-card px-4 py-2 font-display text-sm tracking-[0.12em] uppercase`. Text only, no logos.
  - **/about tag chips** (6): `rounded-full border border-border bg-card px-4 py-1.5 text-sm text-muted-foreground`.
  - **/portfolio filter chips:** 25 inactive, `rounded-full border border-border px-4 py-1.5 text-sm text-muted-foreground transition-colors hover:text-foreground`; 1 active, `rounded-full border border-primary bg-primary px-4 py-1.5 text-sm font-semibold text-primary-foreground active`.
- **Badge:** one style, 3 instances on /services ("CONCEPT · MOCK"): `absolute top-3 left-3 rounded-sm border border-primary bg-background/90 px-2.5 py-1 font-clean text-[0.68rem] font-bold tracking-[0.16em] text-primary uppercase` *(cmp-badge-01)*.
- **CTA band:** `flex flex-col gap-7 rounded-lg border border-primary/35 bg-surface p-7 sm:flex-row sm:items-center sm:justify-between sm:p-9` (5), or the same with `gradient.cta-tint` in place of `bg-surface` (2). Each holds a muted eyebrow, an h2 and buttons *(cmp-cta-01, -02)*.
- **Heroes** *(cmp-hero-01–06)*:
  - Photo heroes under `--background` scrims: home, /booking, /contact, /about, /plan-my-event.
  - Split text + framed photo: /work, /services.
  - Text-only: /portfolio, /insights.
- **Floating WhatsApp button:** `fixed right-5 bottom-5 z-50 inline-flex items-center gap-2 rounded-full bg-primary px-4 py-3 font-medium text-primary-foreground shadow-[var(--shadow-lift)] transition-transform duration-300 hover:-translate-y-1 …`, with a ring-2 + offset focus style. It appears on home, /booking, /plan-my-event and /contact *(cmp-wa-01)*.
- **Credentials strip:** home only, `border-y bg-surface`, with middot-separated display-font spans *(cmp-strip-03)*.
- **Not seen:** modal, tabs, accordion, table, pagination, breadcrumb, testimonial, stat card, skip link and charts. Some have compiled utilities in the CSS but no markup *(cmp-abs-01–08, component-miss-07–10)*.

## 7. Voice, with quotes

All quotes are verbatim from the page named. Eyebrows appear uppercase on screen through CSS; the quotes show the text as authored. In quotes, " / " marks a `<br/>` line break in the source. The eyebrow column below contains real slashes ("Work / proof-led production").

### Headlines by page

| Page | h1 | Hero eyebrow |
|---|---|---|
| `/` | "ONE team. ONE Concept. ONE Event. ONE Invoice." ("ONE Invoice." in orange) | "Corporate & Brand Event Production" |
| `/work` | "See the work. / Then brief the team." | "Work / proof-led production" |
| `/portfolio?client=` | "Browse the proof. / Filter by client." | "Portfolio / proof cases" |
| `/services` | "One crew. / Five pillars. / One invoice." | "Services / full-stack production" |
| `/insights` | "Floor notes. / Not brochure filler." | "Insights" |
| `/booking` | "Hold a date with the floor team." | "Booking · Hold a date" |
| `/plan-my-event` | "Describe the event. See the production path." | "Plan · Pathway builder" |
| `/about` | "ONE team. ONE Concept. ONE Event. ONE Invoice." | "About · 360 Vision Events" |
| `/contact` | "Brief the floor team." | "Contact · Brief us now" |

*(voc-home-03/04, voc-work-03/04, voc-port-03/04, voc-svc-03/04, voc-ins-03/04, voc-book-03/04, voc-plan-03/04, voc-about-03/04, voc-con-03/04)*

### Buttons and CTAs (verbatim labels)

| Label | Where |
|---|---|
| "Send a brief" | header button on every page; also heroes, CTA bands, and the /contact submit |
| "WhatsApp the floor team" (sometimes with " →") | primary button on most pages |
| "WhatsApp instead" | /booking, /contact |
| "WhatsApp us" | floating button, sm and up |
| "Book a date" | nav; home CTA band |
| "Request this date" | /booking submit |
| "Map my production pathway" | /plan-my-event submit |
| "View case study →" | /work and /portfolio cards |
| "View work" | home cards |
| "Explore services" | home cards |
| "Deep page" | /services cards |
| "Read the floor note" | /insights cards |
| "Talk through this look" | /services concept cards |
| "Browse all production stills" | /work |
| "Or leave a brief" | /contact |

*(voc-gl-02, voc-gl-04, voc-vp-11, voc-book-10, voc-plan-08, voc-work-07, voc-home-09/12, voc-svc-10/15, voc-ins-09, voc-work-09, voc-con-06)*

### Section and CTA-band headings (examples)

- "Built for brands that cannot afford an off night." (`/`)
- "Need one crew to take the idea to the floor?" (`/`, also on /work and /plan-my-event)
- "Built for the brief. / Owned on the floor." (`/work`)
- "Quote the stack / you actually need." (`/services`)
- "Named proof. Nothing invented." (`/about`)
- "Ready to brief the floor?" (`/contact`)
- "Bring the brief. We’ll bring the floor team." (`/about`)

The recurring CTA-band eyebrow is "Ready when the brief is real". *(voc-home-07, -14, voc-work-06, voc-svc-08, voc-about-11, -13, voc-con-12, voc-gl-07)*

### Patterns (each backed by two or more quotes)

- **Mantra:** "ONE team · ONE Concept · ONE Event · ONE Invoice" (middot form, 7 pages), or the full-stop form as the h1 on / and /about. Casing is inconsistent: "ONE team" against "ONE Concept"; /services writes "One crew. … One invoice." *(voc-vp-01, voc-vp-02)*
- **Full stops on headlines:** all 9 h1s end with a full stop. Of the 33 h2s, 19 end with a full stop, 5 with a question mark, and 9 are bare labels. Headlines are staccato beats split with `<br/>`. *(voc-vp-03, voc-vp-04, voice-miss-15)*
- **"X, not Y" contrast:** "Proof, not brochure." appears 24 times, plus a 25th variant on /insights ("Proof, not brochure — not a gear catalogue."). Other examples are "Quote the floor, not the shell." (/insights) and "not a gear catalogue" (/services). *(voc-vp-06)*
- **"Quote the …" imperatives:** "Quote the run-of-show" and "Quote the room stack" (/services); "Quote the room." (/insights). *(voc-vp-07)*
- **Core lexicon:** "floor" (72, case-insensitive; e.g. "floor team", "on the floor") and "brief" (54; noun and verb). *(voc-vp-08, voc-vp-09)*
- **CTAs:**
  - Mostly imperative, sentence case, 2–4 words. The exceptions are the noun phrases "Deep page" and "Press kit".
  - The channel is used as a verb ("WhatsApp the floor team"), sometimes with a trailing "→".
  - WhatsApp comes first: "WhatsApp is fastest." (`/`), "WhatsApp is the fastest hire path." (`/contact`).
  - On /booking and /contact the submit is secondary-styled, and a WhatsApp link gets the primary button. On /plan-my-event the submit itself is primary.

  *(voc-vp-11, voc-vp-12, voc-plan-08)*
- **Person and register:** "we" and "you" are used sparingly; most copy is subjectless fragments ("Based in Gauteng. Working nationwide."). Contractions are rare ("We’ll" ×3), and "cannot" stays uncontracted. *(voc-vp-13, voc-vp-14, voc-vp-26)*
- **South African grounding:** "Gauteng" (29), "South Africa" (33), "nationwide" (25, case-insensitive), `.co.za` and +27 formats, and the BEE status line. *(voc-vp-16)*
- **Spelling:** mostly UK/SA: "décor", "programme", "colour", "catalogue", "centrepieces", "finalised". Visible copy has one US slip ("labeled", /services). "centerpieces" appears only in image `alt` text on /work and /portfolio. *(voc-vp-17)*
- **Punctuation:** spaced em dash (59), middot separators (92), "×" for collaborations ("BMW i8 × Allianz Launch"), "→" in CTAs, and "&" in headings. There are no exclamation marks. *(voc-vp-18)*
- **Scope line:** "Corporate and brand only — not weddings or private parties." (/booking), with variants on /services, /plan-my-event and /about. *(voc-vp-19)*
- **Title Case `<title>` vs sentence-case UI:** "Send a Brief — 360 Vision Events" (title) against "Send a brief" (button). The exception is /insights, whose title reuses the sentence-case h1. *(voc-vp-23)*

**Public brand channels** (`public_brand_channel`; digits and addresses withheld):
- `info@360-vision-events.co.za`
- a WhatsApp business link (`wa.me`)
- a company telephone (`tel:`)
- LinkedIn `/company/360visionevents`
- two Facebook pages
- YouTube `@360visionevents`

*(voc-ch-01–06)*

## 8. Usage rules that follow from the observations

These rules describe how the live site already behaves. They are not new brand direction.

1. **Dark canvas only.** Pages sit on `color.bg`; cards, bands and panels sit on `color.surface`; copy uses `color.text`. `color.surface-2` appears only as the secondary-button fill. The site declares no light theme, so a light variant would be invention *(col-129, col-055)*.
2. **Orange is a signal, not a field.** `color.brand` marks CTA fills, eyebrows and kickers, text links, the focus ring, hover borders and the 2px accent bar. Large orange areas appear only as a 14% tint (`gradient.cta-tint`) or as 35%/45% hairlines *(col-064, col-052, col-075, col-101, col-106)*.
3. **Dark text on orange.** Put `color.on-brand` (`#0b0b0c`) on `color.brand` (5.61:1). The site never sets white on orange (3.51:1) *(col-010)*.
4. **One brand hue.** `color.accent` equals `color.brand`, so do not introduce a second accent. Secondary copy and nav links use `color.text-muted`; hovered links use `color.text`. The active nav link has no visible state (see the gaps) *(col-015, cmp-nav-03/04)*.
5. **Hairline borders:**
   - Cards, chips and dividers default to a 1px `color.border` (white 12%).
   - Form fields and outline buttons use `color.input` (16%).
   - CTA bands use `color.brand-border` (35%); one /about fact card uses brand at 20%.
   - The active filter chip and the badge use solid `color.brand`.

   *(col-019, col-020, col-075, cmp-chip-04, cmp-badge-01)*
6. **Headings:**
   - The base rule sets h1–h3 in Space Grotesk at -.03em, and body in Inter Tight.
   - In practice 6 of 9 page h1s, 14 of 33 h2s and 8 of 116 h3s override this with Inter (`.font-clean`); see the gaps.
   - The majority h1 pattern (6 of 9) is `text-5xl` → `sm:text-7xl`, bold, leading .95.
   - Labels are xs/sm, uppercase and letter-spaced.

   *(typ-07, typ-76–85)*
7. **Buttons:**
   - All are `rounded-md`, with 16px icons and an 8px gap. Labels are `text-sm font-medium`, except the header CTA (`text-xs`) and the date-picker trigger (`font-normal`).
   - Primary (orange) carries the main CTA: usually WhatsApp, plus the header "Send a brief" and the /plan-my-event submit. Outline is the alternative. Secondary is the submit on /booking and /contact.
   - Sizes are h-8 (header), h-9 (default), h-10 (most CTAs), and h-12 or min-h-12 (hero).

   *(cmp-btn-01–10)*
8. **Cards:**
   - Cards default to `bg-card` with `color.border`.
   - Radius follows card type: `radius.lg` for image cards and panels; `radius.md` for service, insight and concept cards; `radius.xl` for the 34 home teaser cards.
   - CTA bands are different: `radius.lg` on `bg-surface` or `gradient.cta-tint`, with `color.brand-border`. One /about fact card uses a 20% brand border.
   - Interactive cards use the `.card-lift` hover: a 6px lift, `shadow.lift`, a 45% orange border and `.3s` smooth easing.

   *(cmp-card-01–08, cmp-card-17)*
9. **Layout:**
   - A 72rem container with a constant 20px gutter.
   - Section rhythm of `py-20` (home `py-24`).
   - Two-column grids from `sm`/`md`.
   - Asymmetric `lg:grid-cols-[1fr_0.95fr]`-style splits for split heroes and form/aside layouts.

   *(spc-21, spc-22, spc-29, spc-37, spc-38)*
10. **Motion is short and eased-out:**
    - colour changes `.15s`
    - card lift `.3s`
    - image zoom `.5s` (scale 1.02)
    - scroll reveal `.7s` over a 24px rise
    - arrow and floating-button nudges of 4px

    *(spc-80–spc-95)*
11. **Imagery:**
    - Real production stills, full-bleed `object-cover`, under a `--background` scrim wherever text overlaps.
    - Ratios are 16/10 and 4/3.
    - Concept renders are labelled "CONCEPT · MOCK".

    *(spc-115, spc-116, cmp-badge-01, voc-svc-14)*
12. **Copy:**
    - Mostly imperative, sentence-case CTAs.
    - Full stops on headlines.
    - UK/SA spelling.
    - Em dashes and middots.
    - "360 Vision Events" in UI; the "(PTY) Ltd trading as" form only in legal lines.

    *(voc-vp-03, voc-vp-11, voc-vp-17, voc-bn-04)*

## 9. Open gaps

These are things the site does not show, or shows inconsistently. None of them have been filled in.

- **No light theme or status colours.** `color.success`, `color.warning` and `color.info` are absent. `color.destructive` is declared but never rendered.
- **Form states not visible.** Error, helper, required and success states are not in the SSR markup, and the Select list renders client-side. Observing them would mean submitting a form, which this run must not do.
- **Submit hierarchy is split.** Two forms use a secondary submit beside a primary WhatsApp link; the third (/plan-my-event) uses a full-width primary submit inside a differently styled panel (`rounded-md p-6 sm:p-8` vs `rounded-lg p-5 sm:p-7`).
- **Font loading vs use.** The weights the CSS asks for do not match the weights requested from Google Fonts *(typ-17–typ-19)*:
  - Space Grotesk is requested at 500 and 700, but the CSS asks for 400 (147 `.font-display` labels) and 600 (46 h3s).
  - Inter Tight is requested at 400–600, but `<strong>` asks for 700.
  - Inter 400/500 are requested but never reached.

  By CSS font-matching rules, those requests fall back to the nearest loaded face: 400 → 500, 600 → 700, and Inter Tight 700 → 600. This is inferred, not observed: the Google Fonts stylesheet was not fetched and no browser rendered the pages.
- **Three heading voices.** Hero h1s split between Space Grotesk (3 pages) and Inter `.font-clean` (6 pages). Case-card titles differ between home (`text-xl font-semibold`) and /work (`text-2xl font-bold`). There are two competing eyebrow systems and seven tracking values *(typ-85, typ-90, typ-91, typ-94, typ-95)*.
- **Print and light media.** The site has no light theme or print styles. The templates' paper mode therefore uses proposed values: ink `#0b0b0c`, muted `#5f5f64` (at least 4.5:1 on white), and orange only for rules, bars and large figures, because `#ff4000` on white is 3.5:1. Confirm them with the brand owner *(D28)*.
- **Accessibility signals:**
  - There is no `prefers-reduced-motion` rule.
  - Reveal wrappers ship `opacity-0` in the SSR HTML, so content depends on JS to appear.
  - The home stagger reaches 3000ms.
  - `.card-lift:hover` is not gated by `(hover:hover)`, unlike the utility hovers.
  - Nav links, filter chips and the mobile menu toggle have no custom `focus-visible` style, so they fall back to the browser default.
  - The active nav link has no visible state: its `text-foreground` class loses to `text-muted-foreground` in the cascade, so only `aria-current` marks it.
  - The page declares `html lang="en"`, not `en-ZA`.

  *(spc-83, spc-84, spc-85, spc-102, voice-miss-02)*
- **Not tokenised:** the per-page hero scrim gradients and the 16/10 and 4/3 image ratios. Both are documented in §5.
- **Declared but unused:** `--gradient-hero` (`.hero-surface`), `--gradient-accent`, and `--surface-2` as a surface utility. `--color-bg` and `--sidebar-*` are referenced but never declared *(col-024, col-102, col-140, col-141)*.
- **Logo:**
  - **Only one fully vector logo.** That is the P09 wordmark, whose "360" is `#ff4000`. The P03/P05/P06/P07 SVGs use a bitmap ring, so it won't stay sharp when enlarged, and it is slightly lighter than their vector "360". There are no ON-DARK or P12 SVGs *(D27)*.
  - **Two greys.** "EVENTS" is `#737373` in P03/P05/P06 and `#828282` in P09.
  - **Solid backgrounds.** The pack files sit on solid `#000000`/`#ffffff` grounds, so an ON-DARK file shows as a faint box on the `#0b0b0c` canvas.
  - **The pack's orange is inconsistent.** It runs from `#e22500` to `#ff3e00`, and the wordmark is `#f14624`, while the site and its served logo use `#ff4000`. Agreeing one orange for every file is a decision for the brand owner *(D26)*.
- **Copy inconsistencies:**
  - Mantra casing.
  - Nav and footer naming: "Book a date"/"Booking" and "Plan"/"Plan my event".
  - Straight vs curly apostrophes.
  - "labeled" (US spelling).
  - Internal or SEO terms in public copy: "Entity and NAP", "Canonical:", "/follow-ups", "Inbox email notify is still being finalised".

  *(voc-vp-02, voc-vp-21, voc-vp-25, voice-miss-03)*
- **Coverage limits:**
  - Only the homepage and 8 main-nav pages were read. Detail pages (/work/*, /services/*) and /press, /privacy, /gallery and /founder may use styles not recorded here.
  - Values come from declared CSS and SSR class usage. No browser rendering engine was run, so JS-only states were not observed: the mobile menu, select dropdown, toasts and date picker.

---

## Definition of done

Criteria 1–7 make up the definition of done. Each was re-checked mechanically against the four files as finally written; the table is regenerated until it matches the files it describes.

| # | Criterion (brief wording) | Result | How verified | Detail |
|---|---|---|---|---|
| 1 | `./design-system/DESIGN.md`, `tokens.json`, `tokens.css`, and `evidence.json` all exist. | PASS | listed ./design-system/ | required files present: DESIGN.md, tokens.json, tokens.css, evidence.json; optional extras: assets, preview.html, templates |
| 2 | Every non-null color and font token has `$extensions.mode` of `observed` or `inferred`, and observed tokens have a `source_url`. | PASS | scanned every non-null color.* and font.* token in tokens.json | 62 tokens checked; problems: none |
| 3 | No token value appears that is missing from `evidence.json` observations or from an `inferred` decision. | PASS | cross-checked every token against evidence.json token_trace and the cited observations | 113 tokens (110 observed, 0 inferred, 3 absent). 55 values appear verbatim in their evidence; 29 are the evidence's declaration with var() resolved or calc(var(--spacing) * N) computed (decision D08); 26 numeric/bezier values equal their evidence numerically. Problems: none |
| 4 | `tokens.css` custom properties match `tokens.json` names one-for-one. | PASS | diffed custom-property names (and values) in tokens.css against tokens.json paths | 113 properties vs 113 tokens; names only in JSON: none; only in CSS: none; value mismatches: none |
| 5 | `evidence.json` contains the start URL, final URL, and page list. | PASS | checked the keys in evidence.json | start_url https://360visionevents.co.za; final_url https://360-vision-events.co.za/; pages 9 |
| 6 | No secrets or form tokens appear in the four files. | PASS | searched the four files (and preview.html and templates/) for the brief's literal secret patterns, secret-like token/csrf/bearer assignments, the site-verification value, cookie / request-id / deployment-id values (hash-matched), phone digits, account-like digit runs and SWIFT-like codes in templates/, the bucket host and the withheld personal name | 0 secret or personal-data hits. The word 'token' occurs 284 times, all design-token vocabulary (file names, token paths); 30 mentions of csrf/bearer/secret are type labels or statements with no value attached. |
| 7 | No git commit, push, or deploy was performed by the extraction run; any later operation required explicit user confirmation. | PASS | ran git status and git log in the working directory, and checked decisions D24–D25 | the extraction run made no commit, push, or deploy. The repository was committed and pushed afterwards at the user's explicit request (D25): a7817bd 2026-10-02T13:29:03+02:00 Fix stale "no SVG" wording and the SVG divider labels; 1bf0e37 2026-10-02T12:29:05+02:00 Add owner's ON-LIGHT SVG logos and record what they contain; bcf8a21 2026-10-02T11:52:54+02:00 Merge pull request #2 from AN3S-CREATE/fix-decision-log-order; 94a0b48 2026-10-02T11:50:50+02:00 Fix decision log range and order; 85955e2 2026-10-02T11:47:11+02:00 Merge pull request #1 from AN3S-CREATE/add-official-logo-pack-2026 |

**Overall: PASS — definition of done met.**


## Optional extras

The user asked for these on 2026-10-02, after the package existed *(D21–D24)*:

- **One-page component preview: added**, as `preview.html`.
  - It covers token swatches, the type scale, spacing, radius and shadow, and the header, every button variant (including the date-picker trigger), eyebrows, pills and chips, cards, form controls, both CTA-band variants, footer and floating button.
  - Every colour, type, spacing, radius, shadow and motion value is a `tokens.css` variable, a `calc(var(--space-unit) * N)`, or a literal commented with the observed Tailwind class. Documentation chrome (1px rules, swatch hatching, table columns) uses plain literals.
  - Labels and headings are quoted from the site; body-copy slots use neutral role text. It is labelled as not the live website. An independent audit compared every component with the raw site markup.
  - **To view it:** open it directly from disk in any desktop browser. The Claude Code in-app browser pane renders `file://` pages without styles, so there use the static server in `.claude/launch.json`, or run `python -m http.server 8765 --bind 127.0.0.1 --directory design-system` and visit `http://127.0.0.1:8765/preview.html`.
- **Dark-mode tokens: labelled, no new file.** The existing set is the dark mode, the only mode the site declares; `tokens.json` `$extensions.color_mode` and the `tokens.css` header say so. A light mode is absent and was not invented.
- **Logo copy: PNG copied byte-for-byte** to `assets/logo-horiz-ON-DARK.png`, with `assets/favicon.png` alongside. The owner's official pack is in `assets/logo-pack-2026/` *(D26)*. The owner later supplied five ON-LIGHT SVGs (`logo-pack-2026/svg/`, D27). Only the P09 wordmark is fully vector. No logo was redrawn or traced here.
- **Commercial document templates: added** *(D28)*, in `templates/`.
  - `quotation.html` and `proforma-invoice.html` rebuild the structure of the owner's old documents in this system's look: running header and footer, a title block with a reference list, prepared-for/by or bill-to/from panels, an amount hero, numbered sections, a grouped line-item schedule with subtotals and a totals box, client acceptance, and payment and banking panels.
  - Both use `tokens.css`, the site's fonts and the ON-DARK logo, on A4. An inline script recalculates totals from each row's quantity and rate, and the VAT basis can be switched.
  - Dark is the default. A paper mode (ink-saving print) swaps in the ON-LIGHT P09 SVG.
  - Every client, personal, banking and pricing value from the source documents is left out. Fields are `[placeholders]`, line items are labelled sample content, and `templates/README.md` explains how to fill them in and save a PDF.
- **Distribution, on your explicit request *(D25)*.** The system is also packaged as a Claude skill (`dist/360-vision-events-design-system.skill`, installed for Claude Code), set up as a private design system in Claude Design, and pushed to your GitHub repository (AN3S-CREATE/360-vision-events-design-system). The extraction run itself published nothing *(D24)*.
