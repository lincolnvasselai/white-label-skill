# Brand slots

The wizard writes here. Everything else stays on the template in [structure.md](structure.md).

## Colors

A single hex updates the base step only. Lighter and darker steps stay until the user pastes them.

| Order | Role in the file | Base token | Semantic tokens that follow it |
| --- | --- | --- | --- |
| Primary | Accent | `color/blue/500` | `text/accent`, `icon/accent` |
| Secondary | Links | `color/azure/500` | `text/link` |
| Tertiary | Visited link | `color/purple/purple-500` | `text/link-visited` |

Related steps that do **not** move when only the base hex is set:

- `text/link-hover` → `color/azure/300`
- `text/info`, `icon/info` → `color/azure/400`
- `icon/info` Dark mode → `color/gray/000` (source file value)

Say this in the plan. If they want hover and info to follow the secondary color, they supply those steps.

With 1 color, write primary only. With 2, primary and secondary. With 3, all three rows. Extra colors beyond three need a new Core ramp and an explicit semantic token; ask before creating either.

Feedback ramps (`red`, `green`, `orange`) and `gray` are shared. Leave them unless the user says that brand replaces them.

## Fonts

| Answer | Token | Effect |
| --- | --- | --- |
| Primary family | `typography/font-family/primary` | Every text style, because the ramp aliases this token |
| Secondary family | `typography/font-family/secondary` | Stored. No style uses it until the user assigns one |
| Tertiary family | `typography/font-family/tertiary` | Create only when they have 3 or more families. Ramp stays on primary |
| Regular style name | `typography/font-weight/regular` | Styles whose path contains `/regular/` |
| Bold style name | `typography/font-weight/bold` | Styles whose path contains `/bold/` |
| Medium style name | `typography/font-weight/medium` | No style uses it today |

With 1 font, set primary and set secondary to the same family so the placeholder `String value` is gone.

## What the plan must show

For each written token: name, new value, and the aliases that resolve through it.

For each skipped step: the token name and that it stays on the template.
