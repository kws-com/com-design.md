# DESIGN.md — Court of Moravia

> **System Essence:** A technical frame. A human purpose.
> **Core Motto:** WE CHANGE THE GAME OF BUSINESS / WE DELIVER CHANGE IN COMPANIES
> **Snapshot Date:** 20 Nov 2026

---

## 1. Core Design Principles & Rules

When generating UI, web pages, slide decks, or digital assets for **Court of Moravia (COM)**, strictly follow these rules:

1. **01 PURE BLACK CANVAS ONLY:** Pure black (`#000000`) is the **only** surface background color used across pages, slides, `verbox`, `horbox`, `sbox`, color chips, and layout containers. Never use `#121212` (`black-l`) inside boxes or cards—the only exception is button and interactive hover states (`rgba(red-d, 0.40)`).
2. **02 STRICT MONOCHROME + RED ACCENT SYSTEM (NON-RED ACCENTS FORBIDDEN FOR AGENTS):**
   * **Demonstrative Only:** Extended accent families (`Blue`, `Green`, `Orange`, `Yellow`, `Teal`, `Violet`) exist in the system **exclusively for demonstrative showcase purposes** and must **never** be used by AI agents in production decks, websites, or assets.
   * **Structural Lines & Non-Interactive Elements:** Every border, hairline divider, frame rule, and non-interactive decorative SVG shape uses `--color-grey-d` (`#424242`).
   * **Interactive Elements:** Every interactive element (buttons, links, active controls, triggers) uses `--color-red` (`#DF1717`).
   * **Hover States:** Every hoverable element uses `--color-red-d` (`#910606`) as its base/resting state or border and transitions to `--color-red` (`#DF1717`) (with `rgba(145, 6, 6, 0.40)` fill where applicable) on hover.
3. **03 STRICT TEXT COLOR ROLES:**
   * **Headings (`h1`–`h6`):** Always pure white (`#FFFFFF`), with optional inline highlight spans of **2–4 key words** emphasized in `--color-red` (`#DF1717`).
   * **Body Text (`body`):** Always `--color-grey-l` (`#EBE7E0`) with `max-width: 66ch`.
   * **Secondary Labels / Eyebrows / Microtype:** `--color-grey` (`#808080`) or `--color-grey-l` (`#EBE7E0`).
4. **04 TYPOGRAPHY ROLES, SELF-HOSTED FONTS & MEASURE:** `Geist` is used exclusively for `h1` display titles, `body` text, and the bottom label of CTA buttons. `Geist Mono` is used for everything else (`h2`–`h6`, box headers, ordered lists, navigation, and standard buttons). All text outside `body` copy uses `text-transform: uppercase`. Body paragraphs must never exceed `max-width: 66ch`.
   * **Font Embedding:** Never rely solely on external Google Fonts CDN during PDF generation; always load local self-hosted font files (`./fonts/`) via `@font-face` and embed them into exported PDFs.
5. **05 SPACING, NUMBERING & MOTION:** Standard spacing is strictly based on multiples of `8px` (`0px` or minimum `8px`, typically larger). Vertical gaps between `body` text and headings scale proportionally: at least `24px` below `h3`–`h6`, at least `40px` below `h2`, and at least `64px` below `h1`.
   * **Leading Zeros Convention:** Use a leading zero (`01`, `02`...) on numbered chapters, pages, or items **only** when the total count of those elements in the document exceeds 10; otherwise use unpadded numbers (`1`, `2`, `3`...).
   * **Transitions:** Interactive transitions use `transition: all .15s ease-in-out`—no excessive animations.
6. **06 GEOMETRY, BOUNDARIES & EXPORT FORMAT:** Favor flat, angular marks and crisp `0px` border-radius rectangular framing. Composite components (`horbox`, `verbox`, `sbox`, `cta-button`, ordered lists) **never have an outer wrapper border as a whole**. Global outline/stroke alignment is **center** (`outline-offset: 0`). For non-web deliverables (slide decks, print), standard border stroke width is `2px`.
   * **Mandatory PDF Export:** Client-facing presentations and documents must **always** be exported and delivered as **PDF**—never as `.pptx` or `.docx`, which break font embedding and layout consistency across operating systems.
7. **07 FUNCTIONAL MINIMALISM & WEB LINKS:** Zero decorative "tech larp" or terminal cosplay—do not use `//`, `/`, or bracketed flavor text as inline dividers. Minimize eyebrow text (`h5` section numbers) to an absolute minimum.
   * **Web Link Hover:** Standard `<a>` links on web pages use `--color-red-d` (`#910606`) resting or hover state transitioning to `--color-red` (`#DF1717`) with `text-decoration-line: line-through;` on hover.

---

## 2. Color System (26 Variables)

