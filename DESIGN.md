# DESIGN.md — Court of Moravia

> **System Essence:** A technical frame. A human purpose.
> **Core Motto:** WE CHANGE THE GAME OF BUSINESS / WE DELIVER CHANGE IN COMPANIES
> **Snapshot Date:** 26 Nov 2026

---

## 1. Core Design Principles & Rules

When generating UI, web pages, slide decks, or digital assets for **Court of Moravia (COM)**, strictly follow these 5 rules:

1. **01 / PALETTE:** Use pure black (`#000000`) and pure white (`#FFFFFF`) as the primary field, paired with the red accent family (`--color-red-d`, `--color-red`, `--color-red-l`) and neutral greys (`--color-grey-d`, `--color-grey-l`).
2. **02 / HIERARCHY:** Pair large, light, uppercase headlines (`Geist`) with clean, sentence-case body copy (`Geist`). Use monospaced type (`Geist Mono`) for technical labels, headings (`h3`–`h6`), metadata, and navigational details.
3. **03 / COMPOSITION:** Align elements to a clear, crisp edge and protect generous negative space. Keep ornamental borders, ticks, and technical framing confined to the outer perimeter, well away from the core message.
4. **04 / GEOMETRY:** Maintain strict `0px` sharp corners on all passive structural containers, cards, boxes, and frames. Interactive action buttons and small directional/control indicators use full pill/circular rounding (`999px`) so they read immediately as clickable controls.
5. **05 / LEGIBILITY:** Use pure white (`#FFFFFF`) or `--color-grey-l` for readable text on dark backgrounds. Always verify contrast at the final rendered size, especially over translucent or shader surfaces.

---

## 2. Color & Surface Tokens

### Neutrals, Surfaces & Blur
| Token | Value | Role / Usage |
| :--- | :--- | :--- |
| `--color-black` | `#000000` | Primary background / dark field |
| `--color-grey-d` | `#424242` | Technical borders, frame lines, dividers, card outlines |
| `--color-grey-l` | `#EBE7E0` | Secondary body copy, muted light fill |
| `--color-white` | `#FFFFFF` | Primary light text / main CTA fill |
| `--blur-m` | `20px` | Standard web backdrop blur radius (web-only; never use in PDF/static posts) |
| `--blur-bg` | `rgba(0, 0, 0, 0.5)` | Translucent dark surface fill paired with `backdrop-filter: blur(var(--blur-m))` |

### Red Accent Family
| Token | Hex | Role / Usage |
| :--- | :--- | :--- |
| `--color-red-d` (`--accent-d`) | `#910606` | Hover state for links (`line-through`), deep accent borders |
| `--color-red` (`--accent`) | `#DF1717` | Primary interactive accent, secondary buttons, active indicators, default links |
| `--color-red-l` (`--accent-l`) | `#F65656` | High-contrast light accent highlights |

---

## 3. Typography System

### Font Families
* `--font-body`: `'Geist', sans-serif` (Major display headlines `h1`–`h2` and primary body copy)
* `--font-header`: `'Geist Mono', monospace` (Technical headings `h3`–`h6`, UI controls, buttons, labels, microtype)

### Type Scale & Styles
| Style / Role | Font Family | Weight | Size | Line Height | Tracking | Case / Usage |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `h1` | Geist | Light (300) | `160px` | `110%` | `0%` | UPPERCASE — Hero display |
| `h2` | Geist | Light (300) | `96px` | `110%` | `0%` | UPPERCASE — Section display |
| `h3` | Geist Mono | ExtraLight (200) | `64px` | `110%` | `0%` | UPPERCASE — Technical display |
| `h4` | Geist Mono | Light (300) | `48px` | `110%` | `0%` | UPPERCASE — Sub-display / Deck titles |
| `h5` | Geist Mono | Regular (400) | `32px` | `110%` | `+4%` | UPPERCASE — Card / Block headers |
| `h6` | Geist Mono | Light (300) | `24px` | `130%` | `+1%` | Technical subheadings |
| `body` | Geist | Regular (400) | `24px` | `130%` | `0%` | Sentence case — Primary reading copy (`max-width: 66ch`) |
| `micro` | Geist Mono | Regular (400) | `14px` | `110%` | `+4%` | UPPERCASE — Captions, tags, border codes |

