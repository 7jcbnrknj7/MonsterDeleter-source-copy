[简体中文](README.md) | [日本語](README.ja.md) | [English](README.en.md)

# 🦖 Desktop Monster Deleter

A source copy saved when the owner first started using GitHub. Original project: [531149627/MonsterDeleter](https://github.com/531149627/MonsterDeleter).

A Windows desktop application that summons a monster to walk toward a file and perform an animated kick with sound effects. Actual deletion uses `send2trash` to move the specified file to the Windows Recycle Bin, where it can be restored; it does not permanently shred files.

## Features

- A translucent targeting overlay with a red crosshair.
- Frame animations for appearing, walking, pointing, kicking, explosions, and flying away, with transparent assets.
- Background music, monster voice lines, and explosion sounds.
- First launch registers a file context-menu entry named “召唤大将怪兽摧毁” for the current Windows user.
- Receives the target path from the file context menu and lets you select the animation position on screen.

## Using a packaged executable

This repository contains source and assets, without a prebuilt `MonsterDeleter.exe`. If you obtain a packaged executable separately or build one yourself:

1. Run it once to register the context menu. Press `Esc` or close it after the targeting overlay appears.
2. Right-click the target file, select “召唤大将怪兽摧毁”, choose an animation position with the red crosshair on the dimmed screen, and follow the interface prompts.

The path passed by the context menu determines which file is recycled. Running only `python main.py` starts a manual demonstration; recycling requires a target file argument.

## Running from source

Requires Windows and Python 3. The current source imports PyQt6 and uses send2trash for recycling. There is no `requirements.txt` in this copy; install these two dependencies:

```powershell
python -m pip install PyQt6 send2trash
python main.py
python main.py "C:\path\to\your\file.txt"
```

The second line opens the manual demonstration; the third supplies a target file. Check interface, audio, and context-menu compatibility on your machine.

## Packaging reference

Install PyInstaller, then run these commands from the repository root:

```powershell
python -m pip install pyinstaller
pyinstaller --noconfirm --onefile --windowed --name MonsterDeleter --add-data "assets;assets" --hidden-import send2trash main.py
```

The output is `dist/MonsterDeleter.exe`. In single-file mode, resources are read from the extracted `sys._MEIPASS` directory. This is a packaging reference, not a claim of verification on every Windows environment.

## Repository structure

| Path | Contents |
| --- | --- |
| `main.py` | Interface, animation, audio, context-menu registration, and recycling |
| `register_menu.py` | Standalone menu registration script |
| `assets/` | Images, animation frames, and audio |

This copy does not include the `requirements.txt`, `scripts/`, or `tests/` mentioned in the previous introduction.

## Attribution and licensing

Intended for entertainment and learning. Consult the original project and each asset's permissions; this copy's description grants no additional redistribution or commercial rights.
