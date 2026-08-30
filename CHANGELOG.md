# Changelog

## [0.4.3] - 2026-08-30

### Fixed
- `ABButtonEditor`: the `Unity Button` group wrapped the whole standard Button inspector, including the `On Click ()` list, in a foldout that was seeded collapsed. A freshly added `ABButton` therefore read as an empty component and users could not find where to wire their click callback. That group now opens by default; every other foldout group keeps its collapsed default.

### Changed
- `ABButton` now shows Unity's stock Button icon in the Inspector header and the Project window, so the inherited component is recognisable at a glance. The icon is a reference to Unity's built-in editor resource; no image asset is shipped with the package.

## [0.4.2] - 2026-07-06

### Fixed
- Add missing `com.unity.ugui` dependency to `package.json` — the Runtime and Editor code uses `UnityEngine.UI` and `UnityEngine.EventSystems`, but uGUI was not declared as a dependency. On projects with a minimal manifest (no uGUI resolved), this caused compilation errors. Declaring the dependency lets UPM install uGUI automatically.

## [0.4.1] - 2026-04-04

### Fixed
- Add `AB_UTILS_INSPECTOR` versionDefine and defineConstraint to Runtime, Editor and Tests asmdef to prevent compilation errors when Utils Inspector package is not yet resolved
- Remove empty Tests/Editor folder

## [0.4.0] - 2026-04-01

### Added
- `UnselectOnClick` property and Init parameter — when true, clicking the selected button clears the selection
- Auto-selection on click via internal `HandleClick` — buttons now manage selection automatically, no manual `Select()` call needed from consumer
- New tests: Click auto-selection, UnselectOnClick true/false, OnSwitchClick callback, Reset state, double Init listener guard (14 tests total)

## [0.3.0] - 2026-04-01

### Changed (Breaking)
- Rename Tab vocabulary to generic Selection vocabulary in UISwitchButtonsDic:
  - `DefaultTab` → `DefaultKey`
  - `CurrentTab` → `SelectedKey`
  - `AllTabClosed` → `NoneSelected`
  - `SelectTab(K)` → `Select(K)`
  - `CloseAllTab()` → `ClearSelection()`

### Added
- `Reset()` method to properly unsubscribe click delegates and reset state
- `IsInitialized` public read-only property
- `_clickDelegates` dictionary for safe targeted listener removal (no more RemoveAllListeners)

### Fixed
- `Init()` now properly initializes `SelectedKey` and `NoneSelected`
- `Init()` calls `Reset()` internally when called multiple times (prevents listener accumulation)
- Null-checks in `Select()` and `ClearSelection()` (consistent with `Init()`)

## [0.2.0] - 2026-04-01

### Added
- UISwitchButtonsDic<K, V> — generic switch-button dictionary for UISwitchButton collections
- Unit tests for UISwitchButtonsDic (7 tests covering Init, SelectTab, CloseAllTab, callbacks)
- Test assembly definition (AnkleBreaker.Utils.UIBasics.Tests)

## [0.1.0] - 2026-03-30

### Added
- Initial package setup — structure, assembly definitions, and metadata
