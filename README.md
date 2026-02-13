# bms_restore_joystick_xmls

A small Python utility to protect and automatically restore **Falcon BMS** joystick bindings when Windows changes USB device GUIDs.

The tool creates timestamped ZIP snapshots of the full BMS config folder and restores known-good assignment content into newly generated config files while keeping their new filenames and GUIDs.

---

## Why do we need this?

Windows sometimes reassigns USB device IDs (GUIDs), causing Falcon BMS to generate new controller config files and ignore your existing bindings.

This tool:
- Detects matching controller configs by **name (without GUID)**
- Copies the **content** from your backups into the new files
- Keeps the **new filename + GUID intact**
- Prevents hours of re-binding controls

---
