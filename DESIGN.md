# DESIGN.md — Court of Moravia

> **System Essence:** A technical frame. A human purpose.
> **Core Motto:** WE CHANGE THE GAME OF BUSINESS / WE DELIVER CHANGE IN COMPANIES
> **Snapshot Date:** 16 Nov 2026

---

## 1. Core Design Principles & Rules

When generating UI, web pages, slide decks, or digital assets for **Court of Moravia (COM)**, strictly follow these rules:

1. **01 PURE BLACK CANVAS ONLY:** Pure black (`#000000`) is the **only** surface background color used across pages, `verbox`, `horbox`, `sbox`, and layout containers. Never use `#121212` (`black-l`) inside boxes or cards—the only exception is button hover states (`rgba(accent-d, 0.40)`).
2. **02 COLOR SEQUENCE & STRICT TEXT ROLES:** Choose **one accent family per composition** (defaulting to **Red** `#DF1717`). The canonical palette sequence is: **Red, Blue, Green, Orange, Yellow, Teal, Violet, White + Grey, Black**. Pure white (`#FFFFFF`) is strictly reserved for `h1`–`h3` headers and `body` text; all other text, eyebrows, labels, and subheadings (`h4`–`h6`, `micro`) must use `grey-l` (`#E8E5E0`) or the active `--accent` color.
3. **03 TYPOGRAPHY ROLES & MEASURE:** `Geist` is used exclusively for `h1` display titles, `body` text, and the bottom label of CTA buttons. `Geist Mono` is used for everything else (`h2`–`h6`, box headers, ordered lists, navigation, and standard buttons). All text outside `body` copy uses `text-transform: uppercase`. Body paragraphs must never exceed `max-width: 66ch` to ensure optimal reading measure.
4. **04 SPACING & PROPORTIONAL RHYTHM:** Standard spacing is strictly based on multiples of `8px` (`0px` or minimum `8px`, typically larger). Vertical gaps between `body` text and headings scale proportionally: at least `24px` below `h3`–`h6`, at least `40px` below `h2`, and at least `64px` below `h1`.
5. **05 GEOMETRY & COMPONENT BOUNDARIES:** Favor flat, angular marks and crisp `0px` border-radius rectangular framing. Avoid rounded corners, drop shadows, glassmorphism, and soft gradients. Composite components (`horbox`, `verbox`, `sbox`, `cta-button`, ordered lists) **never have an outer wrapper border as a whole**—borders and fills apply strictly to their individual inner parts. For non-web deliverables (slide decks, print), standard border stroke width is `2px` aligned **inside**.
6. **06 FUNCTIONAL MINIMALISM:** Zero decorative "tech larp" or terminal cosplay—do not use `//`, `/`, or bracketed flavor text (e.g., `[CLICK TO COPY]`) as inline dividers or decorative labels. Minimize eyebrow text (`h5` section numbers) to an absolute minimum.

---

## 2. Color System (26 Variables)

*Strict sequence: Red (default), Blue, Green, Orange, Yellow, Teal, Violet, White + Grey, Black.*

### Accent Families (Pick ONE per composition; Default = Red)
| Family | Dark (`-D`) | Base (Primary) | Light (`-L`) |
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
| `--color-grey-l` | `#E8E5E0` | Secondary text, labels, metadata, and `h2` trailing `↘` arrow |
| `--color-grey-d` | `#808080` | Muted structural hairlines and frame rails |
| `--color-black-l` | `#121212` | Reserved token only — never used as a card or box background |
| `--color-black` | `#000000` | Universal background canvas and primary filled-element text |

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
| `h4` | Geist Mono | Light (300) | `48px` | `110%` | `0%` | `grey-l` or `--accent` | UPPERCASE |
| `h5` | Geist Mono | Regular (400) | `32px` | `110%` | `+4%` | `grey-l` or `--accent` | UPPERCASE |
| `h6` | Geist Mono | Light (300) | `24px` | `130%` | `+1%` | `grey-l` or `--accent` | UPPERCASE |
| `body` | Geist | Regular (400) | `24px` | `130%` | `0%` | `#FFFFFF` (`max-width: 66ch`) | Sentence case |
| `micro` | Geist Mono | Regular (400) | `14px` | `110%` | `+4%` | `grey-l` or `--accent` | UPPERCASE |

### Proportional Heading-to-Body Spacing (8px Grid)
* `h1` → `body`: minimum `64px` gap
* `h2` → `body`: minimum `40px` gap (in section headers, `body` sits inside `padding: 56px 88px 24px`)
* `h3`–`h6` → `body`: minimum `24px` gap

---

## 4. Component Specifications (No Outer Wrapper Borders)

Composite components never carry a single border around the entire unit; only their specified child frames are bordered or filled. All surfaces sit on `#000000`.

### A. Section / Big Header
1. **Eyebrow (`h5`):** Optional section number or minimal label (`color: var(--accent)` or `grey-l`). Keep to an absolute minimum.
2. **Gap:** `32px` vertical spacing between `h5` and `h2`.
3. **Title (`h2`):** `color: #FFFFFF`, uppercase `Geist Mono`, ending with a trailing `↘` glyph styled in `color: var(--color-grey-l)`.
4. **Section Description:** `body` text (`max-width: 66ch`, `color: #FFFFFF`) placed inside a wrapper with `padding: 56px 88px 24px`.

