# Deadlock Profile

Status is reference.
Steam app id is `1422450`.
This profile covers spec version 1.

## Game files

Game files live under `.../common/Deadlock/game`.
Decompile targets from `citadel/pak01_dir.vpk`.
If a raw file is absent there, read `core/pak01_dir.vpk` next.
Read the game build id from `citadel/steam.inf` keys `VersionDate` and `VersionTime`.

## Suffix map

The map has three rows.

| Cleartext suffix | Compiled suffix |
| --- | --- |
| `.css` | `.vcss_c` |
| `.xml` | `.vxml_c` |
| `.js` | `.vjs_c` |

Raw suffixes are `.cfg`.

## Decompile

Decompile with Source2Viewer-CLI in decompile mode.
Pin the decompiler per spec rule 11.
Make the output folder first.
If the folder exists, the file lands at its VPK path with the cleartext suffix.
If the folder is absent and `-f` matches one file, Source2Viewer-CLI writes that file to the `-o` path.
One call takes many paths in `-f`, separated by commas.

```sh
mkdir -p /tmp/fresh
Source2Viewer-CLI -i citadel/pak01_dir.vpk -d -o /tmp/fresh -f panorama/styles/hud.vcss_c
# writes /tmp/fresh/panorama/styles/hud.css
```

Extract raw files with no `-d`.

```sh
Source2Viewer-CLI -i citadel/pak01_dir.vpk -o /tmp/fresh -f panorama/citadel_keybinds.cfg
```

## Compile

Compile with `resourcecompiler.exe` from `game/bin_cs2/win64` in the CSDK.
The other binary folders (`bin`, `bin_server`, `bin_tools`) fail the schema check.
Set up a mod root with these paths.

| Path | Content |
| --- | --- |
| `game/citadel/gameinfo.gi` | A writable copy from the game. |
| `game/citadel/bin` | A link to `game/citadel/bin` in the CSDK. |
| `game/core/panorama/panorama_config.txt` | A copy from the CSDK, not from a VPK. |
| `content/citadel_addons/<addon>/<target>` | The cleartext input. |

Run the compiler with the cwd in `game`.
The output lands at `game/citadel_addons/<addon>/<compiled path>`.
Example VPK name: `pak75_dir.vpk`.

```sh
cd modroot/game
resourcecompiler.exe -v -f -game "C:\modroot\game\citadel" "C:\modroot\content\citadel_addons\badge\panorama\layout\hud.xml"
```

On Linux, run the compiler under Wine with `Z:\` paths.
It needs the DXVK `d3d11.dll` and `dxgi.dll` in the Wine prefix.
It runs headless with llvmpipe.
Nix package for it is available via `nix build github:rszyma/deadlock-modbox#deadlock-resourcecompiler`.

## Reference implementation

Modbox is the reference implementation for this profile.
Its repo lives at https://github.com/rszyma/deadlock-modbox.
