# DESIGN.md — Court of Moravia
> **Snapshot Date:** 26 Nov 2026

---

## 1. Core Design Principles & Rules

When generating UI, web pages, slide decks, or digital assets for **Court of Moravia (COM)**, strictly follow these rules:

1. **01 PURE BLACK CANVAS & WEB BLUR SURFACES:** Pure black (`#000000`) is the primary background canvas. In slide decks and static exports, surfaces remain solid `#000000`. On live web interfaces, translucent containers (`topbar`, `bottombar`, `SBOX`, cards, accordions) use `background: var(--blur-bg)` (`rgba(0, 0, 0, 0.5)`) paired with `backdrop-filter: blur(var(--blur-m))` (`1.25rem` / `20px`). Never use backdrop blur when generating PDFs or static posts.
2. **02 STRICT MONOCHROME + RED ACCENT SYSTEM:** Production systems use strictly Black (`#000000`), White (`#FFFFFF`), Grey (`#EBE7E0`, `#808080`, `#424242`), and the Red accent family (`#DF1717`, `#910606`).
   * **Structural Lines & Non-Interactive Elements:** Borders, hairline dividers, frame rules, and non-interactive decorative SVG shapes use `--color-grey-d` (`#424242`).
   * **Interactive Elements:** Buttons, links, active controls, and keyword highlights use `--color-red` (`#DF1717`).
3. **03 STRICT TEXT COLOR ROLES:**
   * **Headings (`h1`–`h6`):** Always pure white (`--color-white`, `#FFFFFF`), with optional inline highlight spans of **2–4 key words** emphasized in Red (`--color-red`, `#DF1717`).
   * **Body Text (`body`):** Always `--color-grey-l` (`#EBE7E0`) with `max-width: 66ch`.
   * **Secondary Labels / Eyebrows / Microtype:** `--color-grey` (`#808080`) or `--color-grey-l` (`#EBE7E0`).
4. **04 TYPOGRAPHY ROLES, SELF-HOSTED FONTS & MEASURE:** `Geist` is used exclusively for `h1` display titles, `body` text, and the bottom label of two-part CTA buttons. `Geist Mono` is used for everything else (`h2`–`h6`, box headers, ordered lists, navigation, and UI buttons). All text outside `body` copy uses `text-transform: uppercase`. Body paragraphs must never exceed `max-width: 66ch`.
   * **Font Embedding:** Never rely solely on external Google Fonts CDN during PDF generation; always load local self-hosted font files (`./fonts/`) via `@font-face` and embed them into exported PDFs.
5. **05 8PX SPACING SCALE, NUMBERING & MOTION:** All spacing and layout rhythm strictly follow multiples of `8px` (`0.5rem` increments: `8px`, `16px`, `24px`, `32px`, `40px`, `48px`, `56px`, `64px`, `72px`, `88px`, `96px`). Vertical gaps between `body` text and headings scale proportionally: at least `24px` below `h3`–`h6`, at least `40px` below `h2`, and at least `64px` below `h1`.
   * **Leading Zeros Convention:** Use a leading zero (`01`, `02`…) on numbered chapters, pages, or items **only** when the total count of those elements in the document exceeds 10; otherwise use unpadded numbers (`1`, `2`, `3`…).
   * **Transitions:** Interactive transitions use `transition: all .15s ease-in-out`.
6. **06 GEOMETRY CONTRAST (SHARP CONTAINERS VS. PILL CONTROLS):**
   * **Passive Structural Containers:** Cards, `SBOX`, `VERBOX`, `HORBOX`, accordions, inputs, and perimeter frames maintain strict `0px` (`--radius-none`) sharp corners. Composite blocks never carry an outer wrapper border as a whole.
   * **Interactive Buttons & Directional Controls:** Interactive action buttons and small directional controls use full pill/circular rounding (`border-radius: 999px`, `--radius-pill`) so they read immediately as clickable controls and contrast clearly against sharp `0px` passive containers.
   * **Export Format:** Client-facing presentations and documents must **always** be exported and delivered as **PDF**—never as `.pptx` or `.docx`.
7. **07 FUNCTIONAL MINIMALISM:** Zero decorative "tech larp" or terminal cosplay—never use `//`, `/`, or bracketed flavor text as inline dividers. Minimize eyebrow text (`h5` section numbers) to an absolute minimum.

---

## 2. Design Tokens