### B. `VERBOX` (Vertical Box — Content Stacked in a Column)
* **No outer wrapper border.**
* **Top Header Frame:** `width: fit-content` (`hug`), `padding: 24px 48px`, `background-color: var(--accent)`, `color: #000000` (`Geist Mono`, uppercase).
* **Content Frame (directly underneath, `0px` gap):** `background-color: #000000`, `border: 1px solid var(--accent)`, `padding: 64px 72px`, `display: flex; flex-direction: column; gap: 64px`.
* **Content Items:** Either plain `body` paragraphs (`max-width: 66ch`, `color: #FFFFFF`) or `h6` (`color: var(--accent)`, uppercase) + `body` pairs with `gap: 24px` between the `h6` and its paragraph.

### C. `HORBOX` (Horizontal Box — Columns in a Row)
* **No outer wrapper border.**
* **Top Header Frame:** `width: fit-content` (`hug`), `padding: 48px 72px` (or `24px 48px`), `background-color: var(--accent)`, `color: #000000` (`Geist Mono`, uppercase).
* **Content Frame (directly underneath, `0px` gap):** `background-color: #000000`, `border: 1px solid var(--accent)`, `padding: 64px 72px`, arranged horizontally in a row (`display: flex` or multi-column grid) with `gap: 56px` between individual `body` blocks or `h6` (`color: var(--accent)`) + `body` (`gap: 24px`) pairs.

### D. `SBOX` (Small Box)
* **No outer wrapper border.**
* **Top Header (`h5`):** `width: 100%` (fills the entire width of the `sbox`), uppercase `Geist Mono` (`background-color: var(--accent)`, `color: #000000`, `padding: 24px 40px`).
* **Content Frame (directly underneath, `0px` gap):** `background-color: #000000`, `border: 1px solid var(--accent)`, `padding: 48px 56px`, containing `body` text (`max-width: 66ch`, `color: #FFFFFF`).

### E. Standard Buttons & Two-Part `CTA` Button
* **Main Button:** `color: #000000`, `background-color: var(--accent)`, `border: 1px solid var(--accent)`, `font-family: 'Geist Mono'`, `text-transform: uppercase`.
  * *Hover:* `color: var(--accent)`, `background-color: rgba(var(--accent-d), 0.40)`, `border-color: var(--accent)`.
* **Side Button (Alternative Choice):** `color: var(--accent)`, `background-color: #000000`, `border: 1px solid var(--accent)`, `font-family: 'Geist Mono'`, `text-transform: uppercase`.
  * *Hover:* `color: var(--accent)`, `background-color: rgba(var(--accent-d), 0.40)`, `border-color: var(--accent)`.
* **Two-Part `CTA` Button (No outer wrapper border):**
  1. **Top Frame:** `padding: 24px 40px`, `background-color: #000000`, `border: 1px solid var(--accent)`, containing an `h6` (`color: var(--accent)`, uppercase).
  2. **Bottom Action Frame (directly underneath, `0px` gap):** `padding: 40px 48px`, `background-color: var(--accent)`, `border: 1px solid var(--accent)`, containing `font-family: 'Geist'`, `font-size: 32px`, `font-weight: 500`, `text-decoration: underline`, `text-transform: uppercase`, `color: #000000`.
     * *Hover:* `color: var(--accent)`, `background-color: rgba(var(--accent-d), 0.40)`, `border-color: var(--accent)`.

### F. Ordered Lists
* **No outer wrapper border.** Each list row consists of two flush (`0px` gap) side-by-side frames (`align-items: stretch`):
  1. **Number Cell (Left):** `padding: 24px`, `background-color: #000000`, `border: 1px solid var(--accent)`, `color: var(--accent)`, `font-family: 'Geist Mono'`, `font-weight: 700` (`h6` bold). Contains **only the number** (no trailing dot or punctuation). Aligns to the top when text wraps.
  2. **Text Cell (Right):** `padding: 24px 48px`, `background-color: var(--accent)`, `border: 1px solid var(--accent)`, `color: #000000`, `font-family: 'Geist Mono'`, `font-weight: 700` (`h6` bold, uppercase). Grows vertically in height when text wraps across multiple lines.

---

## 5. 9-Part Perimeter Frame Architecture

The page uses a **9-part CSS Grid** (`66px 1fr 66px` columns × `66px 1fr 66px` rows) that scrolls naturally with the document so corner and edge elements visibly frame the entire layout:

* **4 Corner Cells (`66px × 66px`):** Centered `30px × 30px` square SVG slot (`1px solid var(--accent)`).
* **Top Center Cell (`1fr × 66px`):** Houses the primary navigation menu and accent switcher.
* **Left, Right & Bottom Stretched Edge Cells (`66px × 1fr` / `1fr × 66px`):** Centered slim SVG ornament slots (`2px × 300px` vertical on left/right; `300px × 2px` horizontal on bottom).
* **Center Cell (`1fr × 1fr`):** Main `#000000` content canvas.

---

## 6. Strict Anti-Patterns (Do NOT Generate)
* **No `black-l` (`#121212`) backgrounds:** Pure `#000000` is the only background used in layout containers, boxes, and cards.
* **No outer wrapper borders on composite blocks:** Never wrap `horbox`, `verbox`, `sbox`, `cta-button`, or ordered list items in an extra outer border.
* **No rounded corners:** `0px` sharp corners everywhere.
* **No off-role white text:** Never use `#FFFFFF` for `h4`–`h6`, labels, eyebrows, or metadata (use `grey-l` or `--accent`).
* **No paragraphs wider than `66ch`:** Always cap `body` text measure at `max-width: 66ch`.
* **No terminal cosplay:** Never use `//`, `/`, or `[TEXT]` flavor decorations in UI labels or headings.
