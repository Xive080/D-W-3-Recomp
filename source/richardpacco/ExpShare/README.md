# Exp Share

Original work by **RichardPacco** — <https://github.com/RichardPacco/DMW2003-Exp-Share>.
Ported with his permission; the routine this mod installs is his.

## What it does

The game keeps twelve flags that decide who is paid EXP when a battle ends:
three party slots by four forms each (the main one and digivolutions 1 to 3).
Normally the game turns them on and off by itself, so only some forms grow.

This mod adds an **Exp Share** row to the in-game pause menu, right under
DIGIVICE, with three settings:

| Setting | Who earns EXP |
|---|---|
| **Off** | whatever the game decides, untouched |
| **Main** | the main form of every party member |
| **All** | every member's main form and all three digivolutions |

The switch takes effect immediately — no restart, no re-patching. The row is
translated into all six languages the port ships.

## How it works

`PRO/STFGTREP.PRO` holds the battle reward code. Once loaded it sits at
`0x800858F4`, where a 0x78-byte loop builds those twelve flags. The mod
overwrites that loop, in memory, with a routine that fits in exactly the same
space:

1. walks the twelve flags at `0x80042B8A..0x80042B95` and forces the ones in a
   mask word;
2. reads the three main-form flags back to count the active leaders;
3. derives the active digivolutions as *total minus leaders*;
4. adds that to the counter the original code kept, and jumps back into the
   original logic at `0x8008596C`.

Writing code into guest RAM works because the engine compares the live bytes
against the image it compiled from before running the compiled version of any
function; when they differ it hands that function to its interpreter.

Two things differ from RichardPacco's original patcher, which bakes the choice
into the ROM ahead of time:

- **the mask is a word the port rewrites**, which is what makes the setting
  live rather than a pre-game decision;
- **empty party slots never earn.** The original forces all twelve flags
  blindly; here the mask is built from who is actually in the party.

## Notes

- PAL only (`SLES_039.36`), which is the build this port runs.
- It does not overlap *Uncapped Digivolution EXP*, which patches the same file
  elsewhere. Both can be on at once.
- The switch in the MODS panel decides whether the row exists at all; the row
  itself decides the setting. Same arrangement as the Digivice.
- This mod carries no `patcher.json`: it changes no game file, because its code
  ships inside the port. It needs a build from 23 August 2026 or later — on an
  older one the folder appears with a switch that does nothing.
