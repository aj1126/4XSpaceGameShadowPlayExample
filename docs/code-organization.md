# Code Organization

The active gameplay code is in:

- `4X Space Game/Assets/Scripts/`

The tutorial snapshots are in:

- `Scripts/` (organized by part number)

## Script organization by feature

### `Space/`

Core space/world domain and view transition logic:

- `Galaxy.cs` creates galaxy star data and star objects.
- `SolarSystem.cs` switches from galaxy to solar-system view and builds planets/starbases.
- `Star.cs`, `Planet.cs` define domain entities.
- `SpaceObjects.cs` creates shared star/planet/orbit/nameplate GameObjects.

### `Empires/`

Empire, economy, and fleet-related data and systems:

- `PlayerManager.cs` stores player state and owned planets.
- `Resources.cs` tracks credits/minerals/food and resource operations.
- `FleetManager.cs`, `Fleet.cs`, `Ship.cs` manage fleet/ship creation and buildup.
- `StarBase.cs` stores build queue and production progress.

### `UI/`

User interface control and updates:

- `GUIManagementScript.cs` controls in-world nameplates and ship build queue UI.
- `UIResourceManager.cs` updates resource text display.
- Additional button scripts handle UI actions.

### `Camera/`

- `CameraController.cs` handles pan, zoom, camera bounds, and view alignment.

### `Calculations/`

- `PositionMath.cs` provides coordinate conversion, random positioning, and collision checks.

### `Data Handlers/`

- `TextAssetManager.cs` parses text assets (for name lists).
- `RomanNumerals.cs` generates roman numerals for naming.

### Top-level scripts

- `TurnManager.cs` advances turn state and applies production/resources each turn.
- `Instantiation.cs` provides basic runtime prefab instantiation helpers.

## Runtime flow at a glance

1. `Galaxy` generates stars and planets and shows galaxy view.
2. `SolarSystem` opens when a star is selected.
3. `PlayerManager` and `Resources` track empire economy.
4. `FleetManager` and `StarBase` process ship queue and fleet creation.
5. `TurnManager` applies production/resources on end turn.
6. UI scripts sync resource counters and build queue information.
