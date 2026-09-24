Copyright (C) 2026 ZionXiaoxiSuOGLocGo
SPDX-License-Identifier: GPL-3.0-or-later
# unity-manual Changelog

## [2.4.0] - 2026-09-24 — Official-Manual Gap Analysis Round
**Source**: full comparison against the Unity 6.0 official Manual (chapter-tree scan + 15 deep-read pages via subagents)

### Added
- **Special Folders in Assets** table — Editor/Resources/Plugins/StreamingAssets semantics, URL-only access on Android/Web, hidden-folder rules
- **Asset Import Essentials** chapter — Model 4-tab rig/materials workflow, Texture Type/Shape/sRGB/platform overrides, Audio Load-Type memory table (Vorbis ≈×10 pitfall)
- **Compilation & Domain Reload** chapter — asmdef basics, Enter Play Mode Options (Reload Domain Off) with its static-reset trade-off
- **Scripting Backends (Mono vs IL2CPP)** chapter — platform support table, Reflection.Emit ban, stripping/[Preserve]/link.xml trap
- **Terrain** chapter — four toolbar modes, brush shortcuts, tree/grass/collision, F-key focus pitfall
- **Physics Materials** section — friction/bounce combine modes; PhysicMaterial→PhysicsMaterial Unity 6 rename note
- **WheelCollider** section — suspension/slip-curve model, GetWorldPose mesh sync, Force App Point pitfall
- **Video Playback** chapter — render/audio/update modes, WebGL URL-source restriction
- **XR (VR/AR)** chapter — XR Plug-in Management + OpenXR + AR Foundation + XRI package map
- **Command Line & Batch Mode** — CI recipe (-batchmode -quit -executeMethod), -accept-apiupdate trap
- **Player logs** table (per-platform Player.log paths) in Troubleshooting
- **Tilemap Workflow** and **SpriteAtlas** sections (2D chapter)
- **Line & Trail Renderers** section (VFX chapter)
- Symptom Router: 9 new symptom rows; frontmatter keywords +13

## [2.3.0] - 2026-09-24 — Feature Coverage Round
**Source**: functional gap scan (grep-based coverage audit across 15 feature domains)

### Fixed
- **Cinemachine API updated to 3.x** (Unity 6 default): `Unity.Cinemachine` namespace, `CinemachineCamera`,
  plain `GetComponent<>()` for noise; added 2.x → 3.x naming table (old example would fail on Unity 6)

### Added
- **Symptom Router** table at the top — symptom → section one-liners for fast retrieval
- **NavMesh (Pathfinding)** section — NavMeshAgent, arrival detection, AI Navigation package baking, agent gotchas
- **Joints** section — Fixed/Hinge/Spring/Character/Configurable table + motorized hinge + breakForce example
- **Multiplayer (Netcode for GameObjects)** chapter — setup, spawn, NetworkVariable, ServerRpc/Rpc, IsOwner guards
- **WebGL Platform Notes** — compression headers, heap sizing, WASM threading, loading UX
- **Custom Editor Window** — MenuItem/GetWindow/OnGUI minimal tool template with Undo support
- **Testing** chapter — EditMode vs PlayMode, NUnit TestCase/UnityTest examples, testability guideline
- Input System chapter now owns its advanced subsections in place (Action Map Switching, Runtime Rebinding,
  Touch Input moved from the end-of-file "Input System Advanced" heading) plus a **Gamepad Vibration** note
- Debug visualization note (OnDrawGizmos / Debug.DrawRay) and ScreenCapture one-liner
- ScrollRect virtualization warning for long UI lists
- Frontmatter keywords: NavMesh, pathfinding, joint, multiplayer, Netcode, WebGL, EditorWindow, testing, Cinemachine

## [2.2.0] - 2026-09-24 — Mojibake Restore + Usability Audit Round
**Source**: usage-driven audit — retrieval tests, gap tests, subagent blind tests

