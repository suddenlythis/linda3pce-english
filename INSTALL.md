# Installing the Linda³ English translation (v0.3)

The download contains only the changes to the game's data track, not the game.
You need your own disc image of **Linda3 (Japan, Rev 2)**.

## What you need

- A disc image of Linda3 (Japan) (Rev 2) as one `.cue` and 28 track `.bin` files.
- Track 02 of that image (the data track) must be exactly:

  | | |
  |---|---|
  | Size | 212,830,128 bytes |
  | SHA-1 | `3296a4db58a92a60dfbd35fc99a8c1943db995e1` |

  With any other Track 02 the patch refuses to apply.
- xdelta3, or a front end for it such as Delta Patcher or xdelta UI.
- A PC Engine CD emulator with a Super System Card (version 3.0).

## What is in the zip

| File | What it is |
|---|---|
| `Linda3-EN-v0.3.xdelta` | The patch (Track 02 only) |
| `Linda3 EN.cue` | Optional cue sheet, only for the side-by-side alternative below. Most people do not need it |
| `README.txt` | The release notes |

## How to apply

Patch your Track 02 file with `Linda3-EN-v0.3.xdelta`. Keep its file name, and
open your usual `.cue`. That is all.

### With Delta Patcher

1. **Original file** = your `... (Track 02).bin`
2. **XDelta patch** = `Linda3-EN-v0.3.xdelta`
3. Tick **Backup original file** in the settings, then **Apply patch**.

### With the command line

xdelta3 writes a new file, so rename the original first:

```
ren "Linda^3 (Japan) (Rev 2) (Track 02).bin" "Track 02 original.bin"
xdelta3 -d -s "Track 02 original.bin" Linda3-EN-v0.3.xdelta "Linda^3 (Japan) (Rev 2) (Track 02).bin"
```

### Check the result

The patched Track 02 has SHA-1:

```
86abb01a2dd40a48d19e7293575468ce1170887e
```

## Alternative: keep the Japanese and English discs side by side

Leave your Track 02 alone, save the patched file as `Linda3 EN (Track 02).bin`
in the same folder, and open `Linda3 EN.cue` from the zip. That cue lists your
original track files plus the patched Track 02. If your files are named
differently, edit the names in it.

## After patching

Start a new game or boot fresh. A save state made on the Japanese game or on an
older version of the patch keeps showing the old text until the game loads that
area again. In-game saves are not affected.

## Tested on

Mainly Mednafen 1.32.1. Also started and played briefly on RetroArch with the
Beetle PCE core. Not tested on other emulators or on real hardware.
