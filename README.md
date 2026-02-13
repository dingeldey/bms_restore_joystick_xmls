# restore_joystick_xmls

A small Python utility to protect and automatically restore **Falcon BMS** adn **DCS** joystick bindings when Windows changes USB device GUIDs.

---

## Why do we need this?

Windows sometimes reassigns USB device IDs (GUIDs), causing Falcon BMS to generate new controller config files and ignore your existing bindings.

This tool:
- Detects matching controller configs by **name (without GUID)**
- Copies the **content** from your backups into the new files
- Keeps the **new filename + GUID intact**
- Prevents hours of re-binding controls

---
