# DESIGN.md — Court of Moravia

> **System Essence:** A technical frame. A human purpose.
> **Core Motto:** WE CHANGE THE GAME OF BUSINESS / WE DELIVER CHANGE IN COMPANIES
> **Snapshot Date:** 16 Nov 2026

---

## 1. Core Design Principles & Rules

When generating UI, web pages, slide decks, or digital assets for **Court of Moravia (COM)**, strictly follow these rules:

1. **01 / PALETTE & COLOR HIERARCHY:** Use pure black (`#000000`) as the primary canvas. Choose **one accent family per composition** (defaulting to **Red** `#DF1717`). Pure white (`#FFFFFF`) is strictly reserved for `h1`–`h3` headers and `body` text; all other text, labels, metadata, and subheadings (`h4`–`h6`, `micro`) must use `grey-l` (`#E8E5E0`) or the active `--accent` color.
2. **02 / TYPOGRAPHY ROLES:** `Geist` is used exclusively for `h1` display titles and `body` text (optimized for short and long-form reading). `Geist Mono` is used for everything else (`h2`–`h6`, banners, labels, buttons, navigation, and microtype). All text outside `body` copy uses `text-transform: uppercase`.
3. **03 / SPACING & PROPORTIONAL RHYTHM:** Standard spacing is strictly based on multiples of `8px` (`0px` or minimum `8px`, typically larger). Vertical gaps between `body` text and headings scale proportionally: at least `24px` below `h3`–`h6`, at least `40px` below `h2`, and at least `64px` below `h1`.
4. **04 / GEOMETRY & STROKES:** Favor flat, angular marks and crisp `0px` border-radius rectangular framing. Avoid rounded corners, drop shadows, glassmorphism, and soft gradients. For non-web deliverables (slide decks, print), standard border stroke width is `2px` aligned **inside**.
5. **05 / FUNCTIONAL MINIMALISM:** Zero decorative "tech larp" or terminal cosplay—do not use `//`, `/`, or bracketed flavor text (e.g., `[CLICK TO COPY]`) as inline dividers or decorative labels. Keep all UI clean, direct, and functional.

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
| `--color-grey-l` | `#E8E5E0` | Secondary text, labels, metadata, and subtle borders |
| `--color-grey-d` | `#808080` | Muted borders and structural hairlines |
| `--color-black-l` | `#121212` | Elevated dark card/box surface |
| `--color-black` | `#000000` | Primary background field and primary button text |

---

## 3. Typography System

### Font Families
* `--font-body`: `'Geist', sans-serif` — Used **only** for `h1` and `body` text.
* `--font-header`: `'Geist Mono', monospace` — Used for **everything else** (`h2`–`h6`, banners, buttons, labels, and microtype).

### Type Scale & Color Rules
| Style / Role | Font Family | Weight | Size | Line Height | Tracking | Color | Case |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `h1` | Geist | Light (300) | `160px` | `110%` | `0%` | `#FFFFFF` | UPPERCASE |
| `h2` | Geist Mono | Light (300) | `96px` | `110%` | `0%` | `#FFFFFF` | UPPERCASE |
| `h3` | Geist Mono | ExtraLight (200) | `64px` | `110%` | `0%` | `#FFFFFF` | UPPERCASE |
| `h4` | Geist Mono | Light (300) | `48px` | `110%` | `0%` | `grey-l` or `--accent` | UPPERCASE |
| `h5` | Geist Mono | Regular (400) | `32px` | `110%` | `+4%` | `grey-l` or `--accent` | UPPERCASE |
| `h6` | Geist Mono | Light (300) | `24px` | `130%` | `+1%` | `grey-l` or `--accent` | UPPERCASE |
| `body` | Geist | Regular (400) | `24px` | `130%` | `0%` | `#FFFFFF` | Sentence case |
| `micro` | Geist Mono | Regular (400) | `14px` | `110%` | `+4%` | `grey-l` or `--accent` | UPPERCASE |

