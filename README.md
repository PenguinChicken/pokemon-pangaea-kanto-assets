# Pokémon World Expansion — Asset Library

This repository stores all custom game assets for Pokémon World Expansion.

The game code loads these assets directly using raw GitHub URLs — no build step needed.

## Usage in the game

In `js/assetLoader.js`, set the base URL to point to this repo:

```js
const ASSET_BASE = 'https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_REPO/main';
```

Then assets are referenced as:
- `${ASSET_BASE}/assets/player_sprite.png`
- `${ASSET_BASE}/assets/tileset.png`
- `${ASSET_BASE}/assets/npc_sprites.png`
- `${ASSET_BASE}/assets/characters/char_0000.png`

## Contents

```
assets/
  player_sprite.png     — Player walking sprite sheet (48×128px, 3×4 frames)
  npc_sprites.png       — 8 NPC character sprites (128×32px)
  tileset.png           — 14 terrain tiles (224×16px)
  pokemon_strip.png     — First 20 Pokémon sprites
  registry.json         — Full sprite registry (1,150 sprites with metadata)
  catalogue.json        — Asset catalogue
  characters/           — 881 individual character sprites (16×24px each)
  pokemon/              — 116 Pokémon sprites (16×24px each)
  misc/                 — 153 miscellaneous sprites (16×24px each)
```

## Updating assets

Push new or replacement PNGs to this repo — the game picks them up on the next reload.
