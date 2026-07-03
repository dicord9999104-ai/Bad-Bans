# BadBans Wiki

<div align="center">

## 🛡️ BadBans

**A lightweight, modern and zero-lag punishment system for Paper servers.**

**Author:** `Bad_0320`
**Platform:** `Paper`
**Java:** `25+`
**Storage:** `MariaDB / SQLite`
**Sync:** `Redis`

</div>

---

## 📌 Introduction

**BadBans** is a modern punishment plugin for Paper servers, built to manage player punishments in a clean, fast and professional way.

It supports **bans, IP bans, mutes, IP mutes, warnings, kicks, dupe IP checks, punishment history, staff rollback, silent punishments and optional player wipe systems**.

BadBans is designed to be **async**, **multi-server ready**, **lightweight** and easy to configure.

> Built to punish players, not your TPS.

---

# 🚀 Features

| Feature                   | Description                                              |
| ------------------------- | -------------------------------------------------------- |
| **Account Bans**          | Ban players by UUID                                      |
| **IP Bans**               | Ban IP addresses and block linked accounts               |
| **Temporary Punishments** | Create temporary bans, mutes and warns                   |
| **Mute System**           | Block chat, private messages and chat commands           |
| **Warning System**        | Warn players and auto-ban after too many warnings        |
| **Kick System**           | Kick one player or the entire server                     |
| **Silent Punishments**    | Use `-s` to hide punishments from normal players         |
| **Dupe IP Scanner**       | Find linked accounts by IP                               |
| **Punishment History**    | View active and expired punishments                      |
| **Rollback System**       | Undo punishments issued by a staff member                |
| **Pretty Punishment IDs** | Stable IDs like `#PPLV4821`                              |
| **XP Sound Feedback**     | Staff hear the XP orb sound after successful punishments |
| **Optional Wipe System**  | Fully reset player data manually or on ban               |
| **MariaDB Support**       | Main storage for networks                                |
| **Redis Sync**            | Synchronize punishments between servers                  |
| **SQLite Fallback**       | Local fallback when MariaDB/Redis are not available      |
| **Web History Support**   | Designed to support web punishment history               |

---

# 📦 Requirements

| Requirement                | Version                           |
| -------------------------- | --------------------------------- |
| **Server Software**        | Paper                             |
| **Java**                   | 25+                               |
| **Minecraft/Paper Target** | 26.1.2                            |
| **Database**               | MariaDB recommended               |
| **Redis**                  | Recommended for multi-server sync |
| **Fallback Storage**       | SQLite                            |

BadBans uses **Paper runtime libraries** for heavy dependencies, so the final plugin jar stays lightweight.

---

# 🧩 Installation

## 1. Download the plugin

Download the latest `BadBans.jar`.

## 2. Upload it to your server

Place the file inside your server plugins folder:

`/plugins/BadBans.jar`

## 3. Start the server

Start your Paper server once to generate the config files.

## 4. Configure storage

Open:

`/plugins/BadBans/config.yml`

Set your MariaDB and Redis settings if you are using a network setup.

## 5. Restart the server

Restart the server after configuring the plugin.

---

# ⚙️ Storage System

BadBans supports three storage modes.

| Storage     | Usage                       |
| ----------- | --------------------------- |
| **MariaDB** | Recommended source of truth |
| **Redis**   | Real-time multi-server sync |
| **SQLite**  | Local fallback              |

## Recommended Setup

For a network, use:

| Service | Status        |
| ------- | ------------- |
| MariaDB | Enabled       |
| Redis   | Enabled       |
| SQLite  | Fallback only |

If MariaDB or Redis are missing, BadBans can automatically disable multi-server sync and fall back to SQLite.

---

# 🔇 Silent Punishments

All punishment commands support `-s` at the end.

## Public punishment

`/ban PlayerName 7d Cheating`

Everyone online sees the punishment broadcast.

## Silent punishment

`/ban PlayerName 7d Cheating -s`

Only console and staff with this permission can see it:

`badbans.notify.silent`

---

# 🔊 Success Sound

When a staff member successfully executes a punishment, they hear the classic Minecraft XP orb pickup sound.

Default sound:

`entity.experience_orb.pickup`

This sound only plays for the staff member who executed the command.

---

# 🆔 Punishment IDs

BadBans generates clean and stable punishment IDs.

Example player:

`PupillaViola`

Generated punishment ID:

`#PPLV4821`

The first part is based on the player name, and the last 4 numbers are random.

For example:

| Player         | Example ID  |
| -------------- | ----------- |
| `PupillaViola` | `#PPLV4821` |
| `Bad_0320`     | `#BAD04821` |

Punishment IDs are saved in the database and do not change when the player rejoins.

---

# ⚠️ Warning System

BadBans includes an automatic warning punishment system.

By default:

