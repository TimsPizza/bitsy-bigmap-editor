# Bitsy Bigroom Generator

Bitsy Bigroom Generator is a browser-based map tool for building oversized layouts for [Bitsy](https://make.bitsy.org/).

Instead of drawing one fixed 16x16 room at a time, you paint on a larger room-by-room canvas. The tool then converts that canvas back into standard Bitsy `ROOM` data and generates the room-to-room exits needed to make it feel like one continuous map.

## What It Does

- Imports existing Bitsy game data
- Extracts tile materials from the source data
- Rebuilds existing room maps into one larger editor canvas
- Lets you paint with imported tile textures
- Supports per-tile blocking configuration
- Lets you place the avatar start position visually
- Exports only the map section of the Bitsy file, leaving the rest of the source intact

## Current Scope

This project is focused on map authoring and room generation.

It currently handles:

- `ROOM` / `SET` map data
- `WAL` room walls
- `EXT` exits between generated rooms
- avatar start position updates

It does not yet fully remap all room-local content such as NPCs, items, or endings when the map layout changes.

## How It Works

1. Paste an existing Bitsy game data export into the import panel.
2. Parse the source to load tiles, rooms, and start position.
3. Resize the world in room units.
4. Paint the big map using imported tiles.
5. Mark tiles as blocking or passable per tile type.
6. Build the export and copy the generated Bitsy data back into your project.

## Development

```bash
npm install
npm run dev
```

Other useful commands:

```bash
npm run build
npm run lint
```

## Notes

- The editor works in Bitsy-sized room chunks, not arbitrary room dimensions.
- Exported transitions try to place the player one tile inside the destination room and avoid bad landing cells where possible.
- If imported source data uses inconsistent room-level wall behavior for the same tile, the editor normalizes that into a single per-tile blocking rule.
