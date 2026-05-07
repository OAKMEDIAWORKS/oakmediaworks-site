# OAK Media Works — brand canon

The public, canonical home for OAK Media Works design tokens. Anything calling itself OAK should match what's in this repo. In case of conflict, this repo wins.

## Anchor

**Truckee Blue** — `#4E85DF`

A working blue. Lived-in, designer-led, not French-institutional. Sits naturally on warm cream paper; lifts cleanly on coffee dark. The tier is built so the canonical hex appears in both modes — light uses it as `--accent`, dark preserves it in `--accent-deep` for fills and chart bands.

> Named for Truckee, California — the Sierra town just over the hill from Lake Tahoe. Switched from Klein Blue (`#002FA7`) on 2026-05-06: Klein read too clinical against the cream surface. Truckee Blue is warmer, more approachable, still distinctly OAK.

## Tokens

Drop [`oak-tokens.css`](./oak-tokens.css) into your global CSS. Apply `[data-theme="dark"]` on `<html>` to opt into dark; remove for light.

### Light (default)

| Token | Hex | Use |
|---|---|---|
| `--accent` | `#4E85DF` | Primary actions, focus rings, fills behind ≥14px semibold text |
| `--accent-hover` | `#6E9CE8` | Hover state |
| `--accent-deep` | `#2E66C7` | **Body links, small text** — AA on cream |
| `--accent-soft` | `#E6EDF9` | Selected rows, hover washes |
| `--accent-on` | `#FFFFFF` | Text/icons on accent fills |

### Dark

| Token | Hex | Use |
|---|---|---|
| `--accent` | `#6E9CE8` | Primary actions — lifted for legibility |
| `--accent-hover` | `#8FB5F0` | Hover state |
| `--accent-deep` | `#4E85DF` | Canonical Truckee Blue — fills behind light text, halos, chart bands |
| `--accent-soft` | `#1A2440` | Wash on dark surfaces |
| `--accent-on` | `#F2EBE0` | Text/icons on accent fills |

## Contrast — read this before you ship

Truckee Blue is lighter than Klein. That has consequences.

- **`--accent` on cream is 3.1:1.** WCAG AA Large only. Use for buttons (≥14px semibold), display type, and chrome. **Don't put body copy or small links on it.**
- **`--accent-deep` on cream is 4.6:1.** AA for normal text. **This is your body-link color.** Reach for `var(--accent-deep)` on `<a>` tags in prose; reserve `var(--accent)` for emphasis fills and primary actions.
- **White on `--accent` is 3.7:1.** Fine for `.btn-primary` at 14px semibold (the pattern the token sheet ships). If you ever go thinner or smaller, switch `--accent-on` to `#1A1612`.

## Rules — warm coffee, no grays

Borders and dividers hit WCAG 1.4.11 (3:1 against canvas) in warm coffee tones. Cool grays on warm surfaces look broken — banished.

| Token | Light | Dark |
|---|---|---|
| `--rule` | `#8C7B5C` (3.5:1 on cream) | `#7B6A4F` (3.6:1 on coffee) |
| `--rule-strong` | `#6B5A40` (5.6:1) | `#9C8A6B` (5.6:1) |

`--rule` is visually present. That's deliberate — old hairlines were 1.3:1 and effectively invisible. If a layout feels over-lined, swap to `var(--bg-well)` recesses for purely decorative separation; reserve `--rule` for component boundaries.

## Surfaces — cream + coffee

Light is **cream paper**, not white. Dark is **coffee**, not pure black. Both warm. Never use pure white or pure black surfaces — they break the temperature.

```
LIGHT                          DARK
canvas   #F2EBE0                canvas   #161311
surface  #F8F2E8                surface  #1E1A16
well     #E8DFCC                well     #0E0C0A
hover    #ECE4D2                hover    #25201B
```

Text tier mirrors the warmth — never plain `#000` or `#FFF`:

```
LIGHT                          DARK
text-1   #1A1612                text-1   #F2EBE0
text-2   #4F463C                text-2   #A8A095
text-3   #8A8278                text-3   #6E665C
```

## Type

- **Sans:** Satoshi, with system fallbacks
- **Mono:** JetBrains Mono
- **Tabular numerals:** apply `font-variant-numeric: var(--num-tabular)` to numeric columns — dollar amounts, scores, counts, timestamps. The `.num`, `[data-num]`, `.tabular`, and `td.num` selectors get it for free, and right-justify automatically so decimal points stack across rows. (Note: same-precision values stack cleanly; mixed precision needs per-context handling.)

## Semantic

Status colors are mode-aware. Keep them — don't swap to other greens/reds.

```
                  LIGHT     DARK
--success         #177D4D   #34C77B
--warning         #B5640A   #E89A48
--error           #A8201F   #E15553
```

## Spacing

Four-pixel base. Eight tokens. Use them for any margin, padding, or gap. No raw px values in product CSS.

| Token | Value | Use |
|---|---|---|
| `--space-xs` | 4px | Component-internal · icon/text gap |
| `--space-sm` | 8px | Tight clusters |
| `--space-md` | 12px | Default cluster gap |
| `--space-lg` | 16px | Card padding · form rows |
| `--space-xl` | 24px | Section-internal gaps |
| `--space-2xl` | 32px | Between sections |
| `--space-3xl` | 48px | Page-level breathing room |
| `--space-4xl` | 64px | Hero · major breaks |

