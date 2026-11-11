# inspekt-claude

Claude Code plugin marketplace for [inspekt.gg](https://inspekt.gg). Its one plugin, `inspekt`, adds the inspekt skill and the [@inspekt-gg/mcp](https://github.com/inspekt-gg/inspekt-mcp) server.

## Install

Node 18+.

1. Sign in at [inspekt.gg/dashboard](https://inspekt.gg/dashboard), start the free 10-day trial and copy the publishable key (`cs2pk_`). Add the origin of each page that loads a still or an embed under Allowed origins.
2. Set the key before you start Claude Code:

   ```
   export INSPEKT_KEY=cs2pk_your_key_here
   ```

   PowerShell: `$env:INSPEKT_KEY = "cs2pk_your_key_here"`. For `inventory_lookup` and `include_image`, set the secret key (`cs2sk_`) as `INSPEKT_SECRET` the same way.
3. Install the plugin:

   ```
   /plugin marketplace add inspekt-gg/inspekt-claude
   /plugin install inspekt@inspekt
   ```

Then ask Claude:

> Embed steam://rungame/730/76561202255233023/+csgo_econ_action_preview 001807209A0228043004388F85D7F30340950512E67D72 in my page as a 3D viewer.

## Tools

| Tool | Returns | Key |
| --- | --- | --- |
| `render_still` | The `/api/still` URL and `<img>` tag for one item. `include_image` adds the picture. | `INSPEKT_KEY`, and `INSPEKT_SECRET` for `include_image` |
| `embed_snippet` | A `cs2embed.js` snippet, a raw iframe or a React component. | `INSPEKT_KEY` |
| `catalog_search` | Catalog ids and float ranges by name and weapon. | none |
| `inventory_lookup` | The CS2 items in a public Steam inventory. | `INSPEKT_SECRET` |
| `docs` | A section of the [agent pack](https://inspekt.gg/docs/inspekt-for-agents.md). | none |

MIT. Copyright (c) 2026 Inspekt.
