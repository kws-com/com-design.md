# DESIGN.md — Court of Moravia

> **System Essence:** A technical frame. A human purpose.
> **Core Motto:** WE CHANGE THE GAME OF BUSINESS / WE DELIVER CHANGE IN COMPANIES
> **Snapshot Date:** 16 Nov 2026

---

## 1. Core Design Principles & Rules

When generating UI, web pages, slide decks, or digital assets for **Court of Moravia (COM)**, strictly follow these rules:

1. **01 PURE BLACK CANVAS ONLY:** Pure black (`#000000`) is the **only** surface background color used across pages, slides, `verbox`, `horbox`, `sbox`, color chips, and layout containers. Never use `#121212` (`black-l`) inside boxes or cards—the only exception is button and interactive hover states (`rgba(accent-d, 0.40)`).
2. **02 ACCENT ROLES & COLOR USAGE RULES:** Choose **one accent family per composition** (defaulting to **Red** `#DF1717`). The canonical palette sequence is: **Red, Blue, Green, Orange, Yellow, Teal, Violet, White + Grey, Black**.
   * **Single-Accent Documents (≤ 20 pages and ≤ 5 chapters):** The entire document uses **one single accent family** from start to finish (defaulting to Red).
   * **Multi-Chapter Long Documents (> 20 pages and/or > 5 explicitly named chapters):** `INTRO` and `OUTRO` (contacts / about us) sections use **Red**, while inner chapters progress sequentially through the canonical palette order: **Blue → Green → Orange → Yellow → Teal → Violet**.
   * **Interactive Elements:** Every interactive element uses `--accent-l` (or transitions to `--accent-l` on hover).
   * **Structural Lines & Decorative Elements:** Every border, hairline divider, and non-textual decorative element uses `--accent-d`—except color swatches, which inherit the border color of the swatch itself.
3. **03 STRICT TEXT COLOR ROLES:** Pure white (`#FFFFFF`) is strictly reserved for `h1`–`h3` headers and `body` text (plus the value breakdown inside color chips). All other text, eyebrows, labels, and subheadings (`h4`–`h6`, `micro`) must use `grey-l` (`#E8E5E0`) or `--accent` / `--accent-l`.
4. **04 TYPOGRAPHY ROLES, SELF-HOSTED FONTS & MEASURE:** `Geist` is used exclusively for `h1` display titles, `body` text, and the bottom label of CTA buttons. `Geist Mono` is used for everything else (`h2`–`h6`, box headers, ordered lists, navigation, and standard buttons). All text outside `body` copy uses `text-transform: uppercase`. Body paragraphs must never exceed `max-width: 66ch`.
   * **Font Embedding:** Never rely solely on external Google Fonts CDN during PDF generation; always load local self-hosted font files (`./fonts/`) via `@font-face` and embed them into exported PDFs.
5. **05 SPACING, NUMBERING & MOTION:** Standard spacing is strictly based on multiples of `8px` (`0px` or minimum `8px`, typically larger). Vertical gaps between `body` text and headings scale proportionally: at least `24px` below `h3`–`h6`, at least `40px` below `h2`, and at least `64px` below `h1`.
   * **Leading Zeros Convention:** Use a leading zero (`01`, `02`...) on numbered chapters, pages, or items **only** when the total count of those elements in the document exceeds 10; otherwise use unpadded numbers (`1`, `2`, `3`...).
   * **Transitions:** Interactive transitions use `transition: all .15s ease-in-out`—no excessive animations.
6. **06 GEOMETRY, BOUNDARIES & EXPORT FORMAT:** Favor flat, angular marks and crisp `0px` border-radius rectangular framing. Composite components (`horbox`, `verbox`, `sbox`, `cta-button`, ordered lists) **never have an outer wrapper border as a whole**. Global outline/stroke alignment is **center** (`outline-offset: 0`). For non-web deliverables (slide decks, print), standard border stroke width is `2px`.
   * **Mandatory PDF Export:** Client-facing presentations and documents must **always** be exported and delivered as **PDF**—never as `.pptx` or `.docx`, which break font embedding and layout consistency across operating systems.
7. **07 FUNCTIONAL MINIMALISM & WEB LINKS:** Zero decorative "tech larp" or terminal cosplay—do not use `//`, `/`, or bracketed flavor text as inline dividers. Minimize eyebrow text (`h5` section numbers) to an absolute minimum.
   * **Web Link Hover:** Standard `<a>` links on web pages use `color: var(--accent-d); text-decoration-line: line-through;` on hover.

---

## 2. Color System (26 Variables)

*Strict sequence: Red (default), Blue, Green, Orange, Yellow, Teal, Violet, White + Grey, Black.*

