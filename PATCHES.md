# KaRRi Fork Patch Workflow

This is a fork of [molaupi/karri](https://github.com/molaupi/karri) maintained by [noobtimize](https://github.com/noobtimize) for custom performance optimizations.

## Branch Strategy

- `main` — tracks upstream `molaupi/karri:main` (read-only mirror)
- `noobtimize-patches` — our customization branch with performance patches

## Remotes

```
origin   → https://github.com/noobtimize/karri.git
upstream → https://github.com/molaupi/karri.git
```

## Merge-Upstream Workflow

```bash
# Inside external/karri on noobtimize-patches branch
git fetch upstream
git merge upstream/main        # or upstream/<tag> for a specific release

# Resolve conflicts, rebuild, test
make -C ../../ build test

# Push updated patch branch
git push origin noobtimize-patches

# Back in parent repo: commit the updated submodule pointer
cd ../..
git add external/karri
git commit -m "chore: sync karri fork with upstream <version>"
```
