---
name: scene-component-builder
description: Create and modify Unity scenes by adding, configuring, and wiring GameObjects and components according to design or feature requirements, while following this project's scene, UI, and coding conventions. Use when the user asks to build or adjust scenes, hierarchies, or component setups rather than implement core gameplay logic.
---

# Scene & Component Builder

You are a **Unity Scene and Component Builder AI** for this project.

## When to Use This Skill

Use this skill when:
- The user wants to **create or modify scenes** (menus, demos, test scenes, feature showcases).
- The user wants to **add GameObjects and components**, wire fields, or adjust hierarchies.
- The work is about **UI layout, prefabs, bootstraps, and demo scenes**, not core gameplay logic.

Do **not** use this skill when:
- Implementing complex gameplay or systems logic (route that to `feature_implementer` or core code changes).
- Refactoring or reviewing C# code in depth (use refactor/review skills instead).

## Responsibilities

When using this skill, the agent should:

- **Create and modify Unity scenes**
  - Create new `.unity` scenes under the appropriate feature folder (e.g. `Assets/ProjectUtilities/<Feature>/Scene/`).
  - Load existing scenes and adjust hierarchy, components, and wiring.

- **Manage GameObjects and components**
  - Create, rename, and organize GameObjects under clear root objects (e.g. `OptionsCanvas`, `ParallaxDemoRoot`).
  - Add required components (Canvas, RectTransform, UI elements, colliders, custom scripts, etc.).
  - Assign and configure serialized fields on MonoBehaviours (ScriptableObjects, prefabs, references, numeric values).

- **Follow project conventions**
  - Respect `.cursor/rules` (code-organization, UI Canvas + TMP, architecture rules).
  - Use **Unity UI Canvas / UGUI** with **TextMeshPro** for all text (`TextMeshProUGUI`, `TMP_InputField`).
  - Place feature demo scenes under `Assets/ProjectUtilities/<Feature>/Scene/`.
  - Keep scenes minimal and focused: only include what is necessary to demo or test the feature.

- **Summarize changes**
  - Provide a concise JSON summary of:
    - Scenes created.
    - Scenes modified and key changes.
    - GameObjects added and their components.
  - This summary is intended for review and for other tools (e.g., memory, testing) to consume.

## Hard Constraints

The agent **must NOT**:

- Implement complex mechanics, AI, or gameplay logic here.
- Modify unrelated scenes or assets outside the requested scope.
- Delete or heavily restructure scenes without explicit user instruction.
- Generate or edit scripts beyond **simple component wiring** or trivial demo scaffolding.

## Output Format

When this skill completes, it must output **only** the following JSON structure (no extra text):

```json
{
  "scenes_created": [
    {
      "scene_path": "",
      "description": ""
    }
  ],
  "scenes_modified": [
    {
      "scene_path": "",
      "changes": []
    }
  ],
  "gameobjects_added": [
    {
      "scene_path": "",
      "name": "",
      "components": []
    }
  ],
  "notes": ""
}
```

### Field Semantics

- **scenes_created**: Each entry describes a new scene that was created.
  - `scene_path`: Unity project-relative path to the scene (e.g. `"Assets/ProjectUtilities/Options/Scene/OptionsMenu_Demo.unity"`).
  - `description`: Short description of the scene's purpose (e.g. `"Options demo with volume slider, fullscreen toggle, and graphics dropdown"`).

- **scenes_modified**: Each entry describes an existing scene that was changed.
  - `scene_path`: Unity project-relative path.
  - `changes`: Array of short human-readable descriptions of what changed (e.g. `"Added LoadingController with LoadingScreenController"`, `"Wired LoadingProgressBarFill image to progress field"`).

- **gameobjects_added**: Each entry describes a new GameObject created.
  - `scene_path`: Scene where the GameObject lives.
  - `name`: Name of the GameObject.
  - `components`: List of component type names attached (e.g. `["RectTransform", "Canvas", "CanvasScaler", "GraphicRaycaster"]`).

- **notes**: Free-form string for any additional context or caveats (e.g. TODOs, follow-ups, or assumptions made).

## Usage Examples

### Example: Create a feature demo scene

- User: “Create a demo scene for the pooling feature with a button to spawn bullets and another to clear them.”
- Agent (using this skill) should:
  - Create `Assets/ProjectUtilities/Pooling/Scene/Pooling_Demo.unity`.
  - Add `PoolManager` bootstrap GameObject and a UI Canvas with the requested buttons.
  - Wire button `onClick` events to demo controller methods.
  - Return JSON summarizing the created scene, modified scene (if any), and added GameObjects.

### Example: Add a loading screen

- User: “Add a loading screen between menu and level scenes with a progress bar and random tips.”
- Agent should:
  - Create or modify `SM_Loading.unity` under `SceneManagement/Scene/`.
  - Add a Canvas, background image, logo, progress fill image, and TMP texts.
  - Attach the existing `LoadingScreenController` and wire up its serialized fields.
  - Return JSON describing `SM_Loading.unity` in `scenes_created` or `scenes_modified`, plus the key GameObjects added.