### Colors
| Token | Value | Role / Usage |
| :--- | :--- | :--- |
| `--color-black` | `#000000` | Primary background canvas and text inside filled buttons |
| `--color-grey-d` | `#424242` | Structural borders, frame lines, dividers, and non-interactive SVG shapes |
| `--color-grey` | `#808080` | Secondary labels, eyebrows, and `h2` trailing `↘` arrow |
| `--color-grey-l` | `#EBE7E0` | Primary `body` text color and light neutral surface |
| `--color-white` | `#FFFFFF` | `h1`–`h6` headers (with optional 2–4 word `--color-red` highlights) and main button fill |
| `--color-red-d` | `#910606` | Hover state for text links (`line-through`) and dark accent border |
| `--color-red-d-40` | `rgba(145, 6, 6, 0.40)` | Translucent hover surface tint for interactive rows and cards |
| `--color-red` | `#DF1717` | Primary interactive accent, links, secondary buttons, and keyword highlights |

### Typography
| Token | Value | Role / Usage |
| :--- | :--- | :--- |
| `--font-body` | `'Geist', sans-serif` | Display `h1`, `body` reading copy (`max-width: 66ch`), and two-part CTA label |
| `--font-header` | `'Geist Mono', monospace` | Technical headings `h2`–`h6`, box headers, lists, navigation, and UI buttons |
| `--font-size-h1` | `clamp(2.75rem, 8.33vw, 10rem)` | Hero display (`44px` → `160px`, `Geist` Light, `110%` line-height) |
| `--font-size-h2` | `clamp(2rem, 5vw, 6rem)` | Section display (`32px` → `96px`, `Geist Mono` Light, `110%` line-height) |
| `--font-size-h3` | `clamp(1.75rem, 3.33vw, 4rem)` | Technical display (`28px` → `64px`, `Geist Mono` ExtraLight, `110%` line-height) |
| `--font-size-h4` | `clamp(1.5rem, 2.5vw, 3rem)` | Sub-display / deck title (`24px` → `48px`, `Geist Mono` Light, `110%` line-height) |
| `--font-size-h5` | `clamp(1.25rem, 1.67vw, 2rem)` | Box headers `SBOX`/`VERBOX`/`HORBOX` (`20px` → `32px`, `Geist Mono` Regular, `+4%` tracking) |
| `--font-size-h6` | `clamp(1.125rem, 1.25vw, 1.5rem)` | Subheadings and ordered lists (`18px` → `24px`, `Geist Mono` Light, `130%` line-height) |
| `--font-size-body` | `clamp(1rem, 1.25vw, 1.5rem)` | Primary reading copy (`16px` → `24px`, `Geist` Regular, `130%` line-height) |
| `--font-size-micro` | `0.875rem` | Micro labels, navigation, buttons, and metadata (`14px`, `Geist Mono` Regular, `+4%` tracking) |

### Spacing (8px Fluid Grid)
| Token | Value | Role / Usage |
| :--- | :--- | :--- |
| `--space-1` | `0.5rem` | `8px` — Base grid increment, small icon-to-label gap |
| `--space-2` | `1rem` | `16px` — Button gaps, list/accordion gaps, compact padding |
| `--space-3` | `1.5rem` | `24px` — Minimum gap below `h3`–`h6`, box header vertical padding |
| `--space-4` | `clamp(1.5rem, 2vw, 2rem)` | `24px` → `32px` — Eyebrow-to-`h2` gap, `SBOX` inner padding |
| `--space-5` | `clamp(1.5rem, 2.5vw, 2.5rem)` | `24px` → `40px` — Minimum gap below `h2`, box header horizontal padding |
| `--space-6` | `clamp(1.5rem, 3vw, 3rem)` | `24px` → `48px` — Section vertical rhythm, `SBOX` body padding |
| `--space-7` | `clamp(2rem, 3.5vw, 3.5rem)` | `32px` → `56px` — `HORBOX` column gap, UI stack spacing |
| `--space-8` | `clamp(2rem, 4vw, 4rem)` | `32px` → `64px` — Minimum gap below `h1`, `VERBOX` vertical stack gap |
| `--space-9` | `clamp(2rem, 4.5vw, 4.5rem)` | `32px` → `72px` — Horizontal inner padding inside `VERBOX` and `HORBOX` |
| `--space-11` | `clamp(1.5rem, 5.5vw, 5.5rem)` | `24px` → `88px` — Section description horizontal inset |
| `--space-12` | `clamp(3rem, 6vw, 6rem)` | `48px` → `96px` — Outer container and major section padding |

