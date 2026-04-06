# ⚡ XP Server — Counter-Strike: Source RPG

> A fully custom CS:S dedicated server running on Bazzite OS with a persistent RPG leveling system, 10x XP gain, and bot support.

---

## 🎮 About

XP Server transforms standard Counter-Strike: Source into a persistent RPG experience. Earn XP from kills, headshots, bomb plants, and objectives — then spend credits on powerful upgrades that change how you play every round.

---

## ✨ Features

- 🧠 **Persistent RPG Leveling** — XP and levels save between sessions via SQLite
- ⚡ **10x XP Multiplier** — Fast-paced progression out of the box
- 🤖 **15 Bots** — Server always has action, bots fill empty slots automatically
- 🛡️ **43 SM:RPG Plugins** — Full suite of upgrades compiled for SourceMod 1.12
- 🗺️ **Custom Map Rotation** — Classic CS:S maps
- 📋 **Custom MOTD** — Styled XP Server welcome screen with upgrade info

---

## 🧬 RPG Upgrades

Players earn XP and spend credits on upgrades via `!rpg` in chat:

| Upgrade | Effect |
|---|---|
| **Vampire** | Steal HP from enemies on hit |
| **Regeneration** | Slowly recover health over time |
| **Speed+** | Move faster than your enemies |
| **Stealth** | Become partially invisible |
| **Armor+** | Increase max armor capacity |
| **Antiflash** | Reduce flashbang blinding |
| **Reduced Gravity** | Jump higher, fall slower |
| **Bouncy Bullets** | Push enemies back on hit |
| **Damage+** | Deal extra damage per shot |
| **Health+** | Increase max HP |
| **Medic** | Heal nearby teammates |
| **Adrenaline** | Speed burst when firing |
| **Frost Pistol** | Slow enemies hit by pistol |
| **Fire Pistol** | Ignite enemies hit by pistol |
| **Mirror Damage** | Reflect damage back at attacker |
| **Long Jump** | Boost jump distance |
| **Impulse** | Knock enemies away |
| **Resupply** | Regenerate ammo every few seconds |
| **Denial** | Keep weapons on next spawn |
| + many more... | |

---

## 💬 In-Game Commands

| Command | Description |
|---|---|
| `!rpg` | Open the XP upgrade menu |
| `!xp` | Check your current level and XP |
| `!rank` | See your rank on the server |
| `!top10` | View the XP leaderboard |
| `!sell` | Sell an upgrade for credits |

---

## 🛠️ Tech Stack

| Component | Technology |
|---|---|
| OS | [Bazzite](https://bazzite.gg) (Fedora-based, immutable) |
| Container Runtime | Podman (rootless) |
| Game Server Manager | [LinuxGSM](https://linuxgsm.com) |
| Game | Counter-Strike: Source (App ID 232330) |
| Mod Framework | [MetaMod:Source](https://www.metamodsource.net) + [SourceMod](https://www.sourcemod.net) |
| RPG Plugin | [SM:RPG](https://github.com/peace-maker/smrpg) by peace-maker |
| Database | SQLite (via SourceMod) |

---

## ⚙️ XP Settings

```
smrpg_exp_kill        150.0   (10x default)
smrpg_exp_damage      10.0    (10x default)
smrpg_exp_headshot    500.0   (10x default)
smrpg_exp_bombplanted 1.5
smrpg_exp_bombdefused 3.0
smrpg_exp_teamwin     1.5
```

---

## 🚀 Server Info

```
Server Name:  [XP] CSS RPG
Game:         Counter-Strike: Source
Map Rotation: de_dust2, de_inferno, de_nuke, de_train, cs_italy, cs_assault + more
Max Players:  16 (15 bots + 1 human)
Bot Skill:    Easy (difficulty 1)
```

---

## 📦 Setup Overview

The server is deployed using a Podman container running LinuxGSM's CSS image. All RPG plugins were compiled from source using SourceMod's `spcomp64` compiler with patched smlib includes for SourceMod 1.12 compatibility.

### Directory Structure

```
~/xp-server/
├── serverfiles/
│   └── cstrike/
│       └── addons/
│           ├── metamod/
│           └── sourcemod/
│               ├── plugins/       ← 43 compiled .smx files
│               ├── configs/       ← smrpg configs + databases.cfg
│               ├── gamedata/      ← smrpg gamedata
│               └── translations/  ← smrpg translations
├── configs/
│   ├── server.cfg
│   ├── motd.txt
│   └── mapcycle.txt
├── start.sh
├── stop.sh
├── update.sh
└── docker-compose.yml
```

---

## 📝 License

This server configuration is open source. SM:RPG is by [peace-maker](https://github.com/peace-maker/smrpg) and licensed separately. SourceMod and MetaMod are by [AlliedModders](https://www.alliedmods.net).