### Proportional Heading-to-Body Spacing (8px Grid)
* `h1` → `body`: minimum `64px` gap
* `h2` → `body`: minimum `40px` gap
* `h3`–`h6` → `body`: minimum `24px` gap

---

## 4. Buttons & Interactive Controls

All interactive buttons use `Geist Mono`, `text-transform: uppercase`, `0px` border-radius, and `1px` solid borders:

* **Main Button (Primary CTA):**
  * Default: `color: #000000`, `background-color: var(--accent)`, `border: 1px solid var(--accent)`
  * Hover: `color: var(--accent)`, `background-color: rgba(var(--accent-d-rgb), 0.40)`, `border-color: var(--accent)`
* **Side Button (Alternative Choice):**
  * Default: `color: var(--accent)`, `background-color: #000000`, `border: 1px solid var(--accent)`
  * Hover: `color: var(--accent)`, `background-color: rgba(var(--accent-d-rgb), 0.40)`, `border-color: var(--accent)`

---

## 5. Slide Deck & Box Component Primitives

* **Non-Web Stroke Rule:** In slide decks and print layouts, borders use a `2px` stroke aligned **inside**.
* **Banners, `HORBOX` & `VERBOX` Headers:** Always sized to content (`width: fit-content` / Figma `hug`) with `padding: 24px 40px`, positioned at the top edge of the container.
* **`HORBOX` & `VERBOX` Content Area:** Interior body container has `padding: 64px 72px`.
* **`INTRO`:** Minimal title frame with uppercase `Geist` Light `h1` display headline (`#FFFFFF`) and bottom `COURT OF MORAVIA` attribution in `Geist Mono` (`grey-l` / `--accent`).
* **`CHAPTER`:** Full-bleed solid `--accent` fill with high-contrast `#000000` uppercase display typography.
* **`TEXT`:** Left-aligned uppercase display statement paired with `body` text (`#FFFFFF`) respecting proportional heading gaps (`24px`–`64px`).
* **`SBOX`:** 2-column grid of equal bordered boxes (`padding: 64px 72px` at full scale) with uppercase `Geist Mono` headers (`grey-l` or `--accent`) and `#FFFFFF` body copy.
* **`ROADMAP`:** 3-column sequential phase progression (`MĚSÍC 1–2: DATA`, etc.) with `Geist Mono` headers and `#FFFFFF` body copy.
* **`GOALS` / `CÍLE`:** Asymmetric 2-column split with an uppercase display title on the left and stacked bordered objective rows on the right.

---

## 6. 9-Part Perimeter Frame Architecture

The master viewport layout uses a **9-part CSS Grid** (`66px 1fr 66px` columns × `66px 1fr 66px` rows) framing the center content canvas:

* **4 Corner Cells (`66px × 66px`):** Centered `30px × 30px` square SVG slot (placeholder `1px` border box).
* **4 Stretched Edge Cells (Top/Bottom `1fr × 66px`, Left/Right `66px × 1fr`):** Centered slim SVG ornament slot (`300px × 2px` horizontal on top/bottom; `2px × 300px` vertical on left/right).
* **Center Cell (`1fr × 1fr`):** Main scrollable/responsive website content canvas.

---

## 7. Strict Anti-Patterns (Do NOT Generate)
* **No rounded corners:** `0px` sharp corners everywhere.
* **No off-role white text:** Never use `#FFFFFF` for `h4`–`h6`, labels, badges, or metadata (use `grey-l` or `--accent`).
* **No `Geist` on subheadings/UI:** `Geist` is strictly for `h1` and `body`; use `Geist Mono` for `h2`–`h6`, navigation, and buttons.
* **No terminal cosplay:** Never use `//`, `/`, or `[TEXT]` flavor decorations in labels or headings.
* **No multi-color mixing:** Stick to Black + White/Grey + **1 Accent Family** per composition.
