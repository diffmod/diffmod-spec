# DiffMod Spec

## What is this

A repository for DiffMod, a community-made standard for Source2 engine based games,
in particular Deadlock, to make modding and using mods more reliable.

## Motivation

UI mods for Deadlock break all the time.
Two mods clash, or a game update breaks one of them.
This annoyed me so much that I made [Modbox](https://github.com/rszyma/deadlock-modbox),
which solved this for a few selected mods, by building them from `.patch` files.
But I cannot keep re-making other people's mods as `.patch` files by myself.
The fix must come from mod makers and mod managers, through one shared standard.
This repository contains the technical solution in form of a spec document.
You can read the spec text [here](./spec/), or [on the website](https://diffmod.github.io/diffmod-spec/).

## Contribute

DiffMod is a community project, and everyone is welcome to help:
mod makers, mod manager makers and players.
See [CONTRIBUTING.md](CONTRIBUTING.md) to get started.

## Community adoption

Adoption is in-progress.
If you know a project that uses DiffMod, please file a Pull Request adding it to the list below!

**Mod managers**:

- *none yet*

**DiffMod compilers / build tools**:

- [modbox](https://github.com/rszyma/deadlock-modbox) - reference implementation, supports Windows and Linux.

**Mods**:

- Mods with `diffmod` tag on Gamebanana, [list](https://gamebanana.com/search?_sSearchString=diffmod)
- ~10 mods in [modbox](https://github.com/rszyma/deadlock-modbox/tree/main/mods) repository

## License

Copyright (c) 2026 DiffMod spec contributors.

Text is under [CC BY 4.0](LICENSE):
the spec, the profiles, the decompiler registry and the site text.
Code is under the [MIT License](LICENSE-MIT):
the commands and examples in the text, and the site styles and scripts.
If you copy a part of the text into source code, that part is under the MIT License.
