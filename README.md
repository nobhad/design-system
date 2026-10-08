# Design System

The token layer behind [nobhad.codes](https://nobhad.codes): 488 CSS custom
properties across 11 files, serving three surfaces (the main site, an admin
portal and a client portal) from one foundation. It also styles
[Health Ledger](https://github.com/nobhad/health-ledger).

Browse it live at
[nobhad.codes/design-system](https://nobhad.codes/design-system).

This repository is a published copy. The tokens are edited in the private
nobhad.codes repository and copied here when they change.

## The one rule

No component stylesheet contains a literal colour, measurement or duration.
Every value is a named token. Three surfaces can look completely different
because they resolve the same token names to different values, not because
they run different stylesheets.

## Use

Plain CSS, no build step:

```css
@import "fonts.css";
@import "index.css";
```

`index.css` imports every token file except `tokens/portal-theme.css` and adds
a small reset. Import the portal theme separately, outside any `@layer`, when
you want its overrides to beat layered styles:

```css
@import "tokens/portal-theme.css";
```

Light and dark themes switch on `html[data-theme="light"]` and
`html[data-theme="dark"]`. The portal surfaces switch on
`body[data-page="admin"]` and `body[data-page="client"]`.

## Files

| File | What it holds |
| --- | --- |
| `tokens/colors.css` | Palette and semantic colours, both themes |
| `tokens/typography.css` | Families, sizes, weights, line heights |
| `tokens/spacing.css` | The spacing scale |
| `tokens/dimensions.css` | Widths, heights, control sizes |
| `tokens/borders.css` | Widths and radii |
| `tokens/shadows.css` | Elevation |
| `tokens/animations.css` | Durations and easings |
| `tokens/z-index.css` | Stacking order |
| `tokens/buttons.css` | Portal button sizing and type |
| `tokens/breakpoints.css` | `@custom-media` queries |
| `tokens/portal-theme.css` | Portal surface overrides |
| `fonts.css` | `@font-face` for Acme, League Spartan, Michroma and Inconsolata |

Comments in the token files name files from the nobhad.codes repository
(`base/reset.css`, `@layer base` and so on). They explain why a token is
shaped the way it is; those files are not part of this copy.

## Licence

The CSS is MIT. Each font is under the SIL Open Font License; its `OFL.txt`
sits beside it in `fonts/`.
