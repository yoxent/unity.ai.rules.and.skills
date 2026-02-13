---
name: unity_folder_structure
description: Organization rules for Assets, Assembly Definitions, Scene Hierarchy, and Prefab structure. Use when the user asks to create new folders, reorganize assets, or setup new systems.
---

# Unity Project Organization

## Assets/ Subdirectory Mapping
- `Art/`: Materials, Models, Textures, Animations, Sprites.
- `Scripts/`: Runtime (Core, Gameplay, UI, Utilities, DOTS), Editor, Tests.
- `AddressableAssets/`: Content organized by concurrent usage or logical entity strategy.
- `Prefabs/`: Consistent subfolders for Characters, Environment, UI, and Effects.

## Assembly Definition (.asmdef)
All major systems must have their own assembly definitions.
- `Core.asmdef`
- `Gameplay.asmdef`
- `UI.asmdef`

## Scene & Prefab Organization
- **Hierarchy Sections**: Use sections like `--- SYSTEMS ---`, `--- LEVEL ---`, and `--- DYNAMIC ---`.
- **Prefab Components**: Separate visual models, colliders, effects, and audio sources into child objects.