### Extended Numeric Scale & Stroke Tokens
* **Display Scale:** `tera: 88px`, `giga: 72px`, `mega: 64px`, `kilo: 56px`, `micro: 48px`, `nano: 40px`, `pico: 32px`, `femto: 24px`
* **Stroke / Border Weight:** `1px` default hairline border (`--stroke-thin: 1px`), `2px` for prominent UI controls (`--stroke-base: 2px`)

---

## 4. Shapes & Marks (`svgs/`)

All vector marks use `currentColor` or monochrome white/grey fills and are organized into 5 functional groups:

1. **Main:**
   * `com-logo-full.svg` — Primary horizontal lockup with "MADE BY COURT OF MORAVIA EXPERT GUILD".
   * `com-logo.svg` — Compact `COM` wordmark for navigation bars and tight headers.
2. **Corners:**
   * Placed strictly in the four corner slots of the outer technical frame (`30px` standard height): `com-d4.svg`, `com-d6.svg`, `com-d8.svg`, `com-d10.svg`, `com-d12.svg`, `com-d20.svg`, `com-c.svg`, `com-o.svg`, `com-m.svg`, `com-g.svg`, `com-aztec-a.svg`, `com-aztec-b.svg`, `com-logo-alt.svg`.
3. **Rails:**
   * Placed along lateral (`-90deg` / `+90deg`) and horizontal perimeter rails (`30px` height): `com-barcode-long.svg`, `com-barcode-short.svg`, `com-pdf417.svg`.
4. **Controls:**
   * `com-arrow-big.svg` — Large directional arrow used exclusively for navigating across major page sections, full-screen steps, or pages.
   * `com-arrow-small.svg` — Single small directional arrow SVG rotated via CSS (`rotate(0deg / 90deg / 180deg / -90deg)`) as needed for local component controls (carousels, accordions, inline triggers).
   * `com-radio.svg`, `com-radio-hover.svg`, `com-radio-active.svg` — Section/step progress indicator nodes.
5. **Icons (Rare / Custom Human-Crafted):**
   * `com-icon-coffee.svg`, `com-icon-crown.svg`, `com-icon-gear.svg`, `com-icon-tool.svg`.
   * *Rule & Disclaimer:* These glyphs are vectorized characters from the Nerd Font build of `Geist Mono`. Do not bundle the full Nerd Font into repositories; these icons are used rarely and must be prepared manually by a human designer (Kevin).

---

## 5. Slide Deck & Structural Primitives

* **Canonical Box Surface (`SBOX`, `HORBOX`, `VERBOX`, `ROADMAP`, `GOALS`):**
  * Border: `1px solid var(--color-grey-d)` (or `2px` where emphasized), `border-radius: 0px`.
  * Text: `var(--color-grey-l)` for body copy, `var(--color-white)` for headers.
  * Background: `var(--blur-bg)` (`rgba(0, 0, 0, 0.5)`) with `backdrop-filter: blur(var(--blur-m))` on web surfaces (solid `#000000` in PDF/static exports).
* **`INTRO`:** Minimal dark canvas with uppercase `Geist` Light display title (`h1`/`h2`) and bottom `COURT OF MORAVIA` attribution.
* **`CHAPTER`:** Full-bleed solid `var(--accent)` background with `#000000` uppercase display typography.
* **`TEXT`:** Left-aligned uppercase statement headline paired with a `body` paragraph (`max-width: 66ch`).

---

## 6. Web UI Components & Viewport Rules

### Topbar & Bottombar (Web Frame Chrome)
* Fixed/sticky outer bars with `background: var(--blur-bg)`, `backdrop-filter: blur(var(--blur-m))`, `1px solid var(--color-grey-d)` inner rules, and corner mark slots.
* **Export Rule:** Blur (`--blur-m`) is strictly for live web interfaces—never use backdrop blur when generating PDFs or static social posts.

