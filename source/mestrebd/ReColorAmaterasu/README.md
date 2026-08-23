# ReColor - Amaterasu

Original work by **MestreBD**, distributed as a full patched disc image
(`Digimon World 2003 ReColor - Amaterasu.img`).

Repackaged here as a mod folder, **with MestreBD's permission**, so it can be
switched on and off from the MODS panel without swapping discs. The art is
MestreBD's; this folder only carries the differences.

## What it changes

28 sprite sheets under `FIELD/SPRT/`, and nothing else:

- the three partners and their alternate sets
- the playable Digimon: Agumon, Veemon, Guilmon, Renamon, Patamon, Kotemon,
  Kumamon, Monmon and the rest
- the Digimon Online / satellite NPCs

These are the **field** sprites, the ones you see walking around a zone. Battle
models and portraits are untouched.

Every file keeps its original size, so the changes ship as IPS patches applied
at startup and undone when the mod is switched off — the port restores the
stock files before applying whatever is enabled, so turning it off really
reverts it.

## What it does NOT change

The disc image also carries `SCREEN/TLOGOPAL.BIN`, but it is byte-for-byte the
stock file: the mod does not touch the title logo. It is deliberately left out,
because the port's own copy of that sheet carries the extra letters our menus
draw with, and overwriting it would break them.
