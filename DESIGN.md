# DESIGN.md — Court of Moravia

> **System Essence:** A technical frame. A human purpose.
> **Core Motto:** WE CHANGE THE GAME OF BUSINESS / WE DELIVER CHANGE IN COMPANIES
> **Snapshot Date:** 16 Nov 2026

---

## 1. Core Design Principles & Rules

When generating UI, web pages, slide decks, or digital assets for **Court of Moravia (COM)**, strictly follow these rules:

1. **01 PURE BLACK CANVAS ONLY:** Pure black (`#000000`) is the **only** surface background color used across pages, `verbox`, `horbox`, `sbox`, color chips, and layout containers. Never use `#121212` (`black-l`) inside boxes or cards—the only exception is button and interactive hover states (`rgba(accent-d, 0.40)`).
2. **02 ACCENT ROLES (`-L` vs. `-D`):** Choose **one accent family per composition** (defaulting to **Red** `#DF1717`). The canonical palette sequence is: **Red, Blue, Green, Orange, Yellow, Teal, Violet, White + Grey, Black**.
   * **Interactive Elements:** Every interactive element (buttons, links, active controls, hover text) uses `--accent-l` (`#F65656` for Red) or transitions to `--accent-l` on hover.
   * **Structural Lines & Decorative Elements:** Every border, hairline divider, and non-textual decorative element uses `--accent-d` (`#910606` for Red).
3. **03 STRICT TEXT COLOR ROLES:** Pure white (`#FFFFFF`) is strictly reserved for `h1`–`h3` headers and `body` text (plus the value breakdown inside color chips). All other text, eyebrows, labels, and subheadings (`h4`–`h6`, `micro`) must use `grey-l` (`#E8E5E0`) or `--accent` / `--accent-l`.
4. **04 TYPOGRAPHY ROLES & MEASURE:** `Geist` is used exclusively for `h1` display titles, `body` text, and the bottom label of CTA buttons. `Geist Mono` is used for everything else (`h2`–`h6`, box headers, ordered lists, navigation, and standard buttons). All text outside `body` copy uses `text-transform: uppercase`. Body paragraphs must never exceed `max-width: 66ch` to ensure optimal reading measure.
5. **05 SPACING & PROPORTIONAL RHYTHM:** Standard spacing is strictly based on multiples of `8px` (`0px` or minimum `8px`, typically larger). Vertical gaps between `body` text and headings scale proportionally: at least `24px` below `h3`–`h6`, at least `40px` below `h2`, and at least `64px` below `h1`.
6. **06 GEOMETRY & COMPONENT BOUNDARIES:** Favor flat, angular marks and crisp `0px` border-radius rectangular framing. Composite components (`horbox`, `verbox`, `sbox`, `cta-button`, ordered lists) **never have an outer wrapper border as a whole**—borders and fills apply strictly to their individual inner parts. For non-web deliverables (slide decks, print), standard border stroke width is `2px` aligned **inside**.
7. **07 FUNCTIONAL MINIMALISM:** Zero decorative "tech larp" or terminal cosplay—do not use `//`, `/`, or bracketed flavor text (e.g., `[CLICK TO COPY]`) as inline dividers or decorative labels. Minimize eyebrow text (`h5` section numbers) to an absolute minimum.

---

## 2. Color System (26 Variables)

*Strict sequence: Red (default), Blue, Green, Orange, Yellow, Teal, Violet, White + Grey, Black.*

### Accent Families (Pick ONE per composition; Default = Red)
| Family | Dark (`-D` · Lines/Borders) | Base (Primary) | Light (`-L` · Interactive) |
| :--- | :--- | :--- | :--- |
| **Red (Default)** | `#910606` | `#DF1717` | `#F65656` |
| **Blue** | `#063B91` | `#196FE6` | `#9EC4FA` |
| **Green** | `#067008` | `#1AE51A` | `#9EFAB0` |
| **Orange** | `#913606` | `#FF5500` | `#FFB899` |
| **Yellow** | `#917806` | `#E5C41A` | `#FFEE99` |
| **Teal** | `#068691` | `#14A9B8` | `#9EF2FA` |
| **Violet** | `#4D0691` | `#8019E5` | `#A99EFA` |