### Blur, Border Width & Border Radius
| Token | Value | Role / Usage |
| :--- | :--- | :--- |
| `--blur-m` | `1.25rem` | `20px` — Web-only backdrop blur radius (never used in PDF/static exports) |
| `--blur-bg` | `rgba(0, 0, 0, 0.5)` | Translucent black surface fill paired with `backdrop-filter: blur(var(--blur-m))` |
| `--border-width-thin` | `1px` | Default hairline stroke for web borders, dividers, and frame rules |
| `--border-width-thick` | `2px` | Prominent stroke for `1920 × 1080` slide deck frames and print deliverables |
| `--radius-none` | `0px` | Mandatory sharp corners for all passive containers, cards, boxes, and frames |
| `--radius-pill` | `999px` | Full pill rounding reserved exclusively for interactive buttons and circular arrow controls |

---

## 3. Shapes & Marks (`./svgs/`)

All vector assets live in `./svgs/` and use `currentColor` so they dynamically inherit `--color-grey-d` (non-interactive) or `--color-red` (interactive). They are organized into 5 groups:

1. **Main:**
   * `./svgs/com-logo-full.svg` — Primary horizontal lockup (`max-width: 250px` in `INTRO` slides).
   * `./svgs/com-logo.svg` — Compact `COM` wordmark for headers and corner slots.
2. **Corners:**
   * Placed in diagonal pairs (`Top-Left + Bottom-Right` and `Top-Right + Bottom-Left`, `30px × 30px`) inside the `66px × 66px` corner cells: `com-d4.svg`, `com-d6.svg`, `com-d8.svg`, `com-d10.svg`, `com-d12.svg`, `com-d20.svg`, `com-aztec-a.svg`, `com-aztec-b.svg`, `com-c.svg`, `com-o.svg`, `com-m.svg`, `com-g.svg` (Guild decks only), `com-logo-alt.svg`.
3. **Rails:**
   * Rendered at `37px` height along lateral (`-90deg` left / `+90deg` right) and horizontal perimeter rails: `com-barcode-long.svg` (full-width rail when space permits), `com-barcode-short.svg` (compact rail fallback), `com-pdf417.svg`.
4. **Controls:**
   * `./svgs/com-arrow-big.svg` — Large directional arrow used exclusively for navigating across major page sections, full-screen steps, or pages.
   * `./svgs/com-arrow-small.svg` — Single small directional arrow SVG rotated via CSS (`0deg`, `90deg`, `180deg`, `-90deg`) as needed for intra-component navigation (carousels, local triggers).
   * `./svgs/com-radio.svg` & `./svgs/com-radio-active.svg` — Section and accordion progress nodes (`radio` changes color on hover via CSS without requiring a separate shape).
5. **Icons (Rare / Custom Human-Crafted):**
   * `./svgs/com-icon-coffee.svg`, `./svgs/com-icon-crown.svg`, `./svgs/com-icon-gear.svg`, `./svgs/com-icon-tool.svg`.
   * *Rule & Disclaimer:* These icons are vectorized glyphs from the Nerd Font build of `Geist Mono`. Do not bundle the full Geist Mono Nerd Font into repositories—these marks are used rarely and are crafted manually by a human (Kevin).

---

## 4. Web UI Components & Viewport Rules

### Topbar & Bottombar (Web Frame Chrome)
* Sticky outer bars (`min-height: 66px`) with `background: var(--blur-bg)`, `backdrop-filter: blur(var(--blur-m))`, `var(--border-width-thin) solid var(--color-grey-d)` inner rules, and corner mark slots.
* **Export Rule:** Backdrop blur (`--blur-m`) is strictly for live web interfaces—never use blur when generating PDFs or static social posts.

### Links (`<a>`)
* **Default:** `color: var(--color-red); text-decoration: underline;` with `::after { content: "↗"; }` directly attached to the link text to clearly indicate clickability.
* **Hover:** `color: var(--color-red-d); text-decoration-line: line-through;` (the `↗` remains attached).

### Buttons (Pill Geometry — `border-radius: var(--radius-pill)`)
* Interactive buttons and circular arrow controls are pill-rounded (`999px`) so they read as clickable buttons at first glance and contrast against sharp `0px` passive containers.
* **Main Button (Primary CTA):**
  * Default: `background-color: var(--color-white); border: var(--border-width-thin) solid var(--color-white); color: var(--color-black);`
  * Hover: `background-color: var(--color-black); border-color: var(--color-white); color: var(--color-white);`
* **Alt / Secondary Button:**
  * Default: `background-color: var(--color-red); border: var(--border-width-thin) solid var(--color-red); color: var(--color-black);`
  * Hover: `background-color: var(--color-black); border-color: var(--color-red); color: var(--color-red);`

