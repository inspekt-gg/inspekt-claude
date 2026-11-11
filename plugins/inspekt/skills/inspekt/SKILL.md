---
name: inspekt
description: Builds inspekt.gg embeds and image URLs for CS2 skins with the inspekt MCP tools. Use when the user wants a CS2 skin or item on a site (the live 3D viewer or an /api/still image), has a Steam inspect link or a skin name to render, wants the items in a public Steam inventory, or hits an inspekt.gg key, origin or refusal code.
---

# inspekt.gg

## Which tool

- `embed_snippet`: the live 3D viewer for a page, as the `cs2embed.js` loader, a raw iframe or a React component.
- `render_still`: the `/api/still` URL and an `<img>` tag, for listing cards and Open Graph images. `include_image: true` also returns the picture; it needs `INSPEKT_SECRET` and counts as a render.
- `catalog_search`: the catalog id and float range of a skin named in words.
- `inventory_lookup`: the CS2 items in a public Steam inventory. Needs `INSPEKT_SECRET`.
- `docs`: every parameter, bound, refusal code, limit and plan. On a refusal, call it with topic `errors` and look up the `code`.

Without the MCP server, read https://inspekt.gg/docs/inspekt-for-agents.md.

## Naming the item

Send exactly one of `inspect` or `id`. `inspect` takes a link copied from inside CS2 or a "gen" link. Steam Market and inventory links (ending `S…A…D…` or `M…A…D…`) are refused. For those, and for a skin named in words, get the id from `catalog_search` and send it with `wear`, `seed`, `stickers`, `charm`, `stattrak` and `name`.

## Keys and origins

- The publishable key (`cs2pk_`, `INSPEKT_KEY`) belongs in page code and image URLs. If tool output carries `cs2pk_your_key_here`, tell the user to set `INSPEKT_KEY` and restart Claude Code.
- Tell the user to add each origin the page runs on, with scheme and port (`https://shop.example`, `http://localhost:3000`), under Allowed origins at https://inspekt.gg/dashboard.
- Keep `referrerpolicy="strict-origin"` on every `<img>` and hand-built `<iframe>`.
- The secret key (`cs2sk_`) goes only in a server's `x-cs2-key` header, never in page code, a client bundle or a URL. For server code, call `docs` with topic `render_api` and section `secret keys`.
