# Zeal macOS Builds

Automated builds of [Zeal](https://github.com/zealdocs/zeal) for macOS.

## Downloads

Check the [Releases](../../releases) page for downloadable `.zip` files containing `Zeal.app`.

## How it works

- A GitHub Action runs daily to check for new upstream releases
- When a new version is detected, it automatically builds the app and creates a release
- Each release contains a `Zeal-<version>.zip` file with the app bundle

## Manual build

You can also build locally using the provided script:

```bash
./build
```

Options:
- `--force` - Build even if local source appears current
- `--check-only` - Only check versions, don't build
- `--repo-dir PATH` - Override repo location
- `--app-dest PATH` - Override app install destination

## macOS Compilation Fix

A patch is included to fix a compilation error in `QxtGlobalShortcut` on macOS. Apply it in GitHub Actions after cloning:

```yaml
- name: Apply macOS compilation fix
  run: |
    cd zeal-src
    git apply ../qxtglobalshortcut-macos-fix.patch
```

## Requirements

- macOS 11.0 or later
- Apple Silicon (M1/M2/M3/M4/M5) or Intel Mac