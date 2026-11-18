# Source 2 DiffMod Spec

A DiffMod holds plain diffs over decompiled sources.

This repo holds the Source 2 DiffMod spec and game profiles.
Spec text is canonical in `spec/`.
The site mirrors the spec for reads.

## Motivation

UI mods for Deadlock break all the time.
Two mods clash, or a game update breaks one of them.
This annoyed me so much that I made [Modbox](https://github.com/rszyma/deadlock-modbox),
which builds mods from `.patch` files.
But I cannot keep re-making other people's mods as `.patch` files by myself.
The fix must come from mod makers and mod managers, through one shared standard.
Before you is a technical solution, and the only unsolved part is community adoption.

## Contribute

DiffMod is a community project, and everyone is welcome to help:
mod makers, mod manager makers and players.
Questions, ideas and small fixes all count.
Start with [CONTRIBUTING.md](CONTRIBUTING.md).

## Reference implementation

Modbox is the reference implementation.
It lives at https://github.com/rszyma/deadlock-modbox.
Its mods hold example DiffMods.

## Edit

If you change the spec, add a changelog line.
Never edit a frozen version.
Freeze each release with a tag such as `v1`.

## Serve

Deploy `site/` to `source2-diffmod.org`.
The spec page lives at `/spec`.
Pages deploys `site/` on push to `main`.

## License

Copyright (c) 2026 DiffMod spec contributors.

Text is under [CC BY 4.0](LICENSE):
the spec, the profiles, the decompiler registry and the site text.
Code is under the [MIT License](LICENSE-MIT):
the commands and examples in the text, and the site styles and scripts.
If you copy a part of the text into source code, that part is under the MIT License.
