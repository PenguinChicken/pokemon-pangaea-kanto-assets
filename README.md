# Pokémon World Expansion — Stage 3

A browser-based Pokémon fan game prototype built with plain HTML, CSS, and JavaScript.

## ▶ Play online

Once deployed, the game is live at:  
**`https://<your-username>.github.io/<repo-name>/`**

---

## Deploying to GitHub Pages

### First time setup

1. Push this repository to GitHub (see "Uploading to GitHub" below).
2. Go to your repository on GitHub.
3. Click **Settings → Pages**.
4. Under **Source**, choose **GitHub Actions**.
5. Push any commit — the `deploy.yml` workflow runs automatically and publishes the site.
6. After ~1 minute, your game is live at `https://<your-username>.github.io/<repo-name>/`.

### Uploading to GitHub (if you haven't yet)

**Option A — GitHub website (easiest)**
1. Go to [github.com](https://github.com) and log in.
2. Click **+** → **New repository**.
3. Name it (e.g. `pokemon-world-expansion`), set it **Public**, click **Create repository**.
4. On the next screen click **uploading an existing file**.
5. Drag the entire contents of this ZIP into the upload area.
6. Click **Commit changes**.
7. Follow the Pages setup steps above.

**Option B — Git command line**
```bash
git init
git add .
git commit -m "Stage 3 initial commit"
git branch -M main
git remote add origin https://github.com/<your-username>/<repo-name>.git
git push -u origin main
```

---

## Project structure

```
index.html                  — Main game page
styles.css                  — All styles
.nojekyll                   — Tells GitHub Pages to serve files as-is
.github/workflows/
  deploy.yml                — Auto-deploys to GitHub Pages on every push to main
js/
  maps.js                   — Full Kanto map data
  assetLoader.js            — Sprite/tileset loading (auto-loads from assets/)
  dialogue.js               — Dialogue box
  npcs.js                   — NPC rendering and interaction
  transitions.js            — Map transitions with fade
  saveSystem.js             — IndexedDB saving
  mapEditor.js              — In-game tile editor
  game.js                   — Main loop
assets/
  player_sprite.png         — Player walking sprite sheet (48×128px, 3×4 frames)
  npc_sprites.png           — 8 NPC characters (128×32px)
  tileset.png               — 14 terrain tiles (224×16px)
  pokemon_strip.png         — First 20 Pokémon sprites
  registry.json             — Full sprite registry (1,150 sprites)
  catalogue.json            — Asset catalogue with dimensions and notes
  characters/               — 881 individual character sprites (16×24px each)
  pokemon/                  — 116 Pokémon sprites (16×24px each)
  misc/                     — 153 miscellaneous sprites (16×24px each)
```

---

## Controls

| Key | Action |
|-----|--------|
| W / Arrow Up | Move up |
| A / Arrow Left | Move left |
| S / Arrow Down | Move down |
| D / Arrow Right | Move right |
| Space / Enter | Interact / Advance dialogue |

---

## Map editor

1. Toggle **Edit mode** in the right panel.
2. Select a map from the dropdown.
3. Click a tile in the palette.
4. Click or drag on the game canvas to paint.
5. **Export map JSON** to download your edits.
6. **Import JSON** to reload a saved map.

---

## Uploading custom sprites

The game auto-loads `assets/player_sprite.png` and `assets/tileset.png` on startup.  
To replace them permanently, overwrite those files and push to GitHub.  
To replace them temporarily in-browser, use the upload buttons in the right panel.

### Player sprite format
- PNG, 3 columns × 4 rows, each frame **16×32 px**
- Row order: Down, Left, Right, Up
- Column order: Walk frame 1, Idle, Walk frame 2

### Tileset format
- PNG, 16×16 tiles left-to-right
- Order: Grass, Path, Tree, Water, Flowers, Wall, Door, Floor, Counter, Tall Grass, Rock, Ledge, Sign, Stairs

---

## Adding assets from the library

The `assets/characters/` folder contains **881** individual 16×24 character sprites.  
Reference any by index in map NPC data:

```js
// In maps.js, give an NPC a spriteIndex to pick their sprite
{ id: 'viridian_npc1', x: 10, y: 8, dir: 'down', name: 'Trainer',
  message: 'Hello!', spriteIndex: 5 }
//                                  ^^^^^^^^^^^^^ picks char_0005.png (via npc_sprites strip)
```

---

## Kanto coverage

**Towns:** Pallet, Viridian, Pewter, Cerulean, Vermilion, Lavender, Celadon, Saffron, Fuchsia, Cinnabar  
**Routes:** 1–25 (all 25)  
**Special areas:** Viridian Forest, Mt. Moon, Rock Tunnel, Diglett's Cave, Pokémon Tower, Seafoam Islands, Pokémon Mansion, Safari Zone, Victory Road  
**Interiors:** 40 buildings (House, Mart, Center, Gym per town)