### Links (`<a>`)
* **Default:** `color: var(--accent); text-decoration: underline;` with an attached `::after { content: "↗"; }` directly affixed to the link text to signal clickability.
* **Hover:** `color: var(--accent-d); text-decoration: line-through;` (the `↗` remains attached).

### Buttons (Pill Geometry — `border-radius: 999px`)
* Interactive buttons and small directional controls are rounded (`999px`) so they read unmistakably as interactive controls and contrast clearly against sharp `0px` passive containers.
* **Main Button (Primary CTA):**
  * Default: `background: var(--color-white); border: 2px solid var(--color-white); color: var(--color-black);`
  * Hover: `background: var(--color-black); border-color: var(--color-white); color: var(--color-white);`
* **Secondary / Other Buttons:**
  * Default: `background: var(--accent); border: 2px solid var(--accent); color: var(--color-black);`
  * Hover: `background: var(--color-black); border-color: var(--accent); color: var(--accent);`

### Accordion
* Sharp `0px` rectangular items stacked vertically on `var(--blur-bg)` + `blur(var(--blur-m))` with `1px solid var(--color-grey-d)`.
* **Hover:** Border shifts to `var(--accent)` and header highlights.
* **Active (Expanded):** Header/frame highlights with `var(--accent)` and reveals `body` text (`max-width: 66ch`).

### Quote Carousel
* Centered `body` quote copy flanked by circular pill buttons containing `com-arrow-small.svg` (rotated left/right) and bottom pagination indicators (`com-radio*.svg` or pill dots).

### Team Card
* Two-column border-joined card (`0px` radius, `1px solid var(--color-grey-d)`): square `1:1` portrait on the left, `Geist Mono` name/role/contact details on the right.
* **Photography Filter Rule:** Team portraits must always be rendered in high-contrast black & white via CSS: `filter: grayscale(100%) contrast(1.25);`.

### Client Logos
* Always monochrome SVG vectors colored in `var(--color-grey-l)` / `var(--color-grey-d)` with uniform optical height (`~40px`) and full white (`#FFFFFF`) on hover.

### Minimal Form
* Transparent input fields with no enclosing box—only a bottom border (`border-bottom: 1px solid var(--color-grey-d)`), transitioning to `var(--accent)` on `:focus`, paired with a rounded pill submit button.

### Ambient Shader & Footer Curtain (Experimental — Web Only)
* **Status:** Experimental background layer for web properties only.
* **States:** Full-color distorted 3D geometry on the opening Hero section; transitions to desaturated grayscale & darkened (`grayscale(100%) brightness(0.45)`) once the user scrolls into content sections.
* **Footer Darkening:** The final section/footer applies a dark bottom gradient curtain (`linear-gradient(to bottom, transparent, rgba(0,0,0,0.92))`) so dense contact info, team cards, and client logos remain crisp and legible.

### Scroll Behavior
* **Locked (Section-Snap) Scroll:** Used exclusively on sales-focused **landing pages** where pacing a concise narrative is the primary goal.
* **Unlocked (Natural) Scroll:** Used on content-heavy web properties (documentation, articles, design system reference) and **always enforced on viewports `<= 960px`**.

---

## 7. Strict Anti-Patterns (Do NOT Generate)
* **No rounded passive containers:** Never apply `border-radius` to cards, `SBOX` blocks, accordions, team cards, or frames (`0px` only; rounding is reserved strictly for interactive buttons and circular icon controls).
* **No multi-color rainbows:** Never introduce blue, green, yellow, or violet accents—stick strictly to Black, White, Greys, and the Red accent family.
* **No off-brand fonts:** Never substitute `Geist` or `Geist Mono` with Inter, Roboto, serif, or script fonts.
* **No blur in static exports:** Never use `backdrop-filter: blur()` in PDF decks or static social graphics.
