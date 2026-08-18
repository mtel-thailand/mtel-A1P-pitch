# Typography Review

## Summary

The typography system now uses a single font family in `globals.css`:

- `DM Sans` is used for headings, body copy, buttons, badges, labels, and supporting UI text.

This makes the system simpler and more consistent. The main structure now comes from font size, weight, line-height, and letter-spacing rather than a serif/sans pairing.

## Current UI Notes

- Slide 04 now uses the shared background token `--slide-04-bg-image` from `globals.css`.
- Slides 08 and 09 use matching `Live demo` labels with a green status dot and AI-icon `Generate` buttons.
- Slide 11 uses image-driven industry tabs with a separate white content panel for readability.

## Font Family

| Token | Value | Use |
| --- | --- | --- |
| `--font-body` | `'DM Sans', sans-serif` | All text styles across the site |

## Type Scale

### Core tokens

| Token | Value | Typical use |
| --- | --- | --- |
| `--text-h1` | `clamp(2rem, 5vw, 3.5rem)` | Primary page / hero heading |
| `--text-h2` | `clamp(2rem, 4vw, 2.75rem)` | Section heading |
| `--text-h3` | `clamp(1.5rem, 2.5vw, 2rem)` | Subsection heading |
| `--text-h4` | `clamp(1.125rem, 1rem + 0.5vw, 1.25rem)` | Card / detail heading |
| `--text-h5` | `clamp(1rem, 0.95rem + 0.25vw, 1.125rem)` | Small heading |
| `--text-stat` | `clamp(2.25rem, 4vw, 3.5rem)` | Large stat numbers |
| `--text-body-lg` | `clamp(1rem, 0.96rem + 0.24vw, 1.125rem)` | Intro / lead paragraph |
| `--text-body` | `clamp(0.9375rem, 0.915rem + 0.11vw, 1rem)` | Default body text |
| `--text-sm` | `clamp(0.8125rem, 0.79rem + 0.11vw, 0.875rem)` | Supporting small copy |
| `--text-xs` | `clamp(0.75rem, 0.73rem + 0.09vw, 0.8125rem)` | Labels, badges, UI microcopy |
| `--text-micro` | `clamp(0.6875rem, 0.67rem + 0.08vw, 0.75rem)` | Tiny helper labels |
| `--text-paper-label` | `clamp(1.75rem, 1.35rem + 1.2vw, 2.125rem)` | CTA paper label |
| `--text-paper-alert` | `clamp(2.25rem, 1.8rem + 1.55vw, 2.875rem)` | CTA paper alert |
| `--text-paper-question` | `clamp(2.75rem, 2.2rem + 2vw, 3.625rem)` | CTA paper question |
| `--btn-font-size` | `clamp(0.75rem, 0.72rem + 0.12vw, 0.8125rem)` | Buttons |

### Responsive comparison

| Token | Clamp value | 1920px screen | 1440px screen | 375px screen |
| --- | --- | --- | --- | --- |
| `--text-h1` | `clamp(2rem, 5vw, 3.5rem)` | `56px` | `56px` | `32px` |
| `--text-h2` | `clamp(2rem, 4vw, 2.75rem)` | `44px` | `44px` | `32px` |
| `--text-h3` | `clamp(1.5rem, 2.5vw, 2rem)` | `32px` | `32px` | `24px` |
| `--text-h4` | `clamp(1.125rem, 1rem + 0.5vw, 1.25rem)` | `20px` | `20px` | `18px` |
| `--text-h5` | `clamp(1rem, 0.95rem + 0.25vw, 1.125rem)` | `18px` | `18px` | `16.14px` |
| `--text-stat` | `clamp(2.25rem, 4vw, 3.5rem)` | `56px` | `56px` | `36px` |
| `--text-body-lg` | `clamp(1rem, 0.96rem + 0.24vw, 1.125rem)` | `18px` | `18px` | `16.26px` |
| `--text-body` | `clamp(0.9375rem, 0.915rem + 0.11vw, 1rem)` | `16px` | `16px` | `15.05px` |
| `--text-sm` | `clamp(0.8125rem, 0.79rem + 0.11vw, 0.875rem)` | `14px` | `14px` | `13.05px` |
| `--text-xs` | `clamp(0.75rem, 0.73rem + 0.09vw, 0.8125rem)` | `13px` | `12.98px` | `12.02px` |
| `--text-micro` | `clamp(0.6875rem, 0.67rem + 0.08vw, 0.75rem)` | `12px` | `11.87px` | `11.02px` |
| `--text-paper-label` | `clamp(1.75rem, 1.35rem + 1.2vw, 2.125rem)` | `34px` | `34px` | `28px` |
| `--text-paper-alert` | `clamp(2.25rem, 1.8rem + 1.55vw, 2.875rem)` | `46px` | `46px` | `36px` |
| `--text-paper-question` | `clamp(2.75rem, 2.2rem + 2vw, 3.625rem)` | `58px` | `58px` | `44px` |
| `--btn-font-size` | `clamp(0.75rem, 0.72rem + 0.12vw, 0.8125rem)` | `13px` | `13px` | `12px` |