### Fixed
- Restore CHANGELOG and URP reference bodies to pristine v2.1.1 content: the 2026-06-30 security pass
  re-encoded the files and corrupted every non-ASCII character (em-dashes, arrows, marks) into U+FFFD
  mojibake. Bodies are now byte-identical to the initial baseline; copyright headers re-applied.
- Remove Unreal Engine terminology bleed: `Enhanced Input` → `Input System` (Touch Input section), deleted UWorld/LineTrace cross-reference (Raycasting), deleted Compatible Skeleton comparison (Animation Retargeting)
- Remove duplicated horizontal rule before Profiling & Debugging

### Added
- **TextMeshPro** section under UI (fixes self-contradiction: TMP is Unity 6 default, but UI chapter only taught legacy `Text`)
- **Data Persistence & Save System** chapter (PlayerPrefs tier, JsonUtility + persistentDataPath save file with try/catch + version field, crash-safe write hardening)
- **Editor Troubleshooting** chapter (stuck importing, ShaderCache, DX11 fallback, version mismatch, crash recovery, Safe Mode)
- **CharacterController (No Rigidbody)** mini-section (Move + gravity pass, isGrounded timing, key properties)
- urp-unity6.md: RenderGraph Compatibility Mode escape hatch note
- Frontmatter keywords: TextMeshPro, save system, PlayerPrefs, save file, CharacterController, troubleshooting, editor crash, stuck importing; dropped redundant Shuriken / Input Manager

## [2.1.1] - 2026-06-30 — Audit Bug Fixes
**Source**: project-ledger quality audit

### Fixed
- H1: Fix `ObjectPool.Get()` empty queue `Dequeue()` crash
- H2: Remove conflicting `Rigidbody` from Player teaching example
- H3: Replace outdated namespace limitation with "lifted in 2022.2" note
- H4: Fix fictitious `EditorSettings.ini` to real menu instructions
- H5: Add missing `health` field declarations (x2 locations)
- H6: Fix `Unity 2023+` → `Unity 2022.2+ / Unity 6`
- H7: Add `Renderer` declaration to `FadeOut` coroutine
- M2: Cache `WaitForSeconds` in coroutine example
- M4: Fix undefined `impulse` variable
- M5: Fix async/await error-on-destroy table
- M8: Fix dead cross-reference to unreal-manual
- M9: Fix `collisionDetectionMode` property name
- M11: Add Addressables note to Resources.LoadAll example
- M13: Fix Fixed Timestep advice
- M1: Replace duplicate SO Event Channel with cross-reference
- L2: Fix lowercase "unity" → "Unity"
- L4: Add SafeArea/notch handling note
- L5: Update README line count

### Added
- Profiling & Debugging section (Profiler, Frame Debugger, common commands)
- `Animator.Play()` and `StringToHash()` examples
- `[ContextMenu]` attribute quick reference
- `async void` lifecycle warning in UniTask example

---

## [2.1.0] - 2026-06-30 — Anti-Patterns + Game Architecture + Retargeting + Mobile
**Source**: project-ledger audit session

### Added
- **Copyright + Version**: Copyright notice + SPDX identifier, version 2.1.0 metadata in frontmatter
- **Animation → Retargeting (Humanoid Avatar)**: Avatar setup/configuration workflow, muscle space masks, cross-model animation sharing, common issues
- **Common Anti-Patterns** (new chapter): Physics transform-position misuse, Unity API misuse (FindObjectOfType in Update, GetComponent caching, LINQ in hot paths), event subscription leaks, GC allocation hotspots table with fixes
- **Game Architecture Patterns** (new chapter): Finite State Machine (enum-based), Strategy Pattern via interface, Observer via ScriptableObject Event Channel (decoupled sender/listener)
- **Input System Advanced** (new chapter): Action Map switching, runtime rebinding (InteractiveRebinding + PlayerPrefs persistence), touch input patterns, Enhanced Input touch bindings
- **Shader Graph Basics** (new chapter): Creation workflow, 14-node quick reference, key material properties, common effects (dissolve, outline, ripple, fresnel, toon)
- **Mobile Optimization** (new chapter): Platform-specific settings checklist, runtime quality/lod/texture management, memory/fps detection, mobile-specific pitfalls (overdraw, battery, touch vs mouse)

