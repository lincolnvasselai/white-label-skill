# Variable structure

Copied from the White Label Design System file. Names, modes, and aliases below are the source of truth for a new file.

## Collections

| Collection | Modes | Default | Variables | Holds |
| --- | --- | --- | --- | --- |
| Core | Mode 1 | Mode 1 | 169 | Raw values. No aliases except gamma colors |
| Semantic | Light, Dark | Light | 41 | Color, radius, and border-width aliases into Core |
| Layout | Desktop, Mobile | Desktop | 17 | Grid numbers and spacing aliases |
| Typography | Desktop, Mobile | Desktop | 390 | Composite type aliases into Core |

Desktop/Mobile exist on both Layout and Typography. A frame needs both modes set.

Core scopes are empty, so primitives do not appear in the property picker. Designers apply Semantic color, Layout spacing, and text styles.

## Core naming

kebab-case, grouped with `/`.

| Group | Pattern | Steps |
| --- | --- | --- |
| Color | `color/{ramp}/{step}` | see ramps below |
| Border | `border/{n}` | 0, 1, 2, 3 (px) |
| Radius | `radius/{n}` | 0, 1, 2, 4, 8, 999 |
| Spacing | `spacing/{n}` | 0, 4, 8, 12, 16, 20, 24, 28, 32, 36, 40, 44, 48, 52, 56, 60, 64, 80 |
| Dimension | `dimension/{n}` | 1, 2, 4, 6, 8, 12, 16, 18, 20, 21, 24, 28, 32, 36, 40, 44, 48, 56 |
| Type family | `typography/font-family/{role}` | primary, secondary |
| Type size | `typography/font-size/{px}` | 10, 12, 16, 20, 24, 28, 32, 36, 40, 44, 48, 56, 64 |
| Type weight | `typography/font-weight/{name}` | regular `Regular`, medium `medium`, bold `Bold` |
| Tracking | `typography/letter-spacing/{name}` | `-0,01` `-0.01`, `-0,02` `-0.02`, `0` `0`, `0,01` `0.01`, `0,02` `0.02` |
| Line height | `typography/line-height/{px}` | 10, 12, 14, 16, 18, 20, 21, 22, 24, 28, 30, 32, 34, 36, 38, 40, 42, 44, 46, 48, 52, 54, 56, 58, 60, 64, 66, 68, 72, 76, 84, 96, 98 |

Float value equals the number in the name, except letter-spacing (the signed fraction) and weights/families (strings).

### Color ramps

`color/blue`: 000 `#f3fbff`, 050 `#e2f6ff`, 100 `#c7edfc`, 200 `#9ddef5`, 300 `#6ccbec`, 400 `#35b4e2`, 500 `#0092d8`, 600 `#007bb9`, 700 `#006398`, 800 `#004b74`, 900 `#00284c`, 950 `#001b34`

`color/azure`: 100 `#e8f4ff`, 200 `#bddcff`, 300 `#3a82ff`, 400 `#0f5fff`, 500 `#0946d2`

`color/gray`: 000 `#ffffff`, 025 `#fafafa`, 050 `#f5f5f5`, 100 `#eaeaea`, 200 `#d6d6d6`, 300 `#c1c1c1`, 400 `#acacac`, 500 `#969696`, 600 `#808080`, 700 `#6b6b6b`, 800 `#575757`, 900 `#454545`, 980 `#333333`, 1000 `#000000`

`color/green`: 100 `#e8ffec`, 200 `#aff0bc`, 300 `#24c454`, 400 `#00b53c`, 500 `#009b39`

`color/orange`: 100 `#fff7e8`, 200 `#ffe3ba`, 300 `#ff972e`, 400 `#ff7700`, 500 `#d25b00`

`color/red`: 100 `#ffece8`, 200 `#fbc3ba`, 300 `#f13d36`, 400 `#ed0d0d`, 500 `#c5080e`

`color/purple/purple-500`: `#551a8b`

`color/dark-gamma/{step}` aliases `color/gray/980` with opacity. Steps: 040, 080, 120, 160, 200, 320, 440, 560, 720, 880. The stored opacity number matches the step (`040` → 4).

