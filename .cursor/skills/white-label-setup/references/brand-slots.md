# Brand slots

The source file is the White Label Design System. The wizard replaces the brand slots. Shared scales and functional ramps stay as documented in [structure.md](structure.md).

## Default primary color

`color/blue` is the shade template, stored in Core. Step 500 is `#0092d8`. The other steps are shades of that hex. See [structure.md](structure.md). Leave `color/blue` on those source hexes.

`color/primary` is the brand primary ramp. It uses the same steps. The source default copies each blue hex into the matching `color/primary` step. A new primary brand color replaces `color/primary` only. `text/accent` and `icon/accent` alias `color/primary/500`. Button brand colors alias `color/primary`.

## How a brand hex becomes a ramp

Steps match `color/blue`: `000`, `050`, `100`, `200`, `300`, `400`, `500`, `600`, `700`, `800`, `900`, `950`.

The hex they give is step `500`. Generate the other steps in OKLab so each step relates to that hex the way the source blue step relates to `#0092d8`. Keep the new color's hue. Lighter steps move toward white. Darker steps move toward the dark end of the same hue.

1. Convert the given hex to OKLab. Record `L`, chroma `C`, and hue. This is step `500`.
2. White is `#ffffff`. For a lighter step, `L = L500 + t * (Lwhite - L500)` and chroma is `C500` times the scale below.
3. For a darker step, `L = L500 - t * (L500 - 0.2176)` and chroma is `C500` times the scale below. `0.2176` is the OKLab lightness of source step `950`. Clamp `L` to the range 0–1.
4. Rebuild `a` and `b` from the new hue and the new chroma. Convert back to sRGB hex.

| Step | Toward white `t` | Toward dark `t` | Chroma scale |
| --- | --- | --- | --- |
| `000` | 0.9547 | | 0.0687 |
| `050` | 0.8949 | | 0.1666 |
| `100` | 0.7938 | | 0.3046 |
| `200` | 0.6344 | | 0.4985 |
| `300` | 0.4490 | | 0.6935 |
| `400` | 0.2480 | | 0.8584 |
| `500` | 0 | 0 | 1 |
| `600` | | 0.1754 | 0.8991 |
| `700` | | 0.3657 | 0.7857 |
| `800` | | 0.5687 | 0.6428 |
| `900` | | 0.8643 | 0.5407 |
| `950` | | 1 | 0.4088 |

A pasted ramp replaces the steps they send. Any step they leave out is still generated from their `500`. The plan names every generated step.

## Colors

| Order | Role in the file | Ramp | Semantic tokens that follow it | In the source file |
| --- | --- | --- | --- | --- |
| Primary | Accent | `color/primary` | `text/accent`, `icon/accent` on step `500`. Button brand colors use the matching step | Source default copies `color/blue` |
| Secondary | Extra brand ramp | `color/secondary` | None during setup | Created only when they ask for 2 or 3 colors |
| Tertiary | Extra brand ramp | `color/tertiary` | None during setup | Created only when they ask for 3 colors |

`color/secondary` and `color/tertiary` use the same steps as `color/blue`. Do not write them into `color/azure` or `color/purple`. Do not point Semantic tokens at them.

Functional ramps stay as they are. Do not offer them as brand color answers.

- Azure is links and info: `text/link`, `text/link-hover`, `text/info`, `icon/info`, `surface/info`.
- Purple is the visited link: `text/link-visited` → `color/purple/purple-500`.
- Green is success. Orange is warning. Red is danger.
- Gray is neutral.

With 1 color, write primary only. With 2, primary and secondary. With 3, all three. Extra colors beyond three need a new Core ramp and an explicit semantic token; ask before creating either.

The plan says that azure, purple, green, orange, and red were not changed.

## Fonts

| Answer | Token | Effect |
| --- | --- | --- |
| Primary family | `typography/font-family/primary` | Every text style, because the ramp aliases this token |
| Secondary family | `typography/font-family/secondary` | Stored. No style uses it until the user assigns one |
| Tertiary family | `typography/font-family/tertiary` | Create only when they have 3 or more families. Ramp stays on primary |
| Regular style name | `typography/font-weight/regular` | Styles whose path contains `/regular/` |
| Bold style name | `typography/font-weight/bold` | Styles whose path contains `/bold/` |
| Medium style name | `typography/font-weight/medium` | Button labels. Set the string to `Medium` before binding those styles |

With 1 font, set primary and set secondary to the same family so the placeholder `String value` is gone.

## What the plan must show

For each written token: name, new value, and the aliases that resolve through it.

For each generated `color/primary`, `color/secondary`, or `color/tertiary` step: the token name and the hex. `color/blue` stays on the source hexes.

For each functional ramp left unchanged: the ramp name and that it stays on the source default.
