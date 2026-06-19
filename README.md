# Unique Systems Guaranteed

A Stellaris **Galaxy Generation** mod that makes the game's unique / special star systems **always spawn** during galaxy generation, instead of appearing at random.

[Steam Workshop](https://steamcommunity.com/sharedfiles/filedetails/?id=3354855440)

## What it does

Stellaris seeds many one-off "unique" systems (base game + DLCs) behind a reduced `spawn_chance` / galaxy-size-scaled `scaled_spawn_chance`, so any given galaxy only rolls some of them. This mod forces those systems' spawn gate to **100%** (`spawn_chance = 100`), keeping `max_instances = 1`, so every system it covers is guaranteed to appear exactly once.

Coverage spans the base game and DLC system sets — Ancient Relics, Astral Planes, Distant Stars, Federations, Leviathans, The Machine Age, MegaCorp, Overlord, Paragon, Utopia, plus the pre-FTL / special / unique sets (~89 systems). It also overrides the Ancient Relics `ancrel.12050` event to force **both** special cluster systems (Ultima Vigilis + the First Contact "Chosen" cluster) to spawn — on separate rim systems so they don't crowd each other — instead of vanilla's 2:1:1 nothing / either / or roll.

## Requirements & usage

- Unique systems are **DLC-specific** — you only get a given DLC's systems if you own that DLC (overrides for DLCs you don't own are harmless no-ops).
- Start a **new galaxy** for it to take effect (galaxy generation runs at game start; existing saves won't change).
- Guaranteeing every unique system fills the map fast — a **larger galaxy** gives them room to breathe.

## Compatibility

- These files **replace** their vanilla counterparts wholesale (see *How it works*), so the mod **conflicts with any other mod that edits the same `solar_system_initializers` files or the `ancient_relics_arcsite_events_2.txt` event file**.
- Built for Stellaris **4.4** (`descriptor.mod` declares `v4.4.*`).

## How it works

The `solar_system_initializers` and `events` databases do **not** support per-key override from a separate file — the engine keeps the first (vanilla) definition and ignores a later redefinition (it logs a bare "already exists" with no "using the one at"). The only reliable way to change them is to ship a file with the **same vanilla filename**, which fully replaces vanilla's version.

So each file here is a copy of the **current** vanilla file under its original name, with `spawn_chance` forced to `100` on the guaranteed systems (converting any `scaled_spawn_chance`, which 4.4 introduced and which takes precedence over `spawn_chance`). The event file is the current vanilla `ancient_relics_arcsite_events_2.txt` with only `ancrel.12050` changed.

### Updating after a Stellaris patch

Because each file fully replaces vanilla's, the **whole file** goes stale on a major patch (any new/changed systems in it come from the mod's copy, not the new vanilla). After a patch, re-copy the vanilla files and re-apply `spawn_chance = 100` to the gated systems (search each file for `spawn_chance` / `scaled_spawn_chance`), and re-apply the `ancrel.12050` change to the event file.