`color/light-gamma/{step}` aliases `color/gray/000` the same way. Steps: 050, 080, 120, 160, 200, 320, 440, 560, 720, 880.

Template families: primary `Montserrat`, secondary `String value`.

## Semantic

Every token aliases Core. Light and Dark match, except the three rows marked Dark.

| Token | Scope | Light and Dark alias |
| --- | --- | --- |
| `background/inverse` | FRAME_FILL | `color/gray/800` |
| `background/primary` | FRAME_FILL | `color/gray/000` |
| `background/secondary` | FRAME_FILL | `color/gray/100` |
| `border-radius/full` | ALL_SCOPES | `radius/999` |
| `border-radius/primary` | CORNER_RADIUS | `radius/4` |
| `border-width/none` | ALL_SCOPES | `border/0` |
| `border-width/primary` | ALL_SCOPES | `border/1` |
| `icon/accent` | SHAPE_FILL | `color/blue/500` |
| `icon/danger` | SHAPE_FILL | Light `color/red/400`, Dark `color/gray/000` |
| `icon/danger-inverse` | SHAPE_FILL | `color/gray/000` |
| `icon/disabled` | SHAPE_FILL | `color/gray/400` |
| `icon/info` | SHAPE_FILL | Light `color/azure/400`, Dark `color/gray/000` |
| `icon/info-inverse` | SHAPE_FILL | `color/gray/000` |
| `icon/inverse` | SHAPE_FILL | `color/gray/000` |
| `icon/primary` | SHAPE_FILL | `color/gray/980` |
| `icon/succes-inverse` | SHAPE_FILL | `color/gray/000` |
| `icon/success` | SHAPE_FILL | `color/green/400` |
| `icon/warning` | SHAPE_FILL | Light `color/orange/400`, Dark `color/gray/000` |
| `icon/warning-inverse` | SHAPE_FILL | `color/gray/000` |
| `surface/danger` | FRAME_FILL | `color/red/500` |
| `surface/info` | FRAME_FILL | `color/azure/500` |
| `surface/inverse` | FRAME_FILL | `color/gray/980` |
| `surface/primary` | FRAME_FILL | `color/gray/000` |
| `surface/success` | FRAME_FILL | `color/green/500` |
| `surface/warning` | FRAME_FILL | `color/orange/500` |
| `text/accent` | TEXT_FILL | `color/blue/500` |
| `text/danger` | FRAME_FILL | `color/red/400` |
| `text/danger-inverted` | FRAME_FILL | `color/gray/000` |
| `text/disabled` | TEXT_FILL | `color/gray/400` |
| `text/info` | FRAME_FILL | `color/azure/400` |
| `text/inverse` | TEXT_FILL | `color/gray/000` |
| `text/link` | TEXT_FILL | `color/azure/500` |
| `text/link-hover` | TEXT_FILL | `color/azure/300` |
| `text/link-visited` | TEXT_FILL | `color/purple/purple-500` |
| `text/primary` | TEXT_FILL | `color/gray/980` |
| `text/secondary` | TEXT_FILL | `color/gray/700` |
| `text/success` | FRAME_FILL | `color/green/400` |
| `text/success-inverted` | FRAME_FILL | `color/gray/000` |
| `text/tertiary` | TEXT_FILL | `color/gray/500` |
| `text/warning` | FRAME_FILL | `color/orange/400` |
| `text/warning-inverted` | FRAME_FILL | `color/gray/000` |

## Layout

Grid and measure are raw numbers. Spacing aliases Core. Spacing scopes are `ALL_SCOPES`. Grid scopes are empty. Measure scopes are `WIDTH_HEIGHT`.

