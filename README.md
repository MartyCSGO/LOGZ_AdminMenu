# LOGZ AdminMenu

**LOGZ AdminMenu** is a plugin for CounterStrikeSharp / CS2 that adds a quick admin menu for LOGZ Romania servers.

The plugin is made to work together with **LOGZ_Admin** and does not duplicate the ban, kick, gag, mute or silence system. It only executes the existing commands in `LOGZ_Admin`.

---

## Current Version

```txt
1.0.3
```

---

## Include Necessary

For full functionality, this plugin needs:

- [LOGZ_Admin](https://github.com/MartyCSGO/LOGZ_Admin)

Without `LOGZ_Admin`, the menu can open, but the administration commands will not work.

---

## Features

- quick menu for admins
- player actions:
  - kick
  - ban
  - slay
  - respawn
- comms actions:
  - gag
  - ungag
  - mute
  - unmute
  - silence
- team management:
  - move to Terrorists
  - move to Counter-Terrorists
  - move to Spectator
- plugin info menu
- version/info commands
- configurable messages
- configurable command templates
- `version.txt` support
- GitHub update URL support
- LOGZ Romania proprietary license

---

## Commands

```txt
!adminmenu
!amenu
css_adminmenu
css_amenu
css_logzadminmenu_version
css_logzadminmenu_info
css_logzadminmenu_reload
```

### Command Details

| Command | Description |
|---|---|
| `!adminmenu` / `css_adminmenu` | Opens the admin menu |
| `!amenu` / `css_amenu` | Shortcut for admin menu |
| `css_logzadminmenu_version` | Shows plugin version and version URL |
| `css_logzadminmenu_info` | Shows plugin info, GitHub URL, website and license |
| `css_logzadminmenu_reload` | Shows the correct reload command |

---

## Permission

Default permission:

```txt
@logz/adminmenu
```

Root permissions also have access automatically:

```txt
@css/root
@logz/root
```

Add `@logz/adminmenu` to your admin group if you want normal admins to access the menu.

Example:

```json
{
  "Name": "Administrator",
  "Permissions": [
    "@logz/adminmenu"
  ]
}
```

---

## Installation

1. Compile the plugin with Visual Studio 2022.
2. Copy the compiled files to:

```txt
/game/csgo/addons/counterstrikesharp/plugins/LOGZ_AdminMenu/
```

3. Make sure the folder contains:

```txt
LOGZ_AdminMenu.dll
version.txt
```

4. Restart the server or reload the plugin:

```txt
css_plugins reload LOGZ_AdminMenu
```

---

## Config Path

The config is generated automatically at:

```txt
/game/csgo/addons/counterstrikesharp/configs/plugins/LOGZ_AdminMenu/LOGZ_AdminMenu.json
```

---

## Default Config Example

```json
{
  "Enabled": true,
  "RequiredPermission": "@logz/adminmenu",
  "OpenCommands": [
    "css_adminmenu",
    "css_amenu"
  ],
  "ChatPrefix": "{Gold}[LOGZ AdminMenu]{Default}",
  "MenuTitle": "★ LOGZ Admin Menu ★",
  "WebsiteUrl": "https://www.logz.ro",
  "GithubUrl": "https://github.com/USERNAME/LOGZ_AdminMenu",
  "VersionUrl": "https://raw.githubusercontent.com/USERNAME/LOGZ_AdminMenu/main/version.txt",
  "LicenseName": "LOGZ Romania Proprietary License",
  "DefaultBanMinutes": 30,
  "DefaultGagMinutes": 30,
  "DefaultMuteMinutes": 30,
  "DefaultSilenceMinutes": 30,
  "ShowExecutedCommandToAdmin": true,
  "ShowOpenMessage": true,
  "OpenMessage": "{Green}AdminMenu deschis. Selectează acțiunea dorită.",
  "NoAccessMessage": "{Red}Nu ai acces la AdminMenu.",
  "DisabledMessage": "{Red}AdminMenu este dezactivat.",
  "NoPlayersMessage": "Nu sunt playeri online.",
  "CommandExecutedMessage": "{Green}Executat: {Yellow}{COMMAND}",
  "ReasonText": "AdminMenu"
}
```

---

## Command Templates

`LOGZ_AdminMenu` executes commands from `LOGZ_Admin`.

Default:

```json
"CommandTemplates": {
  "kick": "css_kick #{userid} {reason}",
  "ban": "css_ban #{userid} {minutes} {reason}",
  "slay": "css_slay #{userid}",
  "respawn": "css_respawn #{userid}",
  "gag": "css_gag #{userid} {minutes} {reason}",
  "ungag": "css_ungag {steamid} {reason}",
  "mute": "css_mute #{userid} {minutes} {reason}",
  "unmute": "css_unmute {steamid} {reason}",
  "silence": "css_silence #{userid} {minutes} {reason}",
  "team_t": "css_team #{userid} t",
  "team_ct": "css_team #{userid} ct",
  "team_spec": "css_team #{userid} spec"
}
```

If your `LOGZ_Admin` commands use another prefix, change only the config.

Example:

```json
"kick": "css_logz_kick #{userid} {reason}",
"ban": "css_logz_ban #{userid} {minutes} {reason}",
"gag": "css_logz_gag #{userid} {minutes} {reason}"
```

---

## version.txt

This plugin includes a `version.txt` file.

Recommended format:

```txt
1.0.3
https://github.com/USERNAME/LOGZ_AdminMenu
```

After creating your GitHub repository, replace `USERNAME` with your GitHub username or organization.

Example:

```txt
1.0.3
https://github.com/LOGZRomania/LOGZ_AdminMenu
```

Then update the config:

```json
"VersionUrl": "https://raw.githubusercontent.com/LOGZRomania/LOGZ_AdminMenu/main/version.txt"
```

---

## Reload Notes

In v1.0.3, `Config.Reload()` was removed because not all CounterStrikeSharp API versions support it.

For real reload, use:

```txt
css_plugins reload LOGZ_AdminMenu
```

The command:

```txt
css_logzadminmenu_reload
```

only prints the correct reload instruction.

This avoids the compile error:

```txt
CS1061: LOGZAdminMenuConfig does not contain a definition for Reload
```

---

## Known Requirements

This plugin expects the following commands to exist in `LOGZ_Admin`, depending on your config:

```txt
css_kick
css_ban
css_slay
css_respawn
css_gag
css_ungag
css_mute
css_unmute
css_silence
css_team
css_admins
css_logzadmin_reload
```

If your command names are different, edit `CommandTemplates` in the config.

---

## Recommended GitHub Structure

```txt
LOGZ_AdminMenu/
├── README.md
├── LICENSE.md
└── version.txt
```

---

## License

This project is licensed under the **LOGZ Romania Proprietary License**.

Redistribution, resale, reuploading, leaking, or claiming ownership of this plugin is not allowed.

See [LICENSE.md](LICENSE.md) for details.

---

## Credits

Created for **LOGZ Romania**.

Website:

```txt
https://www.logz.ro
```

