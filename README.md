# SimpleAutoFarm Wiki

Welcome to the **SimpleAutoFarm** Wiki! This page contains all the information you need to install, configure, and use the SimpleAutoFarm plugin on your server.

## 🌟 Introduction
**SimpleAutoFarm** is an advanced, high-performance auto-farming solution designed for modern Minecraft servers. It completely reinvents AFK farming by implementing a **velocity-based movement** system, which smoothly propels players rather than using rigid teleportation. This allows for native client-side animations, realistic rotations, and efficient combat mechanics.

### Key Features:
* **Vanilla-like Movement:** Uses velocity and native rotation for extremely smooth and realistic movements.
* **Smart Stuck Detection:** Includes heuristics to detect obstacle collision with vertical velocity adjustments.
* **Fully GUI Driven:** Easy-to-use menu (`/autofarm`) for toggling settings.
* **Automated Mechanics:** Automatically attacks monsters, eats food/golden apples, and features a "stand still" toggle.
* **Tiered Gamepass System:** Daily farm time limits and movement speeds configurable by permission tiers (e.g., VIP, MVP).
* **Bossbar Integration:** Displays remaining time natively on the player's screen.
* **Performance Optimized:** Advanced tracking ensures the server remains lag-free even with many players farming.

---

## ⚙️ Installation

1. Download the `SimpleAutoFarm.jar` from BuiltByBit or the Releases tab.
2. Place the jar file into your server's `plugins/` directory.
3. Restart or reload your server. 
4. The plugin will automatically generate the default `config.yml` and `messages.yml` files.

---

## 🖥️ Commands

| Command | Description | Permission |
| :--- | :--- | :--- |
| `/autofarm` | Opens the AutoFarm GUI menu. | `simpleautofarm.use` |
| `/autofarm reload` | Reloads the configuration and messages. | `simpleautofarm.admin` |
| `/autofarm reset <player>` | Resets a player's daily used time limit back to 0. | `simpleautofarm.admin` |

*(Aliases: `/saf`)*

---

## 🔑 Permissions

Here is a list of all permissions to customize player experiences and monetize tiers.

| Permission | Description |
| :--- | :--- |
| `simpleautofarm.use` | Allows a player to open the `/autofarm` menu and use default features. |
| `simpleautofarm.admin` | Grants access to `/saf reload` and `/saf reset`. |
| `simpleautofarm.tier.vip` | Grants the VIP time limit duration (defined in config). |
| `simpleautofarm.tier.mvp` | Grants the MVP time limit duration (defined in config). |
| `simpleautofarm.speed.x2` | Multiplies the default movement speed while farming by a configured amount. |
| `simpleautofarm.speed.x3` | Grants a faster movement speed modifier. |

*(Note: Permissions for speed/tiers are completely customizable dynamically inside the `config.yml`)*

---

## 📁 Configuration (`config.yml`)

The configuration file allows you to define tiers, speeds, gui layouts, and more!

```yaml
# Radius to scan for mobs to attack (blocks)
radius: 10.0

# Walking speeds map matching permissions (Example: simpleautofarm.speed.x2)
speeds:
  default: 0.22
  x2: 0.35
  x3: 0.50

# Attack interval in ticks (20 ticks = 1 second)
interval: 10

# Durations for each tier in seconds (Daily Limits)
tiers:
  default: 300
  vip: 600
  mvp: 1200

# Daily limit resets automatically
reset-time-hours: 24
```
*(The config also lets you completely modify the GUI slots, materials, lores, and the Bossbar styling!)*

---

## 💬 Localization (`messages.yml`)

You can translate all messages or adjust prefixes directly in the `messages.yml`.

```yaml
prefix: "&8[&aAutoFarm&8] "
enabled: "&aAuto Farm enabled! You have &e%time% &aseconds left today."
disabled: "&cAuto Farm disabled!"
moved: "&cYou cannot move while Auto Farm is enabled! Type /autofarm to disable."
finished: "&eAuto Farm session finished!"
cooldown: "&cYou have used all your farming time today (%time%s). Please wait %wait% before farming again."
```

---

## 🛠️ Frequently Asked Questions (FAQ)

**Q: Can I add more tiers like ELITE or SUPREME?**
A: Yes! Simply add them to the `tiers` section in `config.yml` (e.g. `elite: 3600`) and grant players the permission `simpleautofarm.tier.elite`. You can do the exact same logic for custom speeds!

**Q: Does it work with specific claim plugins?**
A: Players cannot attack mobs in regions where they do not have damage permissions (handled globally by standard bukkit damage event checks).
