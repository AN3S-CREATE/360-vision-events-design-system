# Logo pack 2026

Official 360 Vision Events logo files, supplied by the brand owner on 2026-10-02. They are byte-identical to the "360 Vision Events Logo 2026" pack in Claude Design and keep the original names below.

Every file is a 2000×2000 RGB PNG on a solid background (**not transparent**): white `#ffffff` for ON-LIGHT, pure black `#000000` for ON-DARK. On the site canvas (`#0b0b0c`) an ON-DARK square shows as a faint darker box. Crop the file or place it on a matching ground.

| File | Official name | Background | Dominant orange |
|---|---|---|---|
| `p03-primary-horizontal-divider-on-dark.png` | 360 Vision Events - Logo P03 Primary Horiz 360 Divider ON-DARK.png | `#000000` | `#fb1c00` |
| `p03-primary-horizontal-divider-on-light.png` | 360 Vision Events - Logo P03 Primary Horiz 360 Divider ON-LIGHT.png | `#ffffff` | `#fb1c00` |
| `p05-primary-horizontal-divider-on-dark.png` | 360 Vision Events - Logo P05 Primary Horiz 360 Divider ON-DARK.png | `#000000` | `#e22500` |
| `p05-primary-horizontal-divider-on-light.png` | 360 Vision Events - Logo P05 Primary Horiz 360 Divider ON-LIGHT.png | `#ffffff` | `#e22500` |
| `p06-stacked-full-colour-on-dark.png` | 360 Vision Events - Logo P06 Stacked Full Colour ON-DARK.png | `#000000` | `#f51900` |
| `p06-stacked-full-colour-on-light.png` | 360 Vision Events - Logo P06 Stacked Full Colour ON-LIGHT.png | `#ffffff` | `#f51900` |
| `p07-mark-360-on-dark.png` | 360 Vision Events - Logo P07 Mark 360 ON-DARK.png | `#000000` | `#ff3500` |
| `p07-mark-360-on-light.png` | 360 Vision Events - Logo P07 Mark 360 ON-LIGHT.png | `#ffffff` | `#ff3500` |
| `p09-wordmark-360vision-on-dark.png` | 360 Vision Events - Logo P09 Wordmark 360VISION ON-DARK.png | `#000000` | `#f14624` |
| `p09-wordmark-360vision-on-light.png` | 360 Vision Events - Logo P09 Wordmark 360VISION ON-LIGHT.png | `#ffffff` | `#f14624` |
| `p12-primary-horizontal-divider-on-dark.png` | 360 Vision Events - Logo P12 Primary Horiz 360 Divider ON-DARK.png | `#000000` | `#ff3e00` |

**Orange varies between files.** The values range from `#e22500` (P05) to `#ff3e00` (P12), and the wordmark "360" is `#f14624` (P09). The website's CSS and its served logo both use `#ff4000`, which stays the UI brand colour (`--color-brand`). P12 (`#ff3e00`) is the closest match. Aligning the pack to one orange is an open decision for the brand owner (see DESIGN.md §9).

## SVG versions (`svg/`)

The brand owner supplied five ON-LIGHT SVGs on 2026-10-02. All are transparent (no background) and contain no scripts or external links.

| File | Type | Vector fills | Embedded bitmap |
|---|---|---|---|
| `svg/p09-wordmark-360vision-on-light.svg` | **fully vector** | `#ff4000` "360", `#000000` VISION, `#828282` EVENTS | none |
| `svg/p03-primary-horizontal-divider-on-light.svg` | hybrid | `#ff4000` "360", `#000000` VISION, `#737373` EVENTS | ring 407×376 (≈`#ff502b`), divider 32×345 |
| `svg/p05-primary-horizontal-divider-on-light.svg` | hybrid | same as P03 | ring 438×407 (≈`#ff5636`), divider 64×345 |
| `svg/p06-stacked-full-colour-on-light.svg` | hybrid | same as P03 | ring 595×594 (≈`#ff502b`) |
| `svg/p07-mark-360-on-light.svg` | hybrid | `#ff4000` "360" | ring 845×845 (≈`#ff4e23`) |

What this means:
- **The SVG lettering matches the site exactly.** The "360" is `#ff4000` in every SVG, which the PNGs are not.
- **The P09 wordmark is the only fully scalable file.** The other four draw the aperture ring (and the divider) as a masked bitmap of 400–850 px. Those parts won't stay sharp when enlarged, and the ring is slightly lighter than the "360" beside it.
- **The two greys differ.** "EVENTS" is `#737373` in P03/P05/P06 and `#828282` in P09.
- **Missing versions.** There are no SVGs for the ON-DARK versions or for P12.

Asking the designer for a fully vector ring in `#ff4000` would make every mark scalable and consistent.

For web UI on the dark canvas, the transparent `../logo-horiz-ON-DARK.png` (exactly `#ff4000`) is the safest choice. Use the pack for print, social and partner material, picking ON-DARK or ON-LIGHT to match the ground. Don't recolour, redraw or trace the marks; no SVG exists.
