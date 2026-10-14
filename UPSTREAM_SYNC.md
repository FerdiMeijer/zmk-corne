# Upstream sync notes

## What was merged

The local `main` branch was merged with `upstream/main` from:

- Upstream: `https://github.com/a741725193/zmk-new_corne.git`
- Local commit before merge: `2df2b28` (`fix: ENTER`)
- Upstream commit merged: `904bf0d` (`Update eyelash_corne.conf`)
- Merge commit: `702f982` (`Merge upstream main`)

This was a merge, not a reset or rebase, so the local branch history and its existing commits were retained. The changes are local and have not been pushed to `origin`.

## Was the custom keyboard configuration overridden?

**No, the custom keymap was not replaced wholesale.** The merged `config/eyelash_corne.keymap` retains the local layout, layers, combos, and home-row mod bindings. In particular, F and J are still configured as:

```dts
&mt LEFT_SHIFT F
&mt RIGHT_SHIFT J
```

So the F/J hold behavior that prompted this work has not yet been changed.

Some upstream configuration *was* merged into the project:

- `config/west.yml` now uses upstream's Cormoran ZMK fork and additional modules.
- The keymap gained upstream runtime sensor-rotation behavior and updated several encoder bindings.
- The board definition was refactored from `boards/arm/eyelash_corne` to `boards/shields/eyelash_corne`.
- The build workflow and `build.yaml` were updated along with the upstream build setup.

These are meaningful build/configuration changes, so this is not an assertion that every local setting stayed byte-for-byte identical. The custom key assignments above were preserved, but the post-merge firmware still needs a build check.

## Merge conflict resolution

The merge conflicted in `README.md`; the local setup instructions were kept and the upstream DYA Studio note was retained. The upstream `README_EN.md` was also added. The keymap merged automatically.

## Follow-up to verify

There is a likely stale encoder reference in `config/eyelash_corne.keymap`: `layer_3` still has `sensor-bindings = <&scroll_encoder>;`, but no `scroll_encoder` behavior definition remains in the repository. This was not changed as part of the sync. Check/fix that and run a firmware build before flashing the keyboard.

## Git commands used

```sh
git remote add upstream https://github.com/a741725193/zmk-new_corne.git
git fetch upstream
git merge --no-edit upstream/main
```

`git merge --no-edit upstream/main` incorporates the fetched `upstream/main` history into the currently checked-out branch (here, local `main`). Because local and upstream had both advanced, Git created a merge commit, preserving both histories. `--no-edit` tells Git to use its default merge commit message without opening an editor. It does not suppress conflicts; Git stopped for README conflicts that had to be resolved manually.

After resolving `README.md` and keeping the upstream `README_EN.md`, I staged the resolutions and completed the merge:

```sh
git add README.md README_EN.md
git diff --cached --check
git commit -m "Merge upstream main"
```
