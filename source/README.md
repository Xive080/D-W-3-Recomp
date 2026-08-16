# Mod sources

Paste one of these addresses into the launcher — **MODS → SOURCES → + ADD
SOURCE FROM CLIPBOARD** — and its mods show up with a DOWNLOAD button, and an
UPDATE button whenever a newer version is published.

**One source per author.** Whose a mod is and where its file happens to sit are
two different questions, and only the first one belongs in a source's name.

| Source | Whose | Address |
|---|---|---|
| Xive080 | Xive080 | `…/source/xive080.json` |
| markisha64 | markisha64 — 20 patches | `…/source/markisha64.json` |
| Flawe | Flawe — Fast Travel | `…/source/flawe.json` |

Full addresses start with
`https://raw.githubusercontent.com/Xive080/D-W-3-Recomp/refs/heads/main/`.

---

## xive080.json

Xive080's own mods. These files **are** hosted here, under `source/xive080/`.

| Mod | What it is |
|---|---|
| **Time Stranger UI** | An 8-bit reskin of the game's interface |

### One source per author, on purpose

This repository publishes what belongs to it. It briefly also carried **DigiLab**
(JulioGawl's) and **DigiRandom** (a port of markisha64's randomizer, MIT), and
they were taken back out: hosting someone else's work under this name reads like
a claim on it, however the rows are labelled.

Those two are launcher tabs that ship with the port itself, so a player already
has them — they don't need a source to arrive. When they do get one, it will be
their author's, or a separate one that carries their name and not this one.

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

## flawe.json

**Fast Travel**, by **Flawe**. One patch.

Its file lives inside markisha64's patcher repository — it is a plain folder
there rather than a submodule — so that is where the source points. That is a
fact about where the file sits, not about whose patch it is, which is why it
gets its own source instead of riding along in markisha64's.

---

## markisha64.json

A mirror of the 20 patches from [markisha64/dmw_2003_patcher][p] that are
**his** (MIT). Fast Travel is listed separately above, as Flawe's.

It **re-hosts nothing** — every file is fetched from markisha64's own
repositories, pinned to an exact commit. This file is only the index.

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