## Current CSS Structure

- `body` uses `--font-body`, `--text-body`, weight `400`, and line-height `1.5`
- `h1` to `h5` use `--font-body`, weight `700`, line-height `1.1`, and `-0.02em` letter-spacing
- `p` uses relaxed line-height `1.65`
- Labels and chips mostly use `--text-xs` with uppercase and extra tracking

## Usage Rules

### Headings

- Use `DM Sans` with size and weight to create hierarchy.
- Keep headings tight with `line-height: 1.1`.
- Use `letter-spacing: -0.02em` on large headings for a denser editorial feel.

### Body copy

- Use `--text-body` for standard copy.
- Use `--text-body-lg` for lead paragraphs, intros, and CTA support text.
- Keep reading text relaxed with `line-height: 1.65`.

### Labels and UI text

- Use `--text-xs` for badges, pills, and metadata.
- Use `--text-micro` only for very small helper labels like scroll cues.
- Use semibold or bold weights for compact UI elements.
- Uppercase plus increased letter-spacing remains the standard label pattern.

## Where Each Size Is Used

### `--text-h1`

- `h1`
- Best for hero headlines and primary titles

### `--text-h2`

- `h2`
- `.bottom-cta-heading`
- `.section-intro h2`
- `.data h2`
- `.exclusivity h2`
- `.pillars-section h2`
- `.create-faster-left h2`
- `.understand-left h2`
- `.outcomes h2`
- Best for section titles

### `--text-h3`

- `h3`
- All slide-specific `h3` selectors
- Best for subsection titles and card headlines

### `--text-h4`

- `h4`
- `.pricing-factor h4`
- Best for card and detail headings

### `--text-h5`

- `h5`
- Best for small headings

### `--text-stat`

- Defined for KPI and metric styling
- Not clearly applied to a selector yet

### `--text-body-lg`

- `.bottom-cta-copy`
- Best for intro and support copy

### `--text-body`

- `body`
- `.btn-link`
- Best for default paragraph and general UI text

### `--text-sm`

- Defined for small supporting copy
- Not clearly applied to a selector yet

### `--text-xs`

- `.bottom-cta-eyebrow`
- `.badge`
- `.section-pill`
- `.section-label`
- `.label-pill-light`
- `.label-pill-dark`

### `--text-micro`

- `.hero-scroll-label`

### Special display tokens

- `.bottom-cta-paper-label`: `--text-paper-label`
- `.bottom-cta-paper-question`: `--text-paper-question`
- `.bottom-cta-paper-alert`: `--text-paper-alert`
- `.btn`: `--btn-font-size`

## Font Weights

| Token | Value | Typical use |
| --- | --- | --- |
| `--weight-regular` | `400` | Body text |
| `--weight-medium` | `500` | Secondary emphasis |
| `--weight-semibold` | `600` | Labels, pills, links |
| `--weight-bold` | `700` | Headings, buttons |
| `--weight-extrabold` | `800` | Strong CTA headings |

## Spacing and Case Rules

- Headings: `line-height: 1.1`
- Body/UI default: `line-height: 1.5`
- Reading copy: `line-height: 1.65`
- Labels: uppercase with `0.06em` to `0.1em` letter-spacing
- Buttons: uppercase with `0.07em` letter-spacing
- Hero scroll cue: `0.15em` letter-spacing

## Audit Notes

- The system is now simpler because all text uses one family.
- Hierarchy depends on size, weight, spacing, and case rather than font contrast.
- `--text-stat` and `--text-sm` are still defined but not clearly mapped to live selectors.
- Most text sizing is token-driven and responsive via `clamp()`.
- Standard slide `h2` selectors use `--text-h2`, keeping their maximum size consistent at `44px`.
- All semantic headings from `h1` through `h5` use global size tokens.
- Slide-specific heading selectors may change color, spacing, or line-height, but not their global font size.

## Recommended Organization

| Content type | Recommended rule |
| --- | --- |
| Hero / primary title | `--text-h1` + `--font-body` + `--weight-bold` |
| Section title | `--text-h2` + `--font-body` + `--weight-bold` |
| Subsection title | `--text-h3` + `--font-body` + `--weight-bold` |
| Card / detail heading | `--text-h4` + `--font-body` + `--weight-bold` |
| Small heading | `--text-h5` + `--font-body` + `--weight-bold` |
| KPI / stat value | `--text-stat` + `--font-body` + `--weight-bold` |
| Intro / lede | `--text-body-lg` + `--font-body` |
| Standard paragraph | `--text-body` + `--font-body` |
| Small support text | `--text-sm` + `--font-body` |
| Label / badge / pill | `--text-xs` + `--font-body` + uppercase |
