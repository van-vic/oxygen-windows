**2. `oxygen-windows` → `README.md`:**

```md
# oxygen-windows

Windows packaging for Oxygen — build scripts, mozconfig and installer for the Oxygen Browser.

Based on `oxygen` core (consumed as submodule). Heavily inspired by `helium-windows` / `ungoogled-chromium-windows`.

## Requirements

- Windows 10/11 x64, 32GB+ RAM, 60GB+ free
- VS2022 + MozillaBuild + Python 3 + Rust (via `mach bootstrap`)
- Short paths (`C:\o` recommended — `mozmake` fails over ~224 chars)

## Build

```cmd
git clone --recurse-submodules https://github.com/oxygen-browser/oxygen-windows.git
cd oxygen-windows
git checkout --recurse-submodules TAG_OR_BRANCH_HERE
python oxygen\scripts\sync.py --apply --src build\src
set MOZCONFIG=%CD%\oxygen\mozconfig.windows
python oxygen\scripts\build.py --src build\src
python package.py
