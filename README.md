# Unique Systems Guaranteed

A Stellaris **Galaxy Generation** mod that makes the game's unique / special star systems **always spawn** during galaxy generation, instead of appearing at random.

[Steam Workshop](https://steamcommunity.com/sharedfiles/filedetails/?id=3354855440)

## What it does

Stellaris seeds many one-off "unique" systems (base game + DLCs) with a low or random `spawn_chance`, so any given galaxy only rolls some of them. This mod overrides the vanilla `common/solar_system_initializers/` files and raises those systems' `spawn_chance` to **100** while keeping `max_instances = 1`, so every eligible unique/special system is guaranteed to appear exactly once.

Coverage spans the base game and DLC system sets:

- Ancient Relics, Astral Planes, Distant Stars, Federations, Leviathans, The Machine Age, MegaCorp, Overlord, Paragon, Utopia, plus the pre-FTL / special / unique system sets.
- Includes an override of the Ancient Relics arcsite event (`events/ancient_relics_arcsite_events_2.txt`).

## Requirements & usage

- Unique systems are **DLC-specific** — you only get a given DLC's systems if you own that DLC.
- Start a **new galaxy** for it to take effect (galaxy generation runs at game start; existing saves won't change).
- Guaranteeing every unique system fills the map fast — a **larger galaxy** gives them room to breathe.

## Compatibility

- Overrides vanilla `common/solar_system_initializers/` files by filename, so it **conflicts with any other mod that edits the same initializer files**.
- Built for Stellaris 4.x (`descriptor.mod` currently declares `v4.2.*`).

## How it works

Each unique system initializer is given `spawn_chance = 100` (via the `@unique_system_spawn_chance` variable) with `max_instances` left at 1, so the system always generates exactly once. The mod's files reuse the vanilla initializer filenames, so they load after and replace the base-game versions.
