# Farmer's Delight - CraftEngine port (Paper 26.1.x)

A server-side port of [Farmer's Delight](https://github.com/vectorwing/FarmersDelight) (Minecraft 1.21.1
mod by vectorwing) to **vanilla-client Paper servers**, using [CraftEngine](https://modrinth.com/plugin/craftengine)
for the items/blocks/recipes/resource pack and a small companion plugin
(`FarmersDelightMechanics`) for the gameplay mechanics. Players join with a **vanilla client** - no mods
required, only the auto-sent resource pack.

## Requirements

- **Paper 26.1.x** (tested on 26.1.2)
- **CraftEngine 26.5.3** (Paper build) installed in `plugins/`
- **Java 25**

## What's included

```
plugins/
├── FarmersDelightMechanics-0.1.0.jar          # companion plugin (mechanics)
└── CraftEngine/resources/farmersdelight/       # CraftEngine content pack
    ├── configuration/                          # items, blocks, crops, recipes, worldgen
    ├── resourcepack/                           # textures, models, sounds, lang
    └── pack.yml
```

## Installation

1. Install **CraftEngine** in your server's `plugins/` (it's a hard dependency).
2. Copy the contents of this repo's `plugins/` into your server's `plugins/`
   (merges into `plugins/CraftEngine/resources/`).
3. Set up resource-pack hosting in `plugins/CraftEngine/config.yml`
   (`resource-pack.delivery.hosting`). Two options:
   - **`self`** (recommended): CraftEngine generates, serves and signs the pack itself.
     ```yaml
     hosting:
       - type: self
         ip: "YOUR_SERVER_IP"
         port: 8163
         protocol: http
         one_time_token: true
     ```
     Open that port in your firewall.
   - **`external`**: host the generated zip yourself and point `url:` to it.
4. Start the server, then run **`ce reload all`** in the console to generate the resource pack
   (a plain `ce reload` does **not** rebuild the zip). Players get the pack on join.

## Features

- **Cooking pot** - 9-slot GUI, heat from fire/lava/campfire or the FD stove; container + output.
- **Cutting board** - right-click to place, cut with the correct tool.
- **Skillet & stove** - cook raw food directly (vanilla + FD meats/fish); the lit stove
  crackles like a furnace and burns you if you step on it.
- **Crops** (cabbage, tomato, onion, rice) - **right-click harvest with an empty hand**:
  drops produce + seeds and the plant regrows, no seed consumed.
- **Wild crops / foraging** - wild cabbages/tomatoes/onions/etc. generate by biome and drop
  **seeds** when foraged (in survival). The only source of `cabbage_seeds`.
- **Village loot** - FD items appear in village chests, themed by profession (farmer → seeds,
  butcher → meats, fisher → fish, smith → knives…). Works with vanilla and Towns & Towers villages.
- **Food effects, drinks, feasts & pies, cabinets, baskets, knives, dog/horse feed, safety net, rope.**

See the [Farmer's Delight wiki](https://github.com/vectorwing/FarmersDelight/wiki) for the original mechanics.
Some mod features are partial or not ported (held skillet, fortune on cutting boards, villager trades,
mushroom colonies growth) - contributions welcome.

## Credits

- Original mod: **Farmer's Delight** by [vectorwing](https://github.com/vectorwing/FarmersDelight) (MIT).
- Port: items/blocks/recipes via CraftEngine + `FarmersDelightMechanics` companion plugin.