## Motion

Animate state changes — hover, focus, active, expand/collapse. Don't animate scroll. The token sheet handles `prefers-reduced-motion` automatically with a global override.

| Duration | Value | Use |
|---|---|---|
| `--motion-fast` | 120ms | Hover · active · tap |
| `--motion-base` | 200ms | Default — most transitions |
| `--motion-slow` | 320ms | Modal/sheet entry · accordion |
| `--motion-slower` | 500ms | Page transitions · hero motion |

| Easing | Curve | Use |
|---|---|---|
| `--ease-standard` | `cubic-bezier(0.2, 0, 0, 1)` | Default |
| `--ease-decelerate` | `cubic-bezier(0, 0, 0, 1)` | Entering UI |
| `--ease-accelerate` | `cubic-bezier(0.3, 0, 1, 1)` | Exiting UI |
| `--ease-emphasized` | `cubic-bezier(0.05, 0.7, 0.1, 1)` | Expressive moments |

## Z-index

Use these tokens for any positioned element. No raw integers in product CSS.

| Token | Value | Use |
|---|---|---|
| `--z-base` | 0 | Default |
| `--z-raised` | 10 | Sticky-within-scroll-container |
| `--z-dropdown` | 100 | Dropdown menus |
| `--z-sticky` | 200 | Sticky headers |
| `--z-fixed` | 300 | Page-level fixed nav |
| `--z-modal-backdrop` | 400 | Modal backdrop |
| `--z-modal` | 500 | Modal content |
| `--z-popover` | 600 | Popovers |
| `--z-tooltip` | 700 | Tooltips |
| `--z-toast` | 800 | Toasts — always on top |

## Icons

Standardize on **Lucide** for every OAK app. Don't mix icon libraries — Lucide's geometry doesn't sit cleanly next to Heroicons / Phosphor / Feather.

- **Stroke:** 1.5px (override Lucide's default 2px to match Satoshi's weight)
- **Sizes:** 14, 16, 20, 24
- **Color:** `currentColor` — icons inherit from text color

```jsx
import { Search, X, Check } from 'lucide-react';

<Search size={16} strokeWidth={1.5} />
```

When the system needs an icon Lucide doesn't have, draw it on the same 24×24 grid with 1.5px stroke and round line caps/joins.

## Visual reference

[`oak-brand-guide.html`](./oak-brand-guide.html) — full brand canon page rendered live. Anchor, token tables, surfaces, type ramp, contrast demos with verdicts, components, integration snippets. Open it in a browser when you need to eyeball the system or copy a pattern.

## Starting a new OAK app

Copy [`oak-starter.html`](./oak-starter.html) as your boilerplate. It loads `oak-tokens.css` from canon, sets up the `data-theme` toggle pattern, and gives you working examples of link, button, and card. Replace everything inside `<main>` with your app — keep the token import. Don't fork hex values into your app. If a color or component you need doesn't exist in the system, file an issue against this repo so the system grows.

## Print

For physical brand expressions — business cards, letterhead, swag, signage, print ads. Mathematical CMYK; Pantone candidates need physical Color Bridge verification before any large run.

| Color | RGB hex | CMYK | Pantone (verify) |
|---|---|---|---|
| Truckee Blue | `#4E85DF` | C65 M40 Y0 K13 | 660 C *(primary)* · 285 C · 2728 C |
| Truckee Blue Deep | `#2E66C7` | C77 M49 Y0 K22 | 2728 C · 286 C |
| Cream Paper | `#F2EBE0` | C0 M3 Y8 K5 | — *(prefer uncoated cream stock, skip ink)* |
| Coffee Dark | `#161311` | C0 M30 Y30 K100 *(warm rich black)* | — |

- RGB → CMYK is gamut-limited. Vivid blues like Truckee shift in process print. For brand-critical pieces, prefer Pantone spot color over CMYK.
- Recommended uncoated stocks: Mohawk Strathmore Natural, Crane's Lettra Pearl, Cougar Natural. They run warm out of the box — less ink coverage for cream backgrounds.
- Don't spec flat K100 black — looks cool/grey on most stocks. Use the warm rich black above to preserve OAK's warm temperature.

## Don'ts

- Don't reintroduce Klein Blue. It's retired.
- Don't reintroduce green to the brand surface — greens were systematically removed from landing/pricing in favor of the brand blue.
- Don't reach for pure grays. Warm coffee only.
- Don't put body links on `--accent`. Use `--accent-deep`.
- Don't put text smaller than 14px on `--accent` fills. Lift weight or switch to `--accent-deep`.
- Don't use pure `#000` or `#FFF` on any surface. The text tier handles both modes correctly.
- Don't introduce icons from libraries other than Lucide. Lucide's geometry won't sit cleanly next to Heroicons / Phosphor / Feather.
- Don't hardcode spacing, motion, or z-index values. Reach for the tokens.

---

Marketing site → [oakmediaworks.com](https://oakmediaworks.com) · deploy → [landing-mocha-mu.vercel.app](https://landing-mocha-mu.vercel.app)