| Token | Desktop | Mobile |
| --- | --- | --- |
| `grid/columns` | 12 | 4 |
| `grid/gutter` | 16 | 12 |
| `grid/margin` | 64 | 16 |
| `measure/max width` | 1920 | 768 |
| `measure/min width` | 1366 | 360 |
| `spacing/inline/compact` | `spacing/4` | `spacing/4` |
| `spacing/inline/default` | `spacing/8` | `spacing/8` |
| `spacing/inline/spacious` | `spacing/12` | `spacing/12` |
| `spacing/inset/compact` | `spacing/4` | `spacing/8` |
| `spacing/inset/default` | `spacing/8` | `spacing/12` |
| `spacing/inset/spacious` | `spacing/12` | `spacing/16` |
| `spacing/section/compact` | `spacing/4` | `spacing/16` |
| `spacing/section/default` | `spacing/8` | `spacing/24` |
| `spacing/section/spacious` | `spacing/12` | `spacing/40` |
| `spacing/stack/compact` | `spacing/4` | `spacing/4` |
| `spacing/stack/default` | `spacing/8` | `spacing/8` |
| `spacing/stack/spacious` | `spacing/12` | `spacing/12` |

## Typography

390 variables, all aliases. Five properties per style: `font-family`, `font-weight`, `font-size`, `line-height`, `letter-spacing`.

Path:

- Text roles: `{role}/{weight}/{density}/{prop}`
- Display and heading: `{role}/{step}/{weight}/{density}/{prop}`

Roles: `display` steps 01–03, `heading` steps 01–06, `lead`, `body`, `caption`, `micro`.

Weights in the ramp: `regular`, `bold`. Densities: `default`, `snug`, `comfortable`.

Every style aliases `typography/font-family/primary`, the matching weight token, and `typography/letter-spacing/0` on both modes. Size and line-height come from the table. Bold uses the same size and line-height as regular.

Line-height cells are default / snug / comfortable, in px.

| Style | Desktop size | Desktop line-height | Mobile size | Mobile line-height |
| --- | --- | --- | --- | --- |
| display/01 | 64 | 64 / 76 / 96 | 48 | 48 / 58 / 72 |
| display/02 | 56 | 56 / 68 / 84 | 44 | 44 / 54 / 66 |
| display/03 | 48 | 48 / 58 / 72 | 40 | 40 / 48 / 60 |
| heading/01 | 44 | 44 / 54 / 66 | 36 | 36 / 44 / 54 |
| heading/02 | 40 | 40 / 48 / 60 | 32 | 32 / 40 / 48 |
| heading/03 | 36 | 36 / 44 / 54 | 28 | 28 / 34 / 42 |
| heading/04 | 32 | 32 / 40 / 48 | 24 | 24 / 30 / 36 |
| heading/05 | 28 | 28 / 34 / 42 | 20 | 20 / 24 / 30 |
| heading/06 | 24 | 24 / 30 / 36 | 16 | 16 / 20 / 24 |
| lead | 20 | 20 / 24 / 30 | 20 | 20 / 24 / 30 |
| body | 16 | 16 / 20 / 24 | 16 | 16 / 20 / 24 |
| caption | 12 | 12 / 14 / 18 | 12 | 12 / 14 / 18 |
| micro | 10 | 10 / 12 / 14 | 10 | 10 / 12 / 14 |

`lead`, `body`, `caption`, and `micro` use the same size on Desktop and Mobile.

Text style names match these paths. Display and heading insert a space before the step: `display 01/bold/default`, `heading 06/regular/snug`.

## Known gaps to copy as-is

Leave these alone during setup unless the user asks to change them.

- Dark matches Light on 38 of 41 semantic tokens. Only `icon/danger`, `icon/info`, and `icon/warning` change, and they alias `color/gray/000`.
- `icon/succes-inverse` is missing an `s`. Inverse suffixes mix `-inverse` and `-inverted`.
- `color/purple/purple-500` repeats the ramp name. `measure/max width` and `measure/min width` contain a space.
- `typography/font-weight/medium` is the string `medium`. `typography/font-family/secondary` is `String value` until the wizard replaces it.
- Letter-spacing names use a comma (`-0,01`).
- Several text tokens use scope `FRAME_FILL`.
- `default` line-height equals the font size. `snug` is looser than `default`. `comfortable` is the loosest.
