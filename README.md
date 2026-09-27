# oxygen-windows

Windows packaging for Oxygen — build scripts, mozconfig and installer for the Oxygen Browser (Firefox soft-fork by patch-stack).

Consumes [oxygen](https://github.com/oxygen-browser/oxygen) core as submodule. Inspired by `helium-windows` / `ungoogled-chromium-windows`.

## Requirements

- Windows 10/11 x64, 32 GB+ RAM, 60 GB+ free
- Visual Studio 2022, MozillaBuild, Python 3, Rust (via `mach bootstrap`)
- Use short paths: `C:\o` recommended. `mozmake` fails with absolute paths >= ~224 chars (`No rule to make target` ghost in xul link).

## Quick start

```cmd
git clone --recurse-submodules https://github.com/oxygen-browser/oxygen-windows.git
cd oxygen-windows
git checkout --recurse-submodules TAG_HERE
python oxygen\scripts\sync.py --apply --src build\src
set MOZCONFIG=%CD%\mozconfig.windows
python build.py --src build\src
python package.py
