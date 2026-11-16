# DESIGN.md — Court of Moravia

> **System Essence:** A technical frame. A human purpose.
> **Core Motto:** WE CHANGE THE GAME OF BUSINESS / WE DELIVER CHANGE IN COMPANIES
> **Snapshot Date:** 16 Nov 2026

---

## 1. Core Design Principles & Rules

When generating UI, web pages, slide decks, or digital assets for **Court of Moravia (COM)**, strictly follow these 5 rules:

1. **01 / PALETTE:** Use pure black (`#000000`) and pure white (`#FFFFFF`) as the primary field. Choose **one accent family per composition**—do not mix multiple palette hues by default.
2. **02 / HIERARCHY:** Pair large, light, uppercase headlines (`Geist`) with clean, sentence-case body copy (`Geist`). Use monospaced type (`Geist Mono`) for technical labels, headings (`h3`–`h6`), metadata, and navigational details.
3. **03 / COMPOSITION:** Align elements to a clear, crisp edge and protect generous negative space. Keep ornamental borders, ticks, and technical framing confined to the outer perimeter, well away from the core message.
4. **04 / GEOMETRY:** Favor flat, angular marks and crisp rectangular framing. Avoid rounded blobs, drop shadows, soft gradients, or organic curves.
5. **05 / LEGIBILITY:** Use pure white (`#FFFFFF`) or a tested `-L` (light) tint for small text on dark backgrounds. Always verify contrast at the final rendered size.

---

## 2. Color System (26 Variables)

*Naming convention: Base token = primary hue, `-D` = dark shade, `-L` = light tint.*

### Neutrals & Surfaces
| Token | Hex | Role / Notes |
| :--- | :--- | :--- |
| `--color-black` | `#000000` | Primary background / dark field |
| `--color-black-l` | `#121212` | Elevated dark surface / subtle card fill |
| `--color-grey-d` | `#808080` | Muted technical borders, secondary labels |
| `--color-grey-l` | `#E8E5E0` | Warm off-white surface / muted light fill |
| `--color-white` | `#FFFFFF` | Primary light text / inverted background |

### Accent Families (Pick ONE per composition)
| Family | Dark (`-D`) | Base (Primary) | Light (`-L`) |
| :--- | :--- | :--- | :--- |
| **Blue** | `#063B91` | `#196FE6` | `#9EC4FA` |
| **Green** | `#067008` | `#1AE51A` | `#9EFAB0` |
| **Orange** | `#913606` | `#FF5500` | `#FFB899` |
| **Yellow** | `#917806` | `#E5C41A` | `#FFEE99` |
| **Red** | `#910606` | `#DF1717` | `#F65656` |
| **Teal** | `#068691` | `#14A9B8` | `#9EF2FA` |
| **Violet** | `#4D0691` | `#8019E5` | `#A99EFA` |

---

## 3. Typography System

### Font Families
* `--font-body`: `'Geist', sans-serif` (Used for major display headlines `h1`–`h2` and body copy)
* `--font-header`: `'Geist Mono', monospace` (Used for technical headings `h3`–`h6`, labels, and microtype)

### Type Scale & Styles
| Style / Role | Font Family | Weight | Size | Line Height | Tracking (Letter Spacing) | Case / Usage |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `h1` | Geist | Light (300) | `160px` | `110%` | `0%` | UPPERCASE — Hero display |
| `h2` | Geist | Light (300) | `96px` | `110%` | `0%` | UPPERCASE — Section display |
| `h3` | Geist Mono | ExtraLight (200) | `64px` | `110%` | `0%` | UPPERCASE — Technical display |
| `h4` | Geist Mono | Light (300) | `48px` | `110%` | `0%` | UPPERCASE — Sub-display / Deck titles |
| `h5` | Geist Mono | Regular (400) | `32px` | `110%` | `+4%` | UPPERCASE — Card / Block headers |
| `h6` | Geist Mono | Light (300) | `24px` | `130%` | `+1%` | Technical subheadings |
| `body` | Geist | Regular (400) | `24px` | `130%` | `0%` | Sentence case — Primary reading copy |
| `micro` | Geist Mono | Regular (400) | `14px` | `110%` | `+4%` | UPPERCASE — Captions, tags, border codes |

### Extended Numeric Scale Tokens
*(Note: Numeric tokens exist in the system without fixed semantic roles; use proportionally when scaling).*
* **Display Scale:** `tera: 88px`, `giga: 72px`, `mega: 64px`, `kilo: 56px`, `micro: 48px`, `nano: 40px`, `pico: 32px`, `femto: 24px`
* **Stroke / Line Weight:** `stroke: 2px` (or `1px` for fine technical hairlines/gutters)

---

## 4. Layout, Grid & Framing Conventions

### Master Grid (`main`)
* **Structure:** 1 stretch row + 1 stretch column (single unified content safe-zone framed by technical perimeter borders).
* **Outer Inset / Margin:** `136px` (for standard `1080x1080` post or `1920x1080` deck formats; scale proportionally for responsive web viewports).
* **Gutter:** `1px`

### Borders & Technical Ornaments (CSS / HTML Approximation)
* **Perimeter Framing:** Use thin `1px` or `2px` solid rules (`--color-grey-d` or the active accent color) with crisp `0px` border-radius.
* **Micro-Motifs:** Decorate outer frame edges or section dividers with monospaced ASCII/technical ticks (`|||||`, `/////`, `\\\`, `XXXXX`), corner crosshairs, or index numbers (e.g., `01 / PALETTE`) set in `Geist Mono` (`14px`, `+4%` tracking).
* **Negative Space:** Keep the interior canvas clean and uncluttered; never crowd text against the perimeter frame.

---

## 5. Strict Anti-Patterns (Do NOT Generate)
* **No rounded corners:** Do not use `border-radius` on cards, buttons, or containers (`0px` sharp corners only).
* **No multi-color rainbows:** Never combine Red, Blue, Green, and Yellow accents on the same screen. Stick to Black + White + **1 Accent Family**.
* **No decorative/serif fonts:** Never substitute `Geist` or `Geist Mono` with Playfair, Inter, Roboto, or handwritten/script fonts.
* **No drop shadows or glassmorphism:** Avoid `box-shadow`, `backdrop-filter: blur()`, and soft gradients. Rely on high-contrast solid fills and `1px`–`2px` hairline borders.
