# Mod sources

Paste one of these addresses into the launcher — **MODS → SOURCES → + ADD
SOURCE FROM CLIPBOARD** — and its mods show up with a DOWNLOAD button, and an
UPDATE button whenever a newer version is published.

| Source | Address |
|---|---|
| Xive080 — this port's own mods | `https://raw.githubusercontent.com/Xive080/D-W-3-Recomp/refs/heads/main/source/xive080.json` |
| markisha64's patches | `https://raw.githubusercontent.com/Xive080/D-W-3-Recomp/refs/heads/main/source/markisha64.json` |

---

## xive080.json

The mods that belong to this port. Unlike the mirror below, these files **are**
hosted here, under `source/xive080/`.

| Mod | What it is | Whose idea |
|---|---|---|
| **DigiLab** | A launcher tab for editing the EXP, digivolution EXP and BITS every enemy drops | [JulioGawl][jg] |
| **DigiRandom** | A launcher tab that randomizes the game — encounters, shops, digivolutions, starting party, scaling | port of [markisha64's randomizer][rz] (MIT) |
| **Time Stranger UI** | An 8-bit reskin of the game's interface | Xive |

[jg]: #digilab
[rz]: https://github.com/markisha64/dmw3-randomizer

**DigiLab and DigiRandom add a tab to the launcher**; they change nothing in the
game by themselves. Installing one makes its tab appear, switching it off makes
it disappear. DigiRandom's runs land in `MODS/` as separate mods, one per seed,
each born switched off.

### DigiLab

From JulioGawl's *Ferramenta Digimon World 2003 — Alterar DVEXP, EXP e BITS*.
The idea and the enemy table are his; the tab is a reimplementation that edits
the loose data file instead of a disc image, always computing from the original
values so multiplying twice doesn't compound.

His tool was shared without a stated licence. If he would rather this were
removed, renamed or licensed differently, that is his call.

### DigiRandom

A port of markisha64's randomizer, MIT. Same options, same algorithm, same seed
→ same run. The only difference is where it applies: his tool rebuilds the disc
image, this one writes a mod, so a run can be switched off and kept.

His repository's `LICENSE.md` carries GitHub's template copyright line unedited,
so it is linked rather than copied — putting *"Copyright GitHub Inc."* on his
work inside our folder would be worse than leaving it out.

---

## markisha64.json

A mirror of the 21 patches from [markisha64/dmw_2003_patcher][p] (MIT). It
**re-hosts nothing** — every file is fetched from markisha64's own repositories,
pinned to an exact commit. This file is only the index.

[p]: https://github.com/markisha64/dmw_2003_patcher

His patches need no changes to work here: the port reads his `patcher.json` /
`patch.json` as they are.

### Why we host the index and he doesn't

Only because nobody had written it yet. He has been sent a kit — the file, the
generator and a GitHub Action — so he can publish it himself under his own name
whenever he likes. When that happens, this mirror goes away and the address
becomes his.

### One patch is deliberately missing

`dmw_2003_japanese` sets the game to Japanese by skipping the language select.
This port already ships every language and picks them in SETTINGS, so offering
it would mean two ways to do the same thing, one of them worse. Nothing is
wrong with the patch.

### Keeping it current

Regenerated with `Development/Tools/hacer_repo_github.py` in the port's tree.
The URLs are pinned to a commit because the launcher checks each file's sha256
before writing it — pointing at a branch would break installs the moment an
author pushes. The trade-off is that this file has to be regenerated after they
publish; patches that changed are reported when it runs.

`Development/Tools/repo_github_estado.json` records which commit maps to which
version number, and that is what makes UPDATE appear. It travels with the
project on purpose.
