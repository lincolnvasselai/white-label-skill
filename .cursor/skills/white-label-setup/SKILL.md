---
name: white-label-setup
description: >-
  Sets up a new white-label brand on the White Label Design System variable
  structure (Core, Semantic, Layout, Typography). Asks how many brand colors
  and fonts the brand has, which are primary, secondary, and tertiary, then
  writes those values into the existing tokens. Use when starting a design
  system, a new brand, white label tokens, variáveis, cores de marca, or
  fonte primária e secundária.
---

# White label setup

One Figma file per brand. The variable structure stays fixed. The wizard collects the brand, then writes only the brand slots.

Source file: `https://www.figma.com/design/tAVy1duQqnqRCYEhc1SA1l/White-Label-%7C-Design-System`

Read [references/structure.md](references/structure.md) and [references/brand-slots.md](references/brand-slots.md) before asking questions or editing variables.

## Wizard

Ask in the user's language. Use AskQuestion for every choice. Hex values, font names, and the brand name go in AskQuestion's Other field. Do not invent a color or a font.

Ask in this order:

1. Brand or client name.
2. How many brand colors? Options: `1 color`, `2 colors`, `3 colors`. More than 3 uses Other.
3. For each color, in order primary, then secondary, then tertiary: the base hex. If they already have a ramp, they paste the steps in Other. A single hex fills only the base slot in [brand-slots.md](references/brand-slots.md).
4. How many font families? Options: `1 font`, `2 fonts`, `3 fonts`. More than 3 uses Other.
5. The family name for each, and which is primary, secondary, and (only when they have 3) tertiary. Names must match a font installed in Figma.
6. Figma style names for Regular and Bold on the primary family. Ask for Medium only when they use it. The string must match Figma (`Bold`, `Semi Bold`). The token name stays `typography/font-weight/bold` even when the style string is `Semi Bold`.

Then show the plan and wait:

```
| Token | New value | What keeps working |
| color/blue/500 | #E11D48 | text/accent, icon/accent |
| typography/font-family/primary | Gotham | every text style |
```

Include a line for each slot you will change and a line for each ramp step you will leave on the template. Apply only after they confirm.

## Apply

Prefer a duplicate of the source file. Update brand slots only.

When the file has no collections, create Core, Semantic, Layout, and Typography from [structure.md](references/structure.md), then set the brand slots. Create Core primitives before Semantic and Typography aliases.

Rules while writing:

- Keep collection names, mode names, and token names from the source.
- Semantic tokens alias Core. Layout spacing aliases `spacing/*`. Typography aliases `typography/*`.
- Set scopes from structure.md. Core scopes stay empty so primitives stay out of the picker.
- Copy known gaps as they are. Do not rename, rescope, or rebalance Dark during setup unless the user asks. The gaps are listed in structure.md.
- A third font family is `typography/font-family/tertiary`. The type ramp stays on primary until they name the styles that should use it.
- Load `figma-use` before any `use_figma` call. Return created and updated variable ids.

## Text styles

After the variables exist, create or update the 78 text styles. Bind font family, font style, font size, line height, and letter spacing to the matching Typography variables.

Style name equals the variable path, with one exception: display and heading use a space instead of a slash before the step.

- Variable `body/regular/default` → style `body/regular/default`
- Variable `display/01/bold/default` → style `display 01/bold/default`
- Variable `heading/06/regular/snug` → style `heading 06/regular/snug`

## Done

Report the brand name, the tokens written, the tokens left on the template, and the Figma file link.