*Strict sequence: Red (active), Blue, Green, Orange, Yellow, Teal, Violet (demonstrative showcase only), White + Grey, Black.*

### Neutrals & Production Surfaces
| Token | Hex | Strict Usage Role |
| :--- | :--- | :--- |
| `--color-white` | `#FFFFFF` | `h1`–`h6` headers (with optional 2–4 word `--color-red` highlights) |
| `--color-grey-l` | `#EBE7E0` | Primary `body` text color and high-contrast light surface |
| `--color-grey` | `#808080` | Muted technical labels, eyebrows, and `h2` trailing `↘` arrow |
| `--color-grey-d` | `#424242` | **All structural borders, frame lines, dividers, and non-interactive SVG shapes** |
| `--color-black-l` | `#121212` | Reserved token only — never used as a card or box background |
| `--color-black` | `#000000` | Universal background canvas and primary filled-button text |

### Production Accent (`Red`) & Demonstrative-Only Families
| Family | Light (`-L`) | Base (Primary) | Dark (`-D`) | Agent Usage Policy |
| :--- | :--- | :--- | :--- | :--- |
| **Red** | `#F65656` | `#DF1717` | `#910606` | **ACTIVE PRODUCTION ACCENT** (`Base` = interactive & keyword highlights; `-D` = hover base) |
| **Blue** | `#9EC4FA` | `#196FE6` | `#063B91` | *Demonstrative showcase only — FORBIDDEN for agents* |
| **Green** | `#9EFAB0` | `#1AE51A` | `#067008` | *Demonstrative showcase only — FORBIDDEN for agents* |
| **Orange** | `#FFB899` | `#FF5500` | `#913606` | *Demonstrative showcase only — FORBIDDEN for agents* |
| **Yellow** | `#FFEE99` | `#E5C41A` | `#917806` | *Demonstrative showcase only — FORBIDDEN for agents* |
| **Teal** | `#9EF2FA` | `#14A9B8` | `#068691` | *Demonstrative showcase only — FORBIDDEN for agents* |
| **Violet** | `#A99EFA` | `#8019E5` | `#4D0691` | *Demonstrative showcase only — FORBIDDEN for agents* |

---

## 3. Typography System

### Font Families & Local Packages
* `--font-body`: `'Geist', sans-serif` — Used **only** for `h1`, `body` text, and the lower CTA button label. (Downloadable bundle: `./fonts/geist.zip`).
* `--font-header`: `'Geist Mono', monospace` — Used for **everything else** (`h2`–`h6`, box headers, ordered lists, navigation, and standard buttons). (Downloadable bundle: `./fonts/geist-mono.zip`).

### Type Scale & Color Rules
| Style / Role | Font Family | Weight | Size | Line Height | Tracking | Color | Case |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `h1` | Geist | Light (300) | `160px` | `110%` | `0%` | `#FFFFFF` (optional 2–4 words `#DF1717`) | UPPERCASE |
| `h2` | Geist Mono | Light (300) | `96px` | `110%` | `0%` | `#FFFFFF` (with `grey` `↘`) | UPPERCASE |
| `h3` | Geist Mono | ExtraLight (200) | `64px` | `110%` | `0%` | `#FFFFFF` (optional 2–4 words `#DF1717`) | UPPERCASE |
| `h4` | Geist Mono | Light (300) | `48px` | `110%` | `0%` | `#FFFFFF` (optional 2–4 words `#DF1717`) | UPPERCASE |
| `h5` | Geist Mono | Regular (400) | `32px` | `110%` | `+4%` | `#FFFFFF` (optional 2–4 words `#DF1717`) | UPPERCASE |
| `h6` | Geist Mono | Light (300) | `24px` | `130%` | `+1%` | `#FFFFFF` (optional 2–4 words `#DF1717`) | UPPERCASE |
| `body` | Geist | Regular (400) | `24px` | `130%` | `0%` | `grey-l` (`#EBE7E0`, `max-width: 66ch`) | Sentence case |
| `micro` | Geist Mono | Regular (400) | `14px` | `110%` | `+4%` | `grey` (`#808080`) or `grey-l` | UPPERCASE |

### Proportional Heading-to-Body Spacing (8px Grid)
* `h1` → `body`: minimum `64px` gap
* `h2` → `body`: minimum `40px` gap (in section headers, `body` sits inside `padding: 56px 88px 24px`)
* `h3`–`h6` → `body`: minimum `24px` gap

---

## 4. Brand Marks, `currentColor` & 9-Part Perimeter Frame (`./svgs/`)