---

## [2.0] - 2026-06-20 — Major Expansion
**Source**: project-ledger audit session

### Added
- **Editor Basics**: panel layout (Scene/Game/Hierarchy/Inspector/Project/Console), scene navigation shortcuts, Transform tools (W/E/R/Q/T/Y/V), Play/Pause/Step modes.
- **Project Setup**: template comparison table (6 templates), folder structure diagram, Unity Hub version management, Git setup with required `.gitignore` and `.meta` file explanation.
- **Package Manager**: 10 common packages quick-reference table with install/update/remove workflow.
- **C# Scripting Basics**: field visibility cheat sheet, Vector3/Vector2/Quaternion/Color type reference, `Time.deltaTime` with anti-pattern examples.
- **Lerp / SmoothDamp / MoveTowards**: 5 interpolation functions compared, common Lerp misuse (`t = Time.deltaTime`) with fix, SmoothDamp/SmoothStep/InverseLerp references.
- **Namespace**: 16 common namespaces table, custom namespace pattern, critical limitation warning (one file = one namespace for MonoBehaviour in Unity 2020.1+).
- **Null Reference Handling**: 6 common causes with fixes, defensive pattern code, Unity's special null override behavior.
- **Events & Delegates**: 4 communication patterns compared (serialized reference, UnityEvent, C# event/Action, SendMessage), cheat sheet for choosing.
- **Time.timeScale & Pausing**: pause/slow-motion code, affected vs unaffected table, selective pausing pattern.
- **Camera**: component properties table, scripting examples (ScreenPointToRay, WorldToScreenPoint), multi-camera setups (minimap, weapon overlay, split-screen, UI camera), Cinemachine quick-start.
- **Lighting**: light types comparison, real-time vs baked vs mixed decision table, Light Probes and Reflection Probes, Tags & Layers reference.
- **Physics vs Transform Movement**: the #1 beginner pitfall — direct transform.position on Rigidbody — with correct alternatives table.
- **Raycasting**: full API (raycast, sphere/box cast, layer masks, RaycastAll), debug visualization, Blueprint equivalent note.
- **2D Basics**: 3D→2D component mapping, Sprite Editor workflow, 2D physics API differences, sorting order hierarchy.
- **VFX (Particle System)**: Shuriken module reference table, script control, VFX Graph introduction, Shuriken vs VFX Graph selection guide.
- **Object Pooling**: full queue-based pool implementation, Unity built-in `ObjectPool<T>` reference, when-to-pool decision table.
- **Addressables**: load-by-address and AssetReference patterns, Resources replacement benefits.
- **Build & Publish**: Build Settings workflow, Player Settings quick-reference, Development Build, output folder structure.
- **Custom Inspector (Editor Scripting)**: CustomEditor pattern, `Editor/` folder convention.
- **async/await + UniTask**: UniTask quick-start, native Task caution, coroutine vs async decision table, cancellation token pattern.

### Principles
- Editor/Project Setup chapters for absolute beginners; coding chapters for intermediate.
- Each section includes both theory (why) and concrete code (how).
- Anti-patterns explicitly marked with ❌ and correct approaches with ✅.
- Decision tables added where multiple valid approaches exist.

---

## [1.0.0] - 2026-06-19 — Initial Release
**Source**: openSkills project launch (created via skill-creator)

### Added
- Unity engine core concepts: GameObject/Component architecture, scene management, render pipelines
  (URP/HDRP/Built-in), physics, animation system, UI Toolkit, uGUI, audio, input system (old + new),
  MonoBehaviour lifecycle, prefabs, ScriptableObject, coroutines, performance best practices.
- Version-specific references: `urp-2022.md` and `urp-unity6.md`.
- 14.8KB SKILL.md, ~1,088 lines.

### Principles
- Covers concept explanations and practical API patterns.
- Version-aware — separate reference files for 2022.3 LTS vs Unity 6.
- Maintenance: update when encountering recurring bugs, version migrations, or new engine features.
