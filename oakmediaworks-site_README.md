# OAK Media Works — brand canon

The public, canonical home for OAK Media Works design tokens. Anything calling itself OAK should match what's in this repo. In case of conflict, this repo wins.

## Anchor

**Denim Blue** — `#4E85DF`

A working blue. Lived-in, designer-led, not French-institutional. Sits naturally on warm cream paper; lifts cleanly on coffee dark. The tier is built so the canonical hex appears in both modes — light uses it as `--accent`, dark preserves it in `--accent-deep` for fills and chart bands.

> Previously Klein Blue (`#002FA7`). Switched 2026-05-06 — Klein read too clinical against the cream surface. Denim is warmer, more approachable, still distinctly OAK.

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
| `--accent-deep` | `#4E85DF` | Canonical denim — fills behind light text, halos, chart bands |
| `--accent-soft` | `#1A2440` | Wash on dark surfaces |
| `--accent-on` | `#F2EBE0` | Text/icons on accent fills |

## Contrast — read this before you ship

Denim is lighter than Klein. That has consequences.

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
- **Tabular numerals:** apply `font-variant-numeric: var(--num-tabular)` to numeric columns — dollar amounts, scores, counts, timestamps. The `.num`, `[data-num]`, `.tabular`, and `td.num` selectors get it for free.

## Semantic

Status colors are mode-aware. Keep them — don't swap to other greens/reds.

```
                  LIGHT     DARK
--success         #177D4D   #34C77B
--warning         #B5640A   #E89A48
--error           #A8201F   #E15553
```

## Visual reference

[`oak-brand-guide.html`](./oak-brand-guide.html) — every token in both modes, side by side. Open it in a browser when you need to eyeball the system.

## Don'ts

- Don't reintroduce Klein Blue. It's retired.
- Don't reintroduce green to the brand surface — greens were systematically removed from landing/pricing in favor of the brand blue.
- Don't reach for pure grays. Warm coffee only.
- Don't put body links on `--accent`. Use `--accent-deep`.
- Don't put text smaller than 14px on `--accent` fills. Lift weight or switch to `--accent-deep`.
- Don't use pure `#000` or `#FFF` on any surface. The text tier handles both modes correctly.

---

Marketing site → [oakmediaworks.com](https://oakmediaworks.com) · deploy → [landing-mocha-mu.vercel.app](https://landing-mocha-mu.vercel.app)
