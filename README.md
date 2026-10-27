# LMOxide content

The game data of [LMOxide](https://github.com/LMOxide/lmoxide), the LEGO Minifigures Online
server revival: worlds and everything placed in them, NPCs and enemies, objects, skills, buffs and
upgrades, loot tables, items, minifigures, dialogues and achievements. One record per file (a
world's records one file per section), plain JSON in a canonical form, so every change is a
readable diff. The server loads this tree as it is; nothing here is generated at build time.

The format, the kinds of records and what each field means: `docs/CONTENT.md` in the lmoxide
repository, and the JSON Schemas in `schemas/` (editors such as VS Code validate against them).

## Contributing

- **The world editor** (lmoxide-dev-ui): place, edit and remove things in game; what an admin
  approves is committed here by the server, authored as the editor, with an `Approved-By:` line.
- **Pull requests**: edit the files, then run the checks below; a reviewer merges.

Every record says where its values came from (`source`: `client`, `live`, `demo`, `footage`,
`server`, `proposed`, `surveyed`, `guess`) and can carry `tags` (`todo`, `approximate`,
`verified`, ...) and a `comment`. Recreating live is the `live` feature; new content goes in
`feature/...` (events, new areas), fixes and experiments in `other/...`.

## Checks

From an lmoxide checkout with this repository at `content/`:

```sh
cargo run -p lmoxide-content -- check --warnings   # references, field names, client ids
cargo run -p lmoxide-content -- fmt --check        # canonical form (fmt without --check rewrites)
```

## Commits made by the server

```
Isle of Yarr: 3 spawns moved, 1 added (feature live)

Content-Author: <editor> <<editor>@users.noreply.lmoxide>
Approved-By: <admin>
Lmoxide-Change: <approval number>
```

## License

Not decided yet. Until it is, please don't contribute: contributions made before a license is
chosen are hard to license afterwards.
