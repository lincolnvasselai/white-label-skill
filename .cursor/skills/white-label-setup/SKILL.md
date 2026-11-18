---
name: white-label-setup
description: >-
  Sets up a white-label brand on the White Label Design System (Core,
  Semantic, Layout, Typography, Components). Opens with Full setup or Skip
  setup. Full setup asks Colors, then Fonts. Skip setup builds the source
  defaults. color/blue is the primary ramp and the shade template. Secondary
  and tertiary are new ramps. Creates 82 text styles and a button bound to
  Components variables. Use when starting a design system, a new brand, white
  label tokens, variáveis, cores de marca, button, or fonte primária e
  secundária.
---

# White label setup

One Figma file per brand. The file keeps the source name. The wizard does not ask for a brand name.

Source file: the White Label Design System at `https://www.figma.com/design/bodT19MTa9LqB0qFgjYWK6/White-Label-%7C-Design-System`

`color/blue` in Core is the source default primary brand color and the shade template for any other brand ramp. Step `color/blue/500` (`#0092d8`) is the base. `text/accent` and `icon/accent` alias that step. A new primary replaces the whole ramp. Read [references/brand-slots.md](references/brand-slots.md) before treating any other Core value as a brand color.

Read [references/structure.md](references/structure.md), [references/brand-slots.md](references/brand-slots.md), and [references/button.md](references/button.md) before asking questions or editing the file.

## Wizard

Ask in the user's language. Use AskQuestion for every choice. Hex values and font names go in Other. Do not invent a color or a font. Do not ask for a brand name.

The first question is the only fork. There is no per-group skip.

Question: How do you want to go through the setup?

| Option id | What happens |
| --- | --- |
| Full setup | Ask Colors, then Fonts. Then show the plan and wait. |
| Skip setup | Ask nothing else. Build the source defaults for every collection, the 82 text styles, and the button. This choice is the confirmation. |

### Full setup

1. **Colors.** How many brand colors? Options: `1 color`, `2 colors`, `3 colors`. More than 3 uses Other. Then the base hex for primary, and for secondary and tertiary only when they asked for them. Follow [brand-slots.md](references/brand-slots.md). One hex is step `500`. Generate the rest of that ramp. A pasted ramp replaces the steps they send. Missing steps are still generated from their `500`.
2. **Fonts.** How many families? Options: `1 font`, `2 fonts`, `3 fonts`. More than 3 uses Other. Then the family name for each, and which is primary, secondary, and (only when they have 3) tertiary. Names must match a font installed in Figma. Then the Figma style names for Regular and Bold on the primary family. Ask for Medium only when they use it. The string must match Figma (`Bold`, `Semi Bold`). The token name stays `typography/font-weight/bold` even when the style string is `Semi Bold`.

Layout, spacing, gray, and the functional ramps stay on the source defaults. They are not questions. Functional ramps are azure (links and info), purple (visited link), green (success), orange (warning), and red (danger).

Show the plan after Fonts. List every generated ramp step. Say that azure, purple, green, orange, and red were not changed. Apply only after they confirm.

Text styles and the button are not questions. Build them after the variables exist.

## Apply

Prefer a duplicate of the source file.

When the file has no collections, create Core, Semantic, Layout, Typography, and Components from [structure.md](references/structure.md), then set the brand slots. Create Core primitives before Semantic, Typography, and Components aliases.

When Components already exists and is empty, fill it. Do not create a second Components collection.

Rules while writing:

- Keep collection names, mode names, and token names from the source.
- Semantic tokens alias Core. Layout spacing aliases `spacing/*`. Typography aliases `typography/*`. Components colors alias Core.
- Set scopes from structure.md and [button.md](references/button.md). Core scopes stay empty so primitives stay out of the picker.
- Copy known gaps as they are. Do not rename, rescope, or rebalance Dark during setup unless the user asks. The gaps are listed in structure.md.
- A third font family is `typography/font-family/tertiary`. The type ramp stays on primary until they name the styles that should use it.
- Do not write a brand secondary or tertiary color into `color/azure` or `color/purple`.
- Load `figma-use` before any `use_figma` call. Return created and updated variable ids.

## Text styles

After the variables exist, create or update the 78 text styles, then the 4 button text styles. Bind font family, font style, font size, line height, and letter spacing to variables.

Style name equals the variable path, with one exception: display and heading use a space instead of a slash before the step.

- Variable `body/regular/default` → style `body/regular/default`
- Variable `display/01/bold/default` → style `display 01/bold/default`
- Variable `heading/06/regular/snug` → style `heading 06/regular/snug`

Button text styles are in [button.md](references/button.md). The done report counts 82 text styles.

## Button

After the text styles exist, create the Components variables and build or rebind the `button` set from [button.md](references/button.md). Load `figma-generate-library` before creating or rebinding that component. Skip setup builds the same button from the source defaults.

## Done

Report the tokens written, the tokens still holding source defaults, the text style count (82), the button set id, the variant count, and the Figma file link. For Skip setup, say that every token, the 82 text styles, and the button set are the source defaults.