### Neutrals & Surfaces
| Token | Hex | Strict Usage Role |
| :--- | :--- | :--- |
| `--color-white` | `#FFFFFF` | **Restricted:** `h1`–`h3` headers and `body` text only |
| `--color-grey-l` | `#E8E5E0` | Secondary text, box headers, labels, and `h2` trailing `↘` arrow |
| `--color-grey-d` | `#808080` | Muted neutral reference |
| `--color-black-l` | `#121212` | Reserved token only — never used as a card or box background |
| `--color-black` | `#000000` | Universal background canvas and primary filled-element text |

### Color Chip Specification
Each color token is documented as a split two-part chip:
1. **Top Swatch Frame:** `padding: 32px 40px`, `background-color: $color`, `color: #000000` (or `#FFFFFF` on dark shades), displaying the `h5` token name (e.g., `RED-L`).
2. **Bottom Spec Frame:** `padding: 32px 40px`, `background-color: #000000`, `border: 1px solid var(--accent-d)`, `color: #FFFFFF`, `display: flex; flex-direction: column; gap: 24px`, containing four stacked paragraphs: **HEX**, **RGB**, **HSL**, and **OKLCH**.

---

## 3. Typography System

### Font Families
* `--font-body`: `'Geist', sans-serif` — Used **only** for `h1`, `body` text, and the lower CTA button label.
* `--font-header`: `'Geist Mono', monospace` — Used for **everything else** (`h2`–`h6`, box headers, ordered lists, navigation, and standard buttons).

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

## 4. Buttons & Interactive Hover States

All interactive buttons and typography showcase rows share a unified hover state (`background-color: rgba(var(--accent-d), 0.40)`, `color: var(--accent-l)`, `border-color: var(--accent-l)`):

* **Main Button (Primary CTA):**
  * Default: `color: #000000`, `background-color: var(--accent-l)`, `border: 1px solid var(--accent-l)`, `font-family: 'Geist Mono'`, `text-transform: uppercase`
  * Hover: `color: var(--accent-l)`, `background-color: rgba(var(--accent-d), 0.40)`, `border-color: var(--accent-l)`
* **Side Button (Alternative Choice):**
  * Default: `color: var(--accent-l)`, `background-color: #000000`, `border: 1px solid var(--accent-l)`, `font-family: 'Geist Mono'`, `text-transform: uppercase`
  * Hover: `color: var(--accent-l)`, `background-color: rgba(var(--accent-d), 0.40)`, `border-color: var(--accent-l)`
* **Two-Part `CTA` Button (No outer wrapper border):**
  1. **Top Frame:** `width: fit-content` (`hug`), `padding: 24px 40px`, `background-color: #000000`, `border: 1px solid var(--accent-d)`, containing an `h6` (`color: var(--accent-l)`, uppercase).
  2. **Bottom Action Frame (directly underneath, `0px` gap):** `padding: 40px 48px`, `background-color: var(--accent-l)`, `border: 1px solid var(--accent-l)`, containing `font-family: 'Geist'`, `font-size: 32px`, `font-weight: 500`, `text-decoration: underline`, `text-transform: uppercase`, `color: #000000`.
     * *Hover:* `color: var(--accent-l)`, `background-color: rgba(var(--accent-d), 0.40)`, `border-color: var(--accent-l)`.

---

## 5. Component Specifications (No Outer Wrapper Borders)

Composite components never carry a single border around the entire unit; only their specified child frames are bordered or filled. All surfaces sit on `#000000`.

### A. Section / Big Header
1. **Eyebrow (`h5`):** Optional section number or minimal label (`color: var(--accent-l)` or `grey-l`). Keep to an absolute minimum.
2. **Gap:** `32px` vertical spacing between `h5` and `h2`.
3. **Title (`h2`):** `color: #FFFFFF`, uppercase `Geist Mono`, ending with a trailing `↘` glyph styled in `color: var(--color-grey-l)`.
4. **Section Description:** `body` text (`max-width: 66ch`, `color: #FFFFFF`) placed inside a wrapper with `padding: 56px 88px 24px`.

