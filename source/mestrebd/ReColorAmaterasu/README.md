# ReColor - Amaterasu

Original work by **MestreBD**, distributed as a full patched disc image
(`Digimon World 2003 ReColor - Amaterasu.img`).

Repackaged here as a mod folder, **with MestreBD's permission**, so it can be
switched on and off from the MODS panel without swapping discs. The art is
MestreBD's; this folder only carries the differences.

## What it changes

Colours only, across 28 sprite sheets under `FIELD/SPRT/`:

- the three main characters: **Junior, Ivy and Teddy**
- the **eight playable Digimon**
- the two support Digimon, **Submarimon and Digmon**

Nothing else is touched: no stats, no text, no layouts.

Every file keeps its original size, so the changes ship as IPS patches applied
at startup and undone when the mod is switched off — the port restores the
stock files before applying whatever is enabled, so turning it off really
reverts it.

## One of a pack

This is one edition of MestreBD's **Recolor Pack**. Every edition recolours the
same sprite sheets, so they declare `grupo = recolor` in their mod.ini: turning
one on turns the others off, and you never end up with two half-applied on top
of each other.

## What it does NOT change

The disc image also carries `SCREEN/TLOGOPAL.BIN`, but it is byte-for-byte the
stock file: the mod does not touch the title logo. It is deliberately left out,
because the port's own copy of that sheet carries the extra letters our menus
draw with, and overwriting it would break them.