| Setting              | Default                     |
| -------------------- | --------------------------- |
| Max active warnings  | `3`                         |
| Automatic punishment | Ban                         |
| Ban duration         | `1 day`                     |
| Reason               | `Too many warnings reached` |

When a player reaches 3 active warnings, they are automatically banned for 1 day.

---

# 🧹 Wipe System

BadBans includes a powerful wipe system.

Command:

`/wipe <player> [-s]`

The wipe system can reset:

| Data                | Reset |
| ------------------- | ----- |
| Inventory           | ✅     |
| Ender chest         | ✅     |
| XP and levels       | ✅     |
| Potion effects      | ✅     |
| Food and saturation | ✅     |
| Advancements        | ✅     |
| Statistics          | ✅     |
| Recipes             | ✅     |
| Vanilla playerdata  | ✅     |
| Stats files         | ✅     |
| Advancement files   | ✅     |
| BadBans data        | ✅     |
| External rank data  | ✅     |

---

# 🧹 Wipe On Ban

BadBans includes an optional automatic wipe-on-ban system.

Default config option:

`wipe-on-ban: false`

## Behavior

| Value   | Result                                      |
| ------- | ------------------------------------------- |
| `false` | Players are not wiped when banned           |
| `true`  | Players are wiped automatically when banned |

This option is disabled by default for safety.

---

# 📜 Commands

## 🔨 Ban Commands

| Command                                       | Description                             |
| --------------------------------------------- | --------------------------------------- |
| `/ban <player> [time] [reason] [-s]`          | Ban a player permanently or temporarily |
| `/ipban <player/IP> [time] [reason] [-s]`     | Ban an IP address                       |
| `/tempban <player> <time> [reason] [-s]`      | Temporarily ban a player                |
| `/tempipban <player/IP> <time> [reason] [-s]` | Temporarily ban an IP address           |
| `/unban <player>`                             | Remove an active player ban             |
| `/unbanip <player/IP>`                        | Remove an active IP ban                 |

---

## 🔇 Mute Commands

| Command                                    | Description                              |
| ------------------------------------------ | ---------------------------------------- |
| `/mute <player> [time] [reason] [-s]`      | Mute a player permanently or temporarily |
| `/tempmute <player> <time> [reason] [-s]`  | Temporarily mute a player                |
| `/unmute <player>`                         | Remove an active mute                    |
| `/ipmute <player/IP> [time] [reason] [-s]` | Mute an IP address                       |
| `/unipmute <player/IP>`                    | Remove an active IP mute                 |

---

## ⚠️ Warning Commands

| Command                                   | Description                               |
| ----------------------------------------- | ----------------------------------------- |
| `/warn <player> [reason] [-s]`            | Warn a player                             |
| `/tempwarn <player> <time> [reason] [-s]` | Temporarily warn a player                 |
| `/unwarn <player> [id/all]`               | Remove one warning or all active warnings |

---

## 👢 Kick Commands

| Command                        | Description              |
| ------------------------------ | ------------------------ |
| `/kick <player> [reason] [-s]` | Kick a player            |
| `/kickall [reason] [-s]`       | Kick every online player |

---

## 🔍 Information Commands

| Command                  | Description                           |
| ------------------------ | ------------------------------------- |
| `/check <player>`        | Show active punishments               |
| `/history <player>`      | Show full punishment history          |
| `/iphistory <player/IP>` | Show IP history                       |
| `/dupeip <player/IP>`    | Show linked accounts from the same IP |

---

## ⚙️ Admin Commands

| Command                            | Description                                 |
| ---------------------------------- | ------------------------------------------- |
| `/badbans reload`                  | Reload configuration files                  |
| `/badbans rollback <staff> [time]` | Cancel punishments issued by a staff member |
| `/wipe <player> [-s]`              | Fully reset a player                        |

---

# 🔐 Permissions

## Ban Permissions

| Permission                  | Description      |
| --------------------------- | ---------------- |
| `badbans.command.ban`       | Use `/ban`       |
| `badbans.command.ipban`     | Use `/ipban`     |
| `badbans.command.tempban`   | Use `/tempban`   |
| `badbans.command.tempipban` | Use `/tempipban` |
| `badbans.command.unban`     | Use `/unban`     |
| `badbans.command.unbanip`   | Use `/unbanip`   |

---

## Mute Permissions

| Permission                 | Description     |
| -------------------------- | --------------- |
| `badbans.command.mute`     | Use `/mute`     |
| `badbans.command.tempmute` | Use `/tempmute` |
| `badbans.command.unmute`   | Use `/unmute`   |
| `badbans.command.ipmute`   | Use `/ipmute`   |
| `badbans.command.unipmute` | Use `/unipmute` |

---

## Warning Permissions

| Permission                 | Description     |
| -------------------------- | --------------- |
| `badbans.command.warn`     | Use `/warn`     |
| `badbans.command.tempwarn` | Use `/tempwarn` |
| `badbans.command.unwarn`   | Use `/unwarn`   |