### Canonical Box Surface (`SBOX`, `VERBOX`, `HORBOX`)
* Sharp `0px` (`--radius-none`) corners, `border: var(--border-width-thin) solid var(--color-grey-d)`, header text `var(--color-white)`, body text `var(--color-grey-l)`.
* **Web Surface:** `background: var(--blur-bg)` + `backdrop-filter: blur(var(--blur-m))`.
* **Static / PDF Surface:** Solid `#000000` background without blur.

### Accordion
* Sharp `0px` items stacked vertically (`gap: var(--space-2)`) on `var(--blur-bg)` + `blur(var(--blur-m))` with `var(--border-width-thin) solid var(--color-grey-d)`.
* **Hover:** Border shifts to `var(--color-red)` and background tints with `var(--color-red-d-40)`.
* **Active (Expanded):** Border highlights with `var(--color-red)` and reveals `body` copy (`max-width: 66ch`).

### Quote Carousel
* Centered `body` quote copy flanked by circular pill buttons (`border-radius: var(--radius-pill)`) housing `com-arrow-small.svg` (rotated left/right) and `com-radio` pagination nodes below.

### Team Card
* Two-column border-joined card (`0px` radius, `var(--border-width-thin) solid var(--color-grey-d)`): square `1:1` portrait on the left, `Geist Mono` name and `Geist` bio on the right.
* **Photography Filter Rule:** Team portraits are always rendered in high-contrast black & white via CSS: `filter: grayscale(100%) contrast(1.25);`.

### Client Logos
* Always monochrome SVG vectors colored in `var(--color-grey)` (`#808080`) with uniform optical height (`~40px`) and `var(--color-white)` on hover.

### Minimal Form
* Transparent input fields with no enclosing box—only a bottom border (`border-bottom: var(--border-width-thin) solid var(--color-grey-d)`), transitioning to `var(--color-red)` on `:focus`, paired with a pill submit button.

### Ambient Shader & Footer Curtain (Experimental — Web Only)
* **Status:** Experimental background layer for web properties only.
* **States:** Full-color animated 3D geometry on the opening Hero section; transitions to desaturated grayscale & darkened (`grayscale(100%) brightness(0.45)`) once the user scrolls into content sections.
* **Footer Darkening:** The final section of a web page applies a dark bottom gradient curtain (`linear-gradient(to top, #000000 0%, rgba(0,0,0,0.92) 40%, transparent 100%)`) so team cards, client logos, and legal info remain crisp and legible.

### Scroll Behavior
* **Locked (Section-Snap) Scroll:** Used exclusively on sales-focused **landing pages** where pacing a concise narrative is the goal.
* **Unlocked (Natural) Scroll:** Used on content-heavy web properties (documentation, articles, design system reference) and **always enforced on viewports `<= 960px`**.

---

## 5. Slide Deck Grid & Compositions (`1920 × 1080`)

* **Fixed Frame & Footer Guardrail:** Every slide uses a locked `1920 × 1080px` (`16:9`) perimeter frame (`66px` rails on all 4 sides, `overflow: hidden;`, `var(--border-width-thick)` border strokes). Content inside the center safe-zone must never overflow or push the bottom bar off the slide.
* **`INTRO` Slide:** Primary logo constrained to `max-width: 250px`, uppercase `h1` title (`--color-white`), and corner pair `com-logo.svg` + `com-d12.svg`.
* **`OUTRO` / Contact Slide Links:** Functional `mailto:` and `tel:+420712345678` links.
* **Core Compositions (12 Standard Layouts):** `INTRO`, `TEXT` (1–4 columns), `HEADLINE + VERBOX`, `HEADLINE + HORBOX` (max 1 per slide, max 3 columns), `HEADER + SBOX` (2, 3, or 2×2 cards), and `OUTRO`.

---

## 6. Strict Anti-Patterns (Do NOT Generate)
* **No rounded passive containers:** Never apply `border-radius` to cards, `SBOX` blocks, accordions, team cards, or frames (`0px` only; rounding is reserved strictly for interactive buttons and circular icon controls).
* **No multi-color rainbows:** Never introduce blue, green, yellow, or violet accents—stick strictly to Black, White, Greys, and the Red accent family.
* **No off-brand fonts:** Never substitute `Geist` or `Geist Mono` with Inter, Roboto, serif, or script fonts.
* **No blur in static exports:** Never use `backdrop-filter: blur()` in PDF decks or static social graphics.
* **No tech cosplay:** Never use "//" or similar decoration-only patterns between words or at the start of sections.
