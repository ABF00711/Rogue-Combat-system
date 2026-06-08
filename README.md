# Rogue Combat System

A Roblox combat framework built around katana melee combat, with blocking, parrying, combos, and hit detection. The repository contains three Roblox place files (`.rbxl`) that can be opened directly in [Roblox Studio](https://create.roblox.com/).

## Place Files

| File | Size | Description |
|------|------|-------------|
| `rogue combat system base.rbxl` | ~2.0 MB | Core combat framework — weapons, stats, remotes, hitboxes, and shared modules |
| `katanacombat.rbxl` | ~1.1 MB | Full katana combat implementation with animations, VFX, and NPC combat scenarios |
| `map.rbxl` | ~400 KB | Environment / test map with katana models and sprint support |

### `rogue combat system base.rbxl`

The foundation place file. Use this as the starting point when integrating the combat system into your own game.

- **Weapons** — `Basic Katana` with sheath / unsheath and blocking states
- **Combat mechanics** — M1 attacks, heavy attacks, combos (up to 4 hits), blocking, and parrying
- **Hit detection** — configurable hitbox settings and sword-hit events
- **Stats** — `CombatStats` tracking health and combat state
- **Networking** — `RemoteEvent` / `RemoteFunction` handlers for client–server combat sync
- **UI** — damage indicators and health bar
- **Camera** — [Camera Shaker](https://github.com/Sleitnick/RbxCameraShaker) for impact feedback
- **Controls** — [SmoothShiftLock](https://devforum.roblox.com/t/smoothshiftlock-module/477314) for improved shift-lock camera behavior

### `katanacombat.rbxl`

A more complete combat experience built on top of the base system.

- Everything in the base place, plus:
- **RaycastHitboxV4** — precise raycast-based hit detection
- **Blocking handler** — block timing, perfect blocks, and block-break mechanics
- **Damage indicator GUI** — floating damage numbers on hit
- **Health manager** — server-side health tracking and display
- **Combat VFX** — hit effects, block explosions, and rain / environmental effects (`RainScript`)
- **In-combat state** — tracks whether a player is actively fighting
- **NPC combat** — example combat NPCs with dialogue

### `map.rbxl`

A lighter place file focused on the world and movement.

- Katana weapon models (v2 with sheath)
- Sprint system (`EnableSprinting` + `SprintRemoteEvent`)
- Minimal combat scripting — primarily a map / sandbox for testing assets

## Features

- Katana melee combat with combo chains
- Block and parry mechanics with perfect-block support
- Server-authoritative damage via remotes
- Configurable hitboxes and hit detection modes
- Camera shake and damage feedback on impact
- Smooth shift-lock camera for combat feel
- Health bars and combat stat tracking
- Sheath / unsheath weapon animations

## Getting Started

### Requirements

- [Roblox Studio](https://create.roblox.com/) (latest version recommended)
- A Roblox account with place-editing permissions

### Opening a Place File

1. Clone or download this repository.
2. Open Roblox Studio.
3. Go to **File → Open from File**.
4. Select one of the `.rbxl` files:
   - Start with **`rogue combat system base.rbxl`** to explore or integrate the core system.
   - Open **`katanacombat.rbxl`** for the full katana combat experience.
   - Open **`map.rbxl`** for the test environment and movement systems.
5. Press **Play** (F5) to test in Studio, or **Play Here** to test in the local session.

### Integrating Into Your Game

1. Open `rogue combat system base.rbxl` in Studio.
2. Copy the relevant services and folders (typically under `ReplicatedStorage`, `ServerScriptService`, and `StarterPlayer`) into your own place.
3. Ensure remotes, modules, and weapon models are replicated correctly.
4. Reference `katanacombat.rbxl` for a complete implementation example of blocking, VFX, and NPC combat.

> **Note:** These are binary `.rbxl` place files, not Rojo source projects. Scripts live inside the place files and are best edited in Roblox Studio. For version-controlled source, consider exporting scripts with a tool like [Rojo](https://rojo.space/) or [Remodel](https://github.com/rojo-rbx/remodel).

## Project Structure

```
Rogue-Combat-system/
├── rogue combat system base.rbxl   # Core combat framework
├── katanacombat.rbxl               # Full katana combat place
├── map.rbxl                        # Map / test environment
└── README.md
```

Inside each place file, scripts are organized under standard Roblox services:

| Service | Typical Contents |
|---------|------------------|
| `ReplicatedStorage` | Shared modules, remotes, weapon configs |
| `ServerScriptService` | Server-side combat logic, health management |
| `StarterPlayer` / `StarterPlayerScripts` | Client combat handlers, camera, input |
| `StarterCharacterScripts` | Per-character combat scripts |
| `Workspace` | Map geometry, weapon models, NPCs |

## Third-Party Modules

This project includes or references community modules. Credit the original authors if you redistribute or publish work based on these places.

| Module | Author | Used For |
|--------|--------|----------|
| SmoothShiftLock | Validark / ForeverHD (Ben Horton) | Smooth shift-lock camera |
| Camera Shaker | Stephen Leitnick | Screen shake on hits |
| RaycastHitboxV4 | Swordphin123 | Raycast hit detection |

## Combat Configuration (Reference)

Default values found in the place files:

| Setting | Value |
|---------|-------|
| Max combo hits | 4 |
| M1 damage | ~7.1 |
| Heavy attack damage | ~7 |

Hitbox color, block timing, and other values can be adjusted in the `HitboxSettings` / `CombatStats` modules inside each place.

## Repository

- **GitHub:** [ABF00711/Rogue-Combat-system](https://github.com/ABF00711/Rogue-Combat-system)

## License

No license file is included in this repository. Contact the repository owner before redistributing or using these assets in a published experience.
