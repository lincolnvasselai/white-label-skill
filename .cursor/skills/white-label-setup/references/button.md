# Button

Build this after Core, Semantic, Layout, Typography, the 78 text styles, and the 4 button text styles exist. Load `figma-use` before `use_figma`, and `figma-generate-library` before creating or rebinding the component.

The source file has an empty `Components` collection, mode `Mode 1`. Fill that collection. Do not add a mode and do not create a second collection. If the file has no Components collection, create it with mode `Mode 1` before the variables.

The example set is `button` on the Buttons page. If that set exists, rebind it. Do not create a second set. If it does not exist, build one set named `button` with the same axes.

Every paint, size, radius, gap, stroke, and label comes from a variable or a text style. No Gotham style and no raw hex remain on the set. Width hugs the label plus padding. The example width 195 is not a token.

## Text styles

One local text style per size. Bind family to `typography/font-family/primary`, font style to `typography/font-weight/medium`, letter spacing to `typography/letter-spacing/0`. Before binding, set `typography/font-weight/medium` to the string `Medium` so the style matches a Figma font.

Size and line height bind to Core. Add the missing tokens first: `typography/font-size/18`, `typography/line-height/19,2`, `typography/line-height/21,6`, `typography/line-height/28,8`. Figma rejects a period in a variable name, so the decimal line heights use a comma, the same way letter-spacing does. The stored numbers are 19.2, 21.6, and 28.8. Size 16, 20, and 24 and line height 24 already exist. Line height is 1.2 times the size.

| Style | Size token | Line-height token |
| --- | --- | --- |
| `button/extra large` | `typography/font-size/24` | `typography/line-height/28,8` |
| `button/large` | `typography/font-size/20` | `typography/line-height/24` |
| `button/medium` | `typography/font-size/18` | `typography/line-height/21,6` |
| `button/small` | `typography/font-size/16` | `typography/line-height/19,2` |

## Size and shape

Number variables in Components. Height, padding, and icon use scope `WIDTH_HEIGHT`. Gap uses `GAP`. Radius uses `CORNER_RADIUS`. Stroke width uses `STROKE_FLOAT`.

| Token | Value |
| --- | --- |
| `button/gap` | 8 |
| `button/radius` | 32 |
| `button/stroke-width` | 1 |
| `button/focus-stroke-width` | 2 |
| `button/extra-large/height` | 64 |
| `button/extra-large/padding-x` | 32 |
| `button/extra-large/padding-y` | 16 |
| `button/extra-large/icon` | 24 |
| `button/large/height` | 56 |
| `button/large/padding-x` | 24 |
| `button/large/padding-y` | 16 |
| `button/large/icon` | 20 |
| `button/medium/height` | 48 |
| `button/medium/padding-x` | 20 |
| `button/medium/padding-y` | 12 |
| `button/medium/icon` | 18 |
| `button/small/height` | 40 |
| `button/small/padding-x` | 14 |
| `button/small/padding-y` | 8 |
| `button/small/icon` | 16 |

Padding left and right use `padding-x`. Padding top and bottom use `padding-y`. Icon width and height use `icon`.

## Color

Color variables in Components alias Core. They do not store a raw hex. Fill variables are scoped to frame fill and shape fill. Stroke variables are scoped to stroke. Label variables are scoped to text fill.

Primary default and hover are linear gradients. The first stop is at 0.2 and the second stop is at 1. Bind those stops to `fill-start` and `fill-end`.

