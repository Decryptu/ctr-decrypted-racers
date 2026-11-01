# CTR Decrypted racers

The custom racer catalogue for [CTR Decrypted](https://github.com/Decryptu/ctr-decrypted). The game's Mods screen lists the racers in `index.json` and installs them from here. Each racer gets its own slot on the character select.

Every racer is someone else's work, credited in [CREDITS.md](CREDITS.md) and in its own `racer.json`.

## Layout
- `racers/<name>-<id>/`: one racer: `racer.json`, `model.ctr`, `portrait.bin`, and `portrait.png` to look at here. The format is in the game's [docs/CUSTOM_RACERS.md](https://github.com/Decryptu/ctr-decrypted/blob/main/docs/CUSTOM_RACERS.md).
- `index.json`: every racer, with the size and SHA-256 of its `racer.json`.
- `sources.json`: what the converter cannot read from a mod (authors, links, names some mods left unchanged).

## Adding racers
Racer mods for the PS1 disc (xdelta patches) are converted with the game repository's tools:

```sh
python tools/racers/convert_racer.py --disc "CTR (USA).bin" --sources sources.json --out racers/ path/to/mod.xdelta
python tools/racers/build_index.py .
```

Give every new mod its authors and link in `sources.json` first: `build_index.py` refuses a racer without authors. A package holds only the mod author's work, never data from the game disc.