### Accent Families (3-Column Rows: `-L` · Base · `-D`)
| Family | Light (`-L` · Interactive) | Base (Primary) | Dark (`-D` · Lines/Borders) |
| :--- | :--- | :--- | :--- |
| **Red (Default)** | `#F65656` | `#DF1717` | `#910606` |
| **Blue** | `#9EC4FA` | `#196FE6` | `#063B91` |
| **Green** | `#9EFAB0` | `#1AE51A` | `#067008` |
| **Orange** | `#FFB899` | `#FF5500` | `#913606` |
| **Yellow** | `#FFEE99` | `#E5C41A` | `#917806` |
| **Teal** | `#9EF2FA` | `#14A9B8` | `#068691` |
| **Violet** | `#A99EFA` | `#8019E5` | `#4D0691` |

### Neutrals & Surfaces
| Token | Hex | Strict Usage Role |
| :--- | :--- | :--- |
| `--color-white` | `#FFFFFF` | **Restricted:** `h1`–`h3` headers and `body` text only |
| `--color-grey-l` | `#E8E5E0` | Secondary text, box headers, labels, and `h2` trailing `↘` arrow |
| `--color-grey-d` | `#808080` | Muted neutral reference |
| `--color-black-l` | `#121212` | Reserved token only — never used as a card or box background |
| `--color-black` | `#000000` | Universal background canvas and primary filled-element text |

---

## 3. Typography System

### Font Families & Local Packages
* `--font-body`: `'Geist', sans-serif` — Used **only** for `h1`, `body` text, and the lower CTA button label. (Downloadable bundle: `./fonts/geist.zip`).
* `--font-header`: `'Geist Mono', monospace` — Used for **everything else** (`h2`–`h6`, box headers, ordered lists, navigation, and standard buttons). (Downloadable bundle: `./fonts/geist-mono.zip`).

### Type Scale & Color Rules
| Style / Role | Font Family | Weight | Size | Line Height | Tracking | Color | Case |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `h1` | Geist | Light (300) | `160px` | `110%` | `0%` | `#FFFFFF` | UPPERCASE |
| `h2` | Geist Mono | Light (300) | `96px` | `110%` | `0%` | `#FFFFFF` (with `grey-l` `↘`) | UPPERCASE |
| `h3` | Geist Mono | ExtraLight (200) | `64px` | `110%` | `0%` | `#FFFFFF` | UPPERCASE |
| `h4` | Geist Mono | Light (300) | `48px` | `110%` | `0%` | `grey-l` or `--accent-l` | UPPERCASE |
| `h5` | Geist Mono | Regular (400) | `32px` | `110%` | `+4%` | `grey-l` or `--accent-l` | UPPERCASE |
| `h6` | Geist Mono | Light (300) | `24px` | `130%` | `+1%` | `grey-l` or `--accent-l` | UPPERCASE |
| `body` | Geist | Regular (400) | `24px` | `130%` | `0%` | `#FFFFFF` (`max-width: 66ch`) | Sentence case |
| `micro` | Geist Mono | Regular (400) | `14px` | `110%` | `+4%` | `grey-l` or `--accent-l` | UPPERCASE |

### Proportional Heading-to-Body Spacing (8px Grid)
* `h1` → `body`: minimum `64px` gap
* `h2` → `body`: minimum `40px` gap (in section headers, `body` sits inside `padding: 56px 88px 24px`)
* `h3`–`h6` → `body`: minimum `24px` gap

---

## 4. Brand Marks, `currentColor` & Corner Pairing Rules (`./svgs/`)

* **SVG Coloring (`fill="currentColor"`):** Source SVG files in `./svgs/` use `fill="black"`. Whenever injecting an SVG into HTML, CSS, or Figma/Illustrator exports, switch `fill` to `currentColor` (or the active hex color) so marks dynamically inherit the active accent color.
* **Primary Full-Width Lockup:** `./svgs/com-logo-full.svg` — Spans `width: 100%` in showcases; in `INTRO` slides, constrain to `max-width: 250px`.
* **Guild Emblem (`./svgs/com-g.svg`):** Used **exclusively** in Guild presentations when explicitly requested by the prompt author—never in standard CoM decks.
* +* **Edge & Perimeter Ornaments (4 Files):**
* `./svgs/com-barcode-long.svg` — Displays centered along any stretched edge rail (**top, bottom, left, or right**) **only when there is sufficient space** for its full length (rotated `90deg` on vertical left edge or `-90deg` on vertical right edge).
* `./svgs/com-barcode-short.svg` — Automatic compact fallback displayed along any stretched edge rail whenever space is too narrow for `com-barcode-long.svg`.
* `./svgs/com-logo-alt.svg` — Pixel/modular `COM` wordmark displayed **exclusively on the bottom edge** (footer / bottom slide rail).
* `./svgs/com-pdf417.svg` — High-density 2D barcode block displayed **exclusively on the bottom edge** (footer / bottom slide rail).
* **Chapter / Section Corner Pairing Protocol:**
  * Corner marks are placed in diagonal pairs (`Top-Left + Bottom-Right` share Mark A; `Top-Right + Bottom-Left` share Mark B) and **stay constant across all slides within a single chapter/section**.
  * **Default `INTRO` / Chapter 1 Pair:** `com-logo.svg` + `com-d12.svg`.
  * **Subsequent Chapters Progression:**
    * Slot A cycles sequentially through the identity letters: `com-logo.svg` → `com-c.svg` → `com-o.svg` → `com-m.svg` → `com-logo.svg` (repeating).
    * Slot B selects randomly from the polyhedral dice pool `{com-d2.svg, com-d6.svg, com-d8.svg, com-d10.svg, com-d20.svg}` **excluding** `com-d12.svg` and the currently active die (preventing consecutive sections from sharing the same die).