* **SVG Coloring (`fill="currentColor"`):** Source SVG files in `./svgs/` use `fill="black"`. Non-interactive decorative SVGs render in `--color-grey-d` (`#424242`); interactive SVG controls render in `--color-red-d` (`#910606`) and transition to `--color-red` (`#DF1717`) on hover.
* **Primary Full-Width Lockup:** `./svgs/com-logo-full.svg` — Spans `width: 100%` in showcases; in `INTRO` slides, constrain to `max-width: 250px`.
* **Guild Emblem (`./svgs/com-g.svg`):** Used **exclusively** in Guild presentations when explicitly requested by the prompt author—never in standard CoM decks.
* **Perimeter Frame Architecture (Top, Bottom, Left, Right):**
  * **4 Corner Cells (`66px × 66px`):** House centered standalone diagonal icon pairs (`Top-Left + Bottom-Right` = Mark A; `Top-Right + Bottom-Left` = Mark B) with inset segmented `2px` `--color-grey-d` (`#424242`) borders:
    * Vertical side border: inset `14px` from top and `14px` from bottom (`top: 14px; bottom: 14px; width: 2px;`).
    * Horizontal top/bottom border: inset `14px` from left and `14px` from right (`left: 14px; right: 14px; height: 2px;`).
  * **Top & Bottom Center Rails:** House a single centered shape (`./svgs/com-barcode-long.svg` when width allows, falling back to `./svgs/com-barcode-short.svg` on narrow viewports) inside a container with a `2px` inside `--color-grey-d` (`#424242`) border starting `12px` away from the corner cell borders (`left: 12px; right: 12px;`).
  * **Left & Right Lateral Center Rails (`66px` wide):** Vertically centered between the top and bottom corner cells (`top: 66px; bottom: 66px;`), housing `./svgs/com-pdf417.svg` on one lateral center rail and `./svgs/com-barcode-short.svg` on the opposite lateral center rail (rotated `90deg` / `-90deg` to align vertically).
* **Chapter / Section Corner Pairing Protocol:**
  * **Default `INTRO` / Chapter 1 Pair:** `com-logo.svg` + `com-d12.svg`.
  * **Subsequent Chapters Progression:**
    * Slot A cycles sequentially: `com-logo.svg` → `com-c.svg` → `com-o.svg` → `com-m.svg` → `com-logo.svg` (repeating).
    * Slot B selects randomly from `{com-d2.svg, com-d6.svg, com-d8.svg, com-d10.svg, com-d20.svg}` **excluding** `com-d12.svg` and the currently active die.

---

## 5. Slide Deck Grid, Overflow Protection & Compositions (`1920 × 1080`)

* **Fixed Frame & Footer Guardrail:** Every slide uses a locked `1920 × 1080px` (`16:9`) perimeter frame (`66px` rails on all 4 sides, `overflow: hidden;`). Content inside the center safe-zone must **never** overflow or push the bottom bar off the slide—if content exceeds the safe height, split it across two slides.
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
   * Used for **2 to 4** standalone pillars/theses following the main slide headline: either **2–3 cards in a single row** or a **2×2 grid**. All `SBOX` cards on a slide must share **equal height**.

---

## 6. Component Specifications (No Outer Wrapper Borders)

* **Main Button:** `color: #000000`, `background-color: var(--color-red)`, `border: 1px solid var(--color-red)`, `font-family: 'Geist Mono'`, `text-transform: uppercase`. Hover: `color: var(--color-red)`, `background-color: rgba(145, 6, 6, 0.40)`, `border-color: var(--color-red)`.
* **Side Button:** `color: var(--color-red)`, `background-color: #000000`, `border: 1px solid var(--color-red)`, `font-family: 'Geist Mono'`, `text-transform: uppercase`. Hover: `color: var(--color-red)`, `background-color: rgba(145, 6, 6, 0.40)`, `border-color: var(--color-red)`.
* **Two-Part `CTA` Button:** Top hug frame (`padding: 24px 40px`, `#000000`, `1px solid var(--color-grey-d)`, `h6` `#FFFFFF`) + bottom frame (`padding: 40px 48px`, `var(--color-red)`, `Geist` `32px` Medium underlined `#000000`).
* **`VERBOX` / `HORBOX` Header:** `width: fit-content`, `padding: 24px 48px`, `border: 1px solid var(--color-grey-d)`, `background-color: #000000`, `color: #FFFFFF` (`h5` `32px` `Geist Mono` uppercase).
* **`SBOX` Header:** `width: 100%`, `padding: 24px 40px`, `border: 1px solid var(--color-grey-d)`, `background-color: #000000`, `color: #FFFFFF` (`h5` `32px` `Geist Mono` uppercase).
* **Ordered Lists:** Left hugging number cell (`padding: 24px`, `1px solid var(--color-grey-d)`, `#000000`, `h6` regular `var(--color-red)`, no trailing dot) + right full-bordered text cell (`padding: 24px 48px`, `1px solid var(--color-grey-d)`, `#000000`, `h6` regular uppercase `#FFFFFF`).
