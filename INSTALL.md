# Installing the Linda³ English translation (v1.1)

The download contains only the changes to the game's data track, not the game.
You need your own disc image of **Linda3 (Japan, Rev 2)**.

## What you need

- A disc image of Linda3 (Japan) (Rev 2) as one `.cue` and 28 track `.bin` files.
- Track 02 of that image (the data track) must be exactly:

  | | |
  |---|---|
  | Size | 212,830,128 bytes |
  | SHA-1 | `3296a4db58a92a60dfbd35fc99a8c1943db995e1` |

  With any other Track 02 the patch refuses to apply. That includes a Track 02
  already patched with v0.3 or v1.0: patch the original Japanese track.
- xdelta3, or a front end for it such as Delta Patcher or xdelta UI.
- A PC Engine CD emulator with a Super System Card (version 3.0).

## What is in the zip

| File | What it is |
|---|---|
| `Linda3-EN-v1.1.xdelta` | The patch (Track 02 only) |
| `Linda3 EN.cue` | Optional cue sheet, only for the side-by-side alternative below. Most people do not need it |
| `README.txt` | The release notes |

## Back up existing saves first

If you have a game in progress, copy your save files first. In-game saves carry
over (see "After patching"), but a copy costs nothing. They are in your
emulator's save folder (for Mednafen, the `sav` folder).

## How to apply

Patch your Track 02 file with `Linda3-EN-v1.1.xdelta`. Keep its file name, and
open your usual `.cue`. That is all.

### With Delta Patcher

1. **Original file** = your `... (Track 02).bin`
2. **XDelta patch** = `Linda3-EN-v1.1.xdelta`
3. Tick **Backup original file** in the settings, then **Apply patch**.

### With the command line

xdelta3 writes a new file, so rename the original first:

```
ren "Linda^3 (Japan) (Rev 2) (Track 02).bin" "Track 02 original.bin"
xdelta3 -d -s "Track 02 original.bin" Linda3-EN-v1.1.xdelta "Linda^3 (Japan) (Rev 2) (Track 02).bin"
```

### Check the result

The patched Track 02 has SHA-1:

```
c544e127c3ffac339a4dc0a194214cd8126ed856
```

## Alternative: keep the Japanese and English discs side by side

Leave your Track 02 alone, save the patched file as `Linda3 EN (Track 02).bin`
in the same folder, and open `Linda3 EN.cue` from the zip. That cue lists your
original track files plus the patched Track 02. If your files are named
differently, edit the names in it.

## After patching

Boot fresh after patching.

**In-game saves carry over.** Saves made with the game's own save option, on
v0.3, v1.0 or the Japanese game, keep your progress and load normally in v1.1,
which then shows the new text. If you keep your usual `.cue` and its file
names, the emulator finds the save by itself.

**Emulator save states do not carry over cleanly.** A save state made on the
Japanese game or on an older version of the patch keeps showing the old text
until the game loads that area again, and one made during a cutscene can
misbehave. Continue from an in-game save instead.

## Tested on

Mainly Mednafen 1.32.1. Also started and played briefly on RetroArch with the
Beetle PCE core. Not tested on other emulators or on real hardware.
