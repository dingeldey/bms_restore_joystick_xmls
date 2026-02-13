# restore_joystick_xmls

A small Python utility to protect and automatically restore **Falcon BMS** and **DCS** joystick bindings when Windows changes USB device GUIDs.

The tool creates timestamped backups and restores known-good controller bindings by copying binding *content* into newly generated files while keeping their new filenames and GUIDs intact.

---

## Why do we need this?

Windows sometimes reassigns USB device IDs (GUIDs), causing Falcon BMS and DCS to generate new controller config files and ignore your existing bindings.

This tool:
- Detects matching controller configs by **name (without GUID)**
- Copies the **content** from your backups into the new files
- Keeps the **new filename + GUID intact**
- Prevents hours of re-binding controls

---

## Important: create backups first

This tool **does not invent bindings** — it can only restore what you have already saved.

Before using it, you must create **manual backup copies** of your working configuration folders for **both games**.

### Falcon BMS

Backup the entire folder:

    Falcon BMS 4.38\User\Config

    
### DCS World

Backup the entire folder:

    Saved Games\DCS\Config\Input

    
(or `Saved Games\DCS.openbeta\Config\Input` if applicable)

These backups serve as the **source of truth**.  
The tool will copy the *content* from these backups into newly generated config files when Windows changes device GUIDs.

Without existing backups, the tool has nothing to restore.

---

## Features

### Common
- Content-based restore (SHA-256 comparison)
- Keeps new filenames and GUIDs intact
- Atomic file replacement
- Timestamped ZIP snapshots
- Configurable via `.ini` files
- Safe to run repeatedly

### Falcon BMS
- Matches controller XML files by name without GUID
- Restores assignments into newly generated BMS config files

### DCS World
- Operates on `*.diff.lua` joystick bindings
- Matches devices by name without GUID
- Ignores non-device files (keyboard, mouse, disabled.lua, etc.)
- Restores only joystick device bindings

---

## Project layout

    restoreJoystickAssignments/
    ├── bms_restore.py
    ├── dcs_restore.py
    ├── config.ini
    ├── dcsconfig.ini
    ├── README.md
    └── dist/
    ├── bms_restore.exe
    ├── dcs_restore.exe
    ├── config.ini
    └── dcsconfig.ini


---
