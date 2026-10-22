<p align="center">
  <img src="ProjectZomboid.cs/ProjectZomboid.png" alt="Project Zomboid" width="128">
</p>

<h1 align="center">WindowsGSM.ProjectZomboid</h1>

<p align="center">
  MeFriendos build for running a Project Zomboid dedicated server with WindowsGSM.
</p>

<p align="center">
  <a href="https://github.com/PapaGordon/WindowsGSM/releases/tag/v1.25.3.0"><img src="https://img.shields.io/badge/WindowsGSM-MeFriendos%20v1.25.3.0-38CDD4" alt="MeFriendos WindowsGSM v1.25.3.0"></a>
  <a href="CHANGELOG.md"><img src="https://img.shields.io/badge/version-0.1.2-EF3F28" alt="Version 0.1.2"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="MIT License"></a>
</p>

This plugin installs, updates and runs the Project Zomboid dedicated server through SteamCMD. The MeFriendos build is based on `WindowsGSM.ProjectZomboid` by Richard Beard and keeps its normal server behavior while leaving firewall management to WindowsGSM.

## Features

- Installs and updates the official dedicated server through SteamCMD.
- Starts the server with its bundled 64-bit Java runtime.
- Supports the embedded WindowsGSM console and graceful shutdown.
- Passes the configured WindowsGSM game port to Project Zomboid.
- Keeps the server configuration and saves inside the WindowsGSM server directory.
- Leaves firewall management to WindowsGSM's per-server **Auto Firewall** setting.
- Leaves targeted manual firewall rules unchanged.

## Quick overview

| Setting | Value |
| --- | --- |
| SteamCMD App ID | `380870` |
| Start executable | `jre64\bin\java.exe` |
| Default game/query port | `16261` |
| Installation method | Anonymous SteamCMD login |
| Server configuration | `Zomboid\Server` inside the WindowsGSM server directory |
| Firewall ports | WindowsGSM Auto Firewall or manual port rules |

## Requirements

MeFriendos uses this plugin with [WindowsGSM v1.25.3.0](https://github.com/PapaGordon/WindowsGSM/releases/tag/v1.25.3.0). The Windows x64 download includes the .NET runtime.

- [MeFriendos WindowsGSM v1.25.3.0](https://github.com/PapaGordon/WindowsGSM/releases/tag/v1.25.3.0) with per-server **Auto Firewall**
- Supported 64-bit Windows installation

Project Zomboid supplies its own Java runtime. A separate Java installation is not required.

## Plugin installation

1. Download the [latest release archive](https://github.com/PapaGordon/WindowsGSM.ProjectZomboid-MeFriendos/releases/latest).
2. Extract the complete `ProjectZomboid.cs` folder into `<WindowsGSM>\plugins\`.
3. Click **Reload Plugins** or restart WindowsGSM.
4. Add **Project Zomboid Dedicated Server** in WindowsGSM.
5. Click **Install** and wait for SteamCMD to finish.
6. Set **Auto Firewall** in WindowsGSM as needed. For manual game and RCON rules, turn it off first.
7. Start the server.

## Updating Project Zomboid

1. Stop the server.
2. Create a save backup.
3. Click **Update** in WindowsGSM.
4. Start the server and review the latest server log.

SteamCMD updates the dedicated-server files. The plugin does not intentionally modify your save, server INI, sandbox settings, mod list or Workshop list.

## Firewall

Firewall management follows WindowsGSM's per-server **Auto Firewall** setting. This plugin does not create, remove or inspect firewall rules and does not block startup for a plugin firewall check.

Use [MeFriendos WindowsGSM v1.25.3.0](https://github.com/PapaGordon/WindowsGSM/releases/tag/v1.25.3.0) with **Auto Firewall**. For the MeFriendos setup with manual port rules, turn **Auto Firewall** off for this server in WindowsGSM and configure the required ports yourself. Router forwarding remains separate.

For the MeFriendos setup, the intended manual policy is:

- Project Zomboid game traffic: required UDP ports on the **Public** profile.
- RCON: TCP on the **Private** profile for the VPN/local subnet only.
- RCON: blocked on the **Public** profile.

Adjust every port to match your WindowsGSM configuration and Project Zomboid server INI.

## Server files

Project Zomboid stores the server configuration and world data below:

```text
<WindowsGSM>\servers\<server ID>\Zomboid
```

Important server configuration files are normally found in:

```text
<WindowsGSM>\servers\<server ID>\Zomboid\Server
```

## Troubleshooting

### The server does not start after installing this build

Check the WindowsGSM error message and server log. Firewall settings are managed by WindowsGSM; this plugin no longer performs a firewall check during startup.

### Players cannot connect

Confirm that the required UDP ports are allowed by a targeted manual firewall rule and forwarded by the router or provider firewall when necessary. The plugin deliberately creates no automatic port rule.

### RCON is unavailable through the VPN

Confirm that the VPN adapter uses the **Private** Windows profile and that the RCON rule is limited to the correct TCP port and VPN/local subnet.

### The server configuration is missing

Start the dedicated server once so Project Zomboid can generate its default files, then stop it before editing the INI and sandbox settings.

## Testing checklist

- WindowsGSM loads `ProjectZomboid.cs` without a plugin error.
- Install and Update complete through SteamCMD.
- The embedded console receives Project Zomboid server output.
- The server is reachable through the manually configured game ports.
- Auto Firewall on/off is controlled by WindowsGSM and is not overridden by the plugin.
- Manually configured port rules remain present.
- RCON works over the Private VPN connection and remains unavailable publicly.

## Project links

- Source: [PapaGordon/WindowsGSM.ProjectZomboid-MeFriendos](https://github.com/PapaGordon/WindowsGSM.ProjectZomboid-MeFriendos)
- Original plugin: [DoctorBeardz/WindowsGSM.ProjectZomboid](https://github.com/DoctorBeardz/WindowsGSM.ProjectZomboid)
- Project Zomboid: [projectzomboid.com](https://projectzomboid.com)
- WindowsGSM: [MeFriendos WindowsGSM v1.25.3.0](https://github.com/PapaGordon/WindowsGSM/releases/tag/v1.25.3.0)
- Community: [mefriendos.de](https://mefriendos.de)

This is an independent community plugin. It is not affiliated with or endorsed by The Indie Stone or WindowsGSM.

## License

Maintained by Brandon Hanke (PapaGordon), owner of MeFriendos.de.

The original plugin and this MeFriendos build are released under the [MIT License](LICENSE). The original copyright and license notice are retained.

You can use, modify and redistribute this plugin, including commercially. Keep the copyright and license notices with any copies or substantial portions of the code.
