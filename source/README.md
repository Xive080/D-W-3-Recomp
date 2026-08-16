# Mod sources

Paste one of these addresses into the launcher — **MODS → SOURCES → + ADD
SOURCE FROM CLIPBOARD** — and its mods show up with a DOWNLOAD button, and an
UPDATE button whenever a newer version is published.

| Source | Address |
|---|---|
| markisha64's patches | `https://raw.githubusercontent.com/Xive080/D-W-3-Recomp/refs/heads/main/source/markisha64.json` |

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
