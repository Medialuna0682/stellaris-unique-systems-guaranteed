# Unique Systems Guaranteed

A Stellaris **Galaxy Generation** mod that makes the game's unique / special star systems **always spawn** during galaxy generation, instead of appearing at random.

[Steam Workshop](https://steamcommunity.com/sharedfiles/filedetails/?id=3354855440)

## What it does

Stellaris seeds many one-off "unique" systems (base game + DLCs) behind a reduced `spawn_chance` / galaxy-size-scaled `scaled_spawn_chance`, so any given galaxy only rolls some of them. This mod **redefines just those specific system initializers** and forces their spawn gate to **100%** (`spawn_chance = 100`), keeping `max_instances = 1`, so every system it covers is guaranteed to appear exactly once.

Coverage spans the base game and DLC system sets — Ancient Relics, Astral Planes, Distant Stars, Federations, Leviathans, The Machine Age, MegaCorp, Overlord, Paragon, Utopia, plus the pre-FTL / special / unique sets (~89 systems). It also includes a per-event override of the Ancient Relics `ancrel.12050` event that forces **both** special cluster systems (Ultima Vigilis + the First Contact "Chosen" cluster) to spawn, instead of vanilla's 1-in-2 roll.

## Requirements & usage

- Unique systems are **DLC-specific** — you only get a given DLC's systems if you own that DLC (overrides for DLCs you don't own are harmless no-ops).
- Start a **new galaxy** for it to take effect (galaxy generation runs at game start; existing saves won't change).
- Guaranteeing every unique system fills the map fast — a **larger galaxy** gives them room to breathe.

## Compatibility

- Uses **per-key overrides**: files named `zzz_usg_*` load after vanilla and redefine *only* the guaranteed systems / event. Everything else — including systems added by future patches/DLCs — passes through from vanilla unchanged.
- Conflicts only with other mods that redefine the **same** specific initializers or the `ancrel.12050` event.
- Built for Stellaris **4.4** (`descriptor.mod` declares `v4.4.*`).

## How it works

Each guaranteed initializer is copied from **current** vanilla with its spawn gate forced to `spawn_chance = 100` (replacing vanilla's `spawn_chance`, or its galaxy-size-scaled `scaled_spawn_chance` — which takes precedence in vanilla, so it is removed). The `zzz_` filename prefix makes these files sort after the base-game initializers, so they override by key while every other system loads from vanilla.

### Updating after a Stellaris patch

Because only the guaranteed systems are redefined, systems the mod doesn't touch need no maintenance. After a major patch, regenerate the `zzz_usg_*` files from the current vanilla blocks (re-applying `spawn_chance = 100`) so the guaranteed systems stay current.