---

## 5. Slide Deck Grid, Overflow Protection & Compositions (`1920 × 1080`)

* **Fixed Frame & Footer Guardrail:** Every slide uses a locked `1920 × 1080px` (`16:9`) grid (`grid-template-rows: 66px 1fr 66px; overflow: hidden;`). Content inside the center `1fr` safe-zone must **never** overflow or push the bottom bar off the slide—if content exceeds the safe height, split it across two slides.
* **`INTRO` Slide:** Features the primary logo constrained to `max-width: 250px`, uppercase `h1` title (`#FFFFFF`), and corner pair `com-logo.svg` + `com-d12.svg`.
* **`OUTRO` / Contact Slide Links:** All email and phone buttons must be functional interactive links (`mailto:name@courtofmoravia.com` and `tel:+420712345678` without spaces in the `href`, while displaying formatted spaces `+420 712 345 678` in the UI).

### Core Slide Compositions
1. **`TEXT` Slide (1 to 4 Columns):**
   * Header block (`[optional number]` + `[h2 title ↘]` + `[strongly recommended subtitle]`), followed by a right-aligned text container:
     * **4 columns:** Spans the full slide width.
     * **3 columns:** Text blocks stretch (`flex: 1`) to fill the full width.
     * **2 columns:** Enforces `max-width: 66ch` per column and aligns right, creating deliberate negative space on the left.
2. **`HEADLINE + VERBOX` Slide:**
   * `VERBOX` aligns flush with the start of the headline (`h2`), with an optional section number overhanging above. The `VERBOX` carries its own core thesis in `verbox-header` (`width: fit-content`, `padding: 24px 48px`), followed by vertically stacked text blocks (`gap: 64px`) with optional `h6` subheaders.
3. **`HEADLINE + HORBOX` Slide:**
   * Maximum **1 `HORBOX` per slide**, containing up to **3 horizontal columns** (`gap: 56px`). The `horbox-header` states the overarching thesis, while each column expands a specific aspect with its own `h6` header (`24px` gap to `body`).
4. **`HEADER + SBOX` Slide:**
   * Used for **2 to 4** standalone pillars/theses following the main slide headline: either **2–3 cards in a single row** or a **2×2 grid**. All `SBOX` cards on a slide must share **equal height** (either by editing copy to match length or stretching grid rows via `align-items: stretch` so bottom borders align cleanly without jagged steps).

---

## 6. Component Specifications (No Outer Wrapper Borders)

* **Main Button:** `color: #000000`, `background-color: var(--accent-l)`, `border: 1px solid var(--accent-l)`, `font-family: 'Geist Mono'`, `text-transform: uppercase`. Hover: `color: var(--accent-l)`, `background-color: rgba(var(--accent-d), 0.40)`.
* **Side Button:** `color: var(--accent-l)`, `background-color: #000000`, `border: 1px solid var(--accent-l)`, `font-family: 'Geist Mono'`, `text-transform: uppercase`. Hover: `color: var(--accent-l)`, `background-color: rgba(var(--accent-d), 0.40)`.
* **Two-Part `CTA` Button:** Top hug frame (`padding: 24px 40px`, `#000000`, `1px solid var(--accent-d)`, `h6` `--accent-l`) + bottom frame (`padding: 40px 48px`, `var(--accent-l)`, `Geist` `32px` Medium underlined `#000000`).
* **`VERBOX` / `HORBOX` Header:** `width: fit-content`, `padding: 24px 48px`, `border: 1px solid var(--accent-d)`, `background-color: #000000`, `color: var(--color-grey-l)` (`h5` `32px` `Geist Mono` uppercase).
* **`SBOX` Header:** `width: 100%`, `padding: 24px 40px`, `border: 1px solid var(--accent-d)`, `background-color: #000000`, `color: var(--color-grey-l)` (`h5` `32px` `Geist Mono` uppercase).
* **Ordered Lists:** Left hugging number cell (`padding: 24px`, `1px solid var(--accent-d)`, `#000000`, `h6` regular `--accent-l`, no trailing dot) + right full-bordered text cell (`padding: 24px 48px`, `1px solid var(--accent-d)`, `#000000`, `h6` regular uppercase `--accent-l`).
