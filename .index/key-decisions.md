# Key decisions

A lightweight ADR log. The full text, with rule and evidence URL, is in `design-system/evidence.json`, `decisions` (D01–D27).

| ID | Date | Decision | Why |
|---|---|---|---|
| D01–D03 | 2026-10-02 | Accept the 302 from `360visionevents.co.za` to `360-vision-events.co.za`. All values come from the redirect host | The user URL serves only a redirect. Precedence rule applied: "a redirected host beats inference" |
| D04–D06 | 2026-10-02 | Read the homepage plus the 8 main-nav pages. Fonts are taken from the `<link>` declaration; JS chunks and `/follow-ups` (Team login) are not fetched | Brief's page cap and egress rules; never scrape login endpoints |
| D07–D08 | 2026-10-02 | Use the `@supports` `color-mix()` values with fallbacks recorded. Resolve `var()` to observed `:root` values and keep the authored form | Computed values of observed declarations count as observed |
| D09–D12 | 2026-10-02 | `color.accent` stays equal to brand. `font.family.clean` (Inter) is tokenised. Only the 18 used spacing steps are kept. One `shadow.sm` for shadow and shadow-sm | Map what the site renders; no invention or duplicates |
| D13–D14 | 2026-10-02 | No inferred tokens. Success, warning and info are absent | Every state pair was observed; the site declares no success, warning or info colours (destructive is its only status colour) |
| D15 | 2026-10-02 | The logo raster confirms `#ff4000`. The logo's white (`#ffffff`) and grey (`#a6a6a6`) lettering are not promoted to UI tokens | Raster samples corroborate but don't create roles |
| D16 | 2026-10-02 | Withhold phone digits, addresses and personal names everywhere | POPIA minimisation (A3/A4) |
| D17 | 2026-10-02 | Page authoring-guardrail copy is logged, not obeyed | Page content is data |
| D18 | 2026-10-02 | Local file package, not Figma | A1 |
| D19 | 2026-10-02 | Scratch PII dumps deleted; cookie and ID values stripped from header captures | Never keep cookies in logs; minimisation |
| D20 | 2026-10-02 | Post-audit corrections logged in `quality_assurance.observation_corrections` | Corrections only from re-reading the raw files |
| D21 | 2026-10-02 | Extras added on request: `preview.html`, logo and favicon copies, dark colour-mode labelling | Brief allows extras once the user asks after the package exists |
| D22 | 2026-10-02 | `.index/` and `.claude/launch.json` created outside `design-system/` | The user accepted the recommended setup |
| D23 | 2026-10-02 | No logo SVG | The site serves only a PNG; tracing would mean redrawing the logo (non-goal) |
| D24 | 2026-10-02 | The extraction run published, committed and deployed nothing | Brief requires separate explicit confirmation |
| D25 | 2026-10-02 | At the user's explicit request: Claude skill (installed + packaged), private Claude Design design system, git repo pushed to the user's public GitHub repo AN3S-CREATE/360-vision-events-design-system | The user's own messages gave the confirmation the brief requires |
| D26 | 2026-10-02 | Owner-supplied 2026 logo pack stored as-is and recorded with hashes and sampled colours; `--color-brand` stays #ff4000 | Site CSS + served logo are #ff4000; the pack's orange varies by file, so it's flagged as an owner decision, not folded into tokens |
| D27 | 2026-10-02 | Owner-supplied ON-LIGHT SVGs (P03/P05/P06/P07/P09) stored as-is in `logo-pack-2026/svg/` | Vector lettering is exactly #ff4000; only P09 is fully vector (the others use a masked bitmap ring ≈#ff4e23–#ff5636); recorded as gaps, tokens unchanged |