| Token | Aliases |
| --- | --- |
| `button/primary/default/fill-start` | `color/blue/600` |
| `button/primary/default/fill-end` | `color/blue/400` |
| `button/primary/default/label` | `color/gray/000` |
| `button/primary/hover/fill-start` | `color/blue/400` |
| `button/primary/hover/fill-end` | `color/blue/300` |
| `button/primary/hover/label` | `color/gray/000` |
| `button/primary/disabled/fill` | `color/gray/200` |
| `button/primary/disabled/label` | `color/gray/000` |
| `button/primary/focus/fill-start` | `color/blue/600` |
| `button/primary/focus/fill-end` | `color/blue/400` |
| `button/primary/focus/stroke` | `color/gray/000` |
| `button/primary/focus/label` | `color/gray/000` |
| `button/secondary/default/fill` | `color/gray/000` |
| `button/secondary/default/stroke` | `color/blue/500` |
| `button/secondary/default/label` | `color/blue/500` |
| `button/secondary/hover/fill` | `color/gray/000` |
| `button/secondary/hover/stroke` | `color/blue/300` |
| `button/secondary/hover/label` | `color/blue/300` |
| `button/secondary/disabled/fill` | `color/gray/000` |
| `button/secondary/disabled/stroke` | `color/gray/200` |
| `button/secondary/disabled/label` | `color/gray/200` |
| `button/secondary/focus/fill` | `color/gray/000` |
| `button/secondary/focus/stroke` | `color/blue/500` |
| `button/secondary/focus/label` | `color/blue/500` |
| `button/ghost-dark/default/fill` | `color/gray/000` |
| `button/ghost-dark/default/stroke` | `color/gray/900` |
| `button/ghost-dark/default/label` | `color/gray/900` |
| `button/ghost-dark/hover/fill` | `color/gray/000` |
| `button/ghost-dark/hover/stroke` | `color/gray/200` |
| `button/ghost-dark/hover/label` | `color/gray/400` |
| `button/ghost-dark/disabled/fill` | `color/gray/000` |
| `button/ghost-dark/disabled/stroke` | `color/gray/200` |
| `button/ghost-dark/disabled/label` | `color/gray/200` |
| `button/ghost-dark/focus/fill` | `color/gray/000` |
| `button/ghost-dark/focus/stroke` | `color/blue/500` |
| `button/ghost-dark/focus/label` | `color/gray/900` |
| `button/ghost-light/default/stroke` | `color/gray/000` |
| `button/ghost-light/default/label` | `color/gray/000` |
| `button/ghost-light/hover/fill` | `color/light-gamma/200` |
| `button/ghost-light/hover/stroke` | `color/gray/000` |
| `button/ghost-light/hover/label` | `color/gray/000` |
| `button/ghost-light/disabled/stroke` | `color/gray/200` |
| `button/ghost-light/disabled/label` | `color/gray/200` |
| `button/ghost-light/focus/stroke` | `color/gray/000` |
| `button/ghost-light/focus/label` | `color/gray/000` |

Ghost light default, focus, and disabled have no fill. Do not invent a fill variable for them. `color/light-gamma/200` is white at 20% opacity.

Focus keeps that type's default fill and label. Its stroke is a 2px ring, aligned outside, bound to `button/focus-stroke-width`. Primary and ghost light use a white ring. Secondary and ghost dark use `color/blue/500`.

Do not copy example hexes that are not tokens (`#2b85c3`, `#37a6f3`, `#474747`, `#adadad`).

## Component

One set named `button`. Variant properties, in order: `size`, `type`, `status`.

- `size`: `extra large`, `large`, `medium`, `small`
- `type`: `primary`, `secondary`, `ghost dark`, `ghost light`
- `status`: `default`, `hover`, `disabled`, `focus`

Boolean properties, default true: `show left icon`, `show right icon`.

Each variant is a horizontal auto-layout frame. Primary and counter alignment are center. Height is fixed from the size token. Width hugs the label and icons. Bind `strokeTopWeight`, `strokeBottomWeight`, `strokeLeftWeight`, and `strokeRightWeight` to `button/stroke-width`. Focus binds those four sides to `button/focus-stroke-width` and sets `strokeAlign` to `OUTSIDE`. Gap is `button/gap`. Corner radius is `button/radius`.

Children, in order: left icon instance, text layer named `Label` with the characters `Label`, right icon instance. The booleans control the two icons. The label uses the text style for that size. Icon width and height use that size's `icon` token.

64 variants. Place the set on the Buttons page. Return the component set id and the variant count.
