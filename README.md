# White label skill

Setup wizard for the [White Label Design System](https://www.figma.com/design/bodT19MTa9LqB0qFgjYWK6/White-Label-%7C-Design-System) variable structure.

The skill lives in `.cursor/skills/white-label-setup`. Open this repo in Cursor and ask to set up a new brand. The first choice is Full setup or Skip setup. Full setup asks for colors, then fonts. Skip setup builds the source defaults and asks nothing else. The file keeps the source name.

The source file is the White Label Design System. One Figma file per brand. `color/blue` is the shade template and stays on its source hexes. `color/primary` is the brand ramp. The source default copies each blue step, and a new primary replaces `color/primary` only. Secondary and tertiary brand colors are new ramps with the same steps. Azure stays links and info, purple stays the visited link, green stays success, orange stays warning, and red stays danger. After the variables, the setup creates 82 text styles and a button bound to the Components collection. Collection names, modes, and semantic token names stay as they are in the source file. Unchanged tokens keep the source defaults.

## Share with the team

Clone this repo and open it in Cursor. The skill is available in this project.
