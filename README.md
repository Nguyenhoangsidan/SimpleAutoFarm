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
#   _____ _                 _         _         _          ______                     
#  / ____(_)               | |       / \       | |        |  ____|                    
# | (___  _ _ __ ___  _ __ | | ___  / _ \ _   _| |_ ___   | |__ __ _ _ __ _ __ ___  
#  \___ \| | '_ ` _ \| '_ \| |/ _ \/ ___ \ | | | __/ _ \  |  __/ _` | '__| '_ ` _ \ 
#  ____) | | | | | | | |_) | |  __/ /   \ \ |_| | || (_) | | | | (_| | |  | | | | | |
# |_____/|_|_| |_| |_| .__/|_|\___/_/    \_\__,_|\__\___/  |_|  \__,_|_|  |_| |_| |_|
#                    | |                                                            
#                    |_|                                                            
#
# SimpleAutoFarm Configuration File
# 

# Mob detection radius (blocks)
radius: 10.0

# Movement speed corresponding to permission (e.g. simpleautofarm.speed.x2)
speeds:
  default: 0.22
  x2: 0.35
  x3: 0.50

# Attack interval in ticks (20 ticks = 1 second)
interval: 10

# Daily farm durations (Seconds) per Tier Rank (Permission: simpleautofarm.tier.<name>)
tiers:
  default: 300
  vip: 600
  mvp: 1200

# User Interface Configuration
gui:
  title: "&8» &a&lAFK CONTROL PANEL &8«"
  size: 27
  auto_attack:
    slot: 10
    material: "DIAMOND_SWORD"
    name: "&b&l⚔ Auto Attack Mobs ⚔"
    lore_on:
      - "&7Status: &aACTIVE"
      - ""
      - "&8Click to &cDISABLE&8."
    lore_off:
      - "&7Status: &cINACTIVE"
      - ""
      - "&8Click to &aENABLE&8."
  stand_still:
    slot: 12
    material: "IRON_BOOTS"
    name: "&b&l👟 Stand Still 👟"
    lore_on:
      - "&7Status: &aACTIVE"
      - ""
      - "&8Click to &cDISABLE&8."
    lore_off:
      - "&7Status: &cINACTIVE"
      - ""
      - "&8Click to &aENABLE&8."
  auto_eat:
    slot: 14
    material: "GOLDEN_APPLE"
    name: "&d&l🍎 Auto Eat (Food/GApples) 🍎"
    lore_on:
      - "&7Status: &aACTIVE"
      - ""
      - "&8Click to &cDISABLE&8."
    lore_off:
      - "&7Status: &cINACTIVE"
      - ""
      - "&8Click to &aENABLE&8."
  toggle_farm:
    slot: 16
    material_on: "LIME_DYE"
    material_off: "GRAY_DYE"
    name: "&e&l⭐ AutoFarm Core ⭐"
    lore_on:
      - "&7System Status: &aRUNNING"
      - ""
      - "&8Click to &cSTOP&8."
    lore_off:
      - "&7System Status: &cIDLE"
      - ""
      - "&8Click to &aSTART&8."
  info:
    slot: 22
    material: "CLOCK"
    name: "&a&l⏱ Time Information ⏱"
    lore:
      - "&7You have &e%time% &7left to farm today."

bossbar:
  title: "&a&lAFK TIME: &e&l%time%"
  color: "GREEN"
  style: "SOLID"

# Automatic limit reset time (Hours)
reset-time-hours: 24

```
*(The config also lets you completely modify the GUI slots, materials, lores, and the Bossbar styling!)*

---

## 💬 Localization (`messages.yml`)

You can translate all messages or adjust prefixes directly in the `messages.yml`.

```yaml
#   _____ _                 _         _         _          ______                     
#  / ____(_)               | |       / \       | |        |  ____|                    
# | (___  _ _ __ ___  _ __ | | ___  / _ \ _   _| |_ ___   | |__ __ _ _ __ _ __ ___  
#  \___ \| | '_ ` _ \| '_ \| |/ _ \/ ___ \ | | | __/ _ \  |  __/ _` | '__| '_ ` _ \ 
#  ____) | | | | | | | |_) | |  __/ /   \ \ |_| | || (_) | | | | (_| | |  | | | | | |
# |_____/|_|_| |_| |_| .__/|_|\___/_/    \_\__,_|\__\___/  |_|  \__,_|_|  |_| |_| |_|
#                    | |                                                            
#                    |_|                                                            
#
# Message Configuration for SimpleAutoFarm

prefix: "&8[&a&lAutoFarm&8] "
enabled: "&a&lENABLED &7| &aAuto Farm is now running! You have &e%time% &aleft today."
disabled: "&c&lDISABLED &7| &cAuto Farm has been stopped!"
moved: "&c&lWARNING &7| &fDo not move while AFK farming! Type /autofarm to disable."
finished: "&e&lEXPIRED &7| &eYour AFK farming time for today has run out!"
reload: "&a&lSUCCESS &7| &aAll configurations have been reloaded!"
no_permission: "&c&lERROR &7| &cYou do not have permission to do this."
cooldown: "&c&lTIMEOUT &7| &cYou have exceeded your limit (%time%s). Wait %wait% to farm again."
admin_reset: "&a&lADMIN &7| &fReset farming time for player &e%player%."
player_not_found: "&c&lERROR &7| &cCould not find the specified player."

help:
  - "&8&m==========================================="
  - " &a&l SimpleAutoFarm &7- Ultimate Edition"
  - ""
  - " &f&l* &e/autofarm &7- Open the main menu."
  - " &f&l* &e/autofarm help &7- View this help page."

admin_help:
  - " &c&l* &e/autofarm reload &7- Reload plugin data."
  - " &c&l* &e/autofarm reset <name> &7- Reset player time limits."
  - "&8&m==========================================="

```

---

## 🛠️ Frequently Asked Questions (FAQ)

**Q: Can I add more tiers like ELITE or SUPREME?**
A: Yes! Simply add them to the `tiers` section in `config.yml` (e.g. `elite: 3600`) and grant players the permission `simpleautofarm.tier.elite`. You can do the exact same logic for custom speeds!

**Q: Does it work with specific claim plugins?**
A: Players cannot attack mobs in regions where they do not have damage permissions (handled globally by standard bukkit damage event checks).