### B. `VERBOX` (Vertical Box — Content Stacked in a Column)
* **No outer wrapper border.**
* **Top Header Frame (`h5`):** `width: fit-content` (`hug`), `padding: 24px 48px`, `border: 1px solid var(--accent-d)`, `background-color: #000000`, `color: var(--color-grey-l)` (`Geist Mono`, `32px`, uppercase).
* **Content Frame (directly underneath, `0px` gap):** `background-color: #000000`, `border: 1px solid var(--accent-d)`, `padding: 64px 72px`, `display: flex; flex-direction: column; gap: 64px`.
* **Content Items:** Either plain `body` paragraphs (`max-width: 66ch`, `color: #FFFFFF`) or `h6` (`color: var(--accent-l)`, uppercase) + `body` pairs with `gap: 24px` between the `h6` and its paragraph.

### C. `HORBOX` (Horizontal Box — Columns in a Row)
* **No outer wrapper border.**
* **Top Header Frame (`h5`):** `width: fit-content` (`hug`), `padding: 24px 48px`, `border: 1px solid var(--accent-d)`, `background-color: #000000`, `color: var(--color-grey-l)` (`Geist Mono`, `32px`, uppercase).
* **Content Frame (directly underneath, `0px` gap):** `background-color: #000000`, `border: 1px solid var(--accent-d)`, `padding: 64px 72px`, arranged horizontally in a row with `gap: 56px` between individual `body` blocks or `h6` (`color: var(--accent-l)`) + `body` (`gap: 24px`) pairs.

### D. `SBOX` (Small Box)
* **No outer wrapper border.**
* **Top Header (`h5`):** `width: 100%` (fills the entire width of the `sbox`), `padding: 24px 40px`, `border: 1px solid var(--accent-d)`, `background-color: #000000`, `color: var(--color-grey-l)` (`Geist Mono`, `32px`, uppercase).
* **Content Frame (directly underneath, `0px` gap):** `background-color: #000000`, `border: 1px solid var(--accent-d)`, `padding: 48px 56px`, containing `body` text (`max-width: 66ch`, `color: #FFFFFF`).

### E. Ordered Lists
* **No outer wrapper border.** Each list row consists of two flush (`0px` gap) side-by-side frames (`align-items: flex-start` so the number cell hugs its content and hangs cleanly next to the item without stretching vertically):
  1. **Number Cell (Left):** `padding: 24px`, `background-color: #000000`, `border: 1px solid var(--accent-d)`, `color: var(--accent-l)`, `font-family: 'Geist Mono'`, `font-weight: 400` (`h6` regular — never bold). Hugs the number (`align-self: flex-start`) with no trailing dot.
  2. **Text Cell (Right):** `padding: 24px 48px`, `background-color: #000000`, `border: 1px solid var(--accent-d)`, `color: var(--accent-l)`, `font-family: 'Geist Mono'`, `font-weight: 400` (`h6` regular — never bold, uppercase). Grows vertically in height when text wraps across multiple lines.

---

## 6. Sticky Topbar & Sticky Footer Shell

Instead of side perimeter rails, the viewport is framed by a **sticky topbar** and **sticky footer**, each `66px` tall:

* **Layout:** 3-column grid (`66px 1fr 66px`) with `height: 66px` on both topbar and footer.
* **End Squares (`66px × 66px`):** Centered `30px × 30px` square SVG placeholder (`1px solid var(--accent-d)`).
* **Center Stretch Cell (`1fr`):**
  * **Topbar Center:** `border-bottom: 1px solid var(--accent-d)`, housing the navigation menu and accent switcher.
  * **Footer Center:** `border-top: 1px solid var(--accent-d)`.

---

## 7. Strict Anti-Patterns (Do NOT Generate)
* **No `black-l` (`#121212`) backgrounds:** Pure `#000000` is the only background used in layout containers, boxes, and cards.
* **No bold font-weight on ordered lists:** Ordered list numbers and text use `font-weight: 400` (Regular), never bold.
* **No outer wrapper borders on composite blocks:** Never wrap `horbox`, `verbox`, `sbox`, `cta-button`, or ordered list items in an extra outer border.
* **No rounded corners:** `0px` sharp corners everywhere.
* **No off-role white text:** Never use `#FFFFFF` for `h4`–`h6`, labels, eyebrows, or metadata (use `grey-l` or `--accent-l`).
* **No paragraphs wider than `66ch`:** Always cap `body` text measure at `max-width: 66ch`.
