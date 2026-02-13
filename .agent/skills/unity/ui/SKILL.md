---
name: unity_ui_systems
description: Guidelines for Unity UI Canvas (Primary) and UI Toolkit. Handles UXML, USS, RectTransform, and TMP. Use when creating or modifying UI.
---

# UI Implementation

## Primary: Unity UI Canvas (UGUI)
- **TextMeshPro**: User `TextMeshProUGUI` instead of `Text`.
- **Optimization**: Turn off **Raycast Target** on non-interactive elements.

## Secondary: UI Toolkit
- **Separation**: Split Business Logic (Controller) from UI Logic (View).
- **Styling**: Use USS for themes.

## Project Selection
**Project** defaults to **Unity UI Canvas / UGUI**.