---

## Kick Permissions

| Permission                | Description    |
| ------------------------- | -------------- |
| `badbans.command.kick`    | Use `/kick`    |
| `badbans.command.kickall` | Use `/kickall` |

---

## Information Permissions

| Permission                  | Description      |
| --------------------------- | ---------------- |
| `badbans.command.check`     | Use `/check`     |
| `badbans.command.history`   | Use `/history`   |
| `badbans.command.iphistory` | Use `/iphistory` |
| `badbans.command.dupeip`    | Use `/dupeip`    |

---

## Admin Permissions

| Permission                 | Description             |
| -------------------------- | ----------------------- |
| `badbans.command.reload`   | Use `/badbans reload`   |
| `badbans.command.rollback` | Use `/badbans rollback` |
| `badbans.command.wipe`     | Use `/wipe`             |
| `badbans.notify.silent`    | See silent punishments  |

---

# 🎨 Messages

BadBans includes customizable messages with a clean punishment style.

| Message Type         | Style                           |
| -------------------- | ------------------------------- |
| Ban screen           | Small caps red punishment style |
| IP ban screen        | Small caps red punishment style |
| Mute message         | Clean warning style             |
| Warn message         | Staff-friendly format           |
| Broadcasts           | Clean and readable              |
| Silent notifications | Staff-only                      |
| Dupe IP output       | Status-colored players          |

The plugin uses a small caps Unicode style, not normal uppercase.

Example style:

**ʏᴏᴜʀ ᴀᴄᴄᴏᴜɴᴛ ʜᴀꜱ ʙᴇᴇɴ ʙᴀɴɴᴇᴅ**

---

# 🔍 Dupe IP

The command:

`/dupeip <player/IP>`

shows all accounts connected to the same IP.

Player names are colored depending on their status.

| Status    | Meaning                         |
| --------- | ------------------------------- |
| Online    | Player is currently online      |
| Offline   | Player is offline               |
| Banned    | Player has an active ban        |
| Muted     | Player has an active mute       |
| IP Banned | Player is linked to a banned IP |

---

# 🔁 Rollback System

The rollback system lets you cancel punishments issued by a specific staff member.

Command:

`/badbans rollback <staff> [time]`

Example:

`/badbans rollback Bad_0320 1d`

This is useful if a staff member abuses permissions or issues wrong punishments.

---

# 🌐 Web History Support

BadBans is designed to include web history support for punishment lookup.

The web system can be used to view punishment data, history and player records outside the game.

---

# 🧪 Time Format

BadBans supports simple time formats.

| Format | Meaning    |
| ------ | ---------- |
| `10s`  | 10 seconds |
| `5m`   | 5 minutes  |
| `2h`   | 2 hours    |
| `7d`   | 7 days     |
| `1w`   | 1 week     |
| `1mo`  | 1 month    |
| `1y`   | 1 year     |

Examples:

`/tempban Player 7d Cheating`

`/tempmute Player 30m Spam`

`/tempwarn Player 1d Toxic behavior`

---

# 🧩 Technical Design

BadBans is designed for modern Paper servers.

| Technical Detail        | Status |
| ----------------------- | ------ |
| `paper-plugin.yml`      | ✅      |
| Paper API               | ✅      |
| Java 25+                | ✅      |
| Maven                   | ✅      |
| No NMS                  | ✅      |
| No useless reflection   | ✅      |
| Runtime libraries       | ✅      |
| Lightweight jar         | ✅      |
| Async database logic    | ✅      |
| Redis sync              | ✅      |
| MariaDB source of truth | ✅      |
| SQLite fallback         | ✅      |
| Clean configs           | ✅      |
| Modular design          | ✅      |

---

# ❓ FAQ

## Does BadBans support silent punishments?

Yes. Add `-s` at the end of the command.

Example:

`/ban Player 7d Cheating -s`

---

## Does BadBans support IP tracking?

Yes. BadBans tracks both UUIDs and IP addresses.

---

## Can BadBans work without MariaDB?

Yes. If MariaDB is not available, BadBans can use SQLite fallback.

---

## Can BadBans sync across multiple servers?

Yes. Multi-server sync uses Redis.

---

## Does BadBans support automatic bans after warnings?

Yes. By default, 3 active warnings trigger a 1-day ban.

---

## Does BadBans wipe players when banned?

Not by default.

The option is:

`wipe-on-ban: false`

Set it to `true` to enable automatic wipe on ban.

---

## Does BadBans use NMS?

No. BadBans is designed around the Paper API and avoids NMS.

---

# 🛡️ Final Notes

BadBans is built for server owners who want a clean, fast and complete punishment system without unnecessary lag or bloated jar files.

**Punish smarter. Sync faster. Keep your TPS safe.**
