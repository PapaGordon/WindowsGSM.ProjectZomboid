<p align="center">
  <img src="ProjectZomboid.cs/ProjectZomboid.png" alt="Project Zomboid" width="128">
</p>

<h1 align="center">WindowsGSM.ProjectZomboid</h1>

<p align="center">
  Run a Project Zomboid dedicated server with WindowsGSM.
</p>

<p align="center">
  <a href="https://github.com/PapaGordon/WindowsGSM/releases/latest"><img src="https://img.shields.io/badge/WindowsGSM-MeFriendos%20latest-38CDD4" alt="Latest MeFriendos WindowsGSM"></a>
  <a href="CHANGELOG.md"><img src="https://img.shields.io/badge/version-0.1.3-EF3F28" alt="Version 0.1.3"></a>
  <a href="LICENSE"><img src="https://img.shields.io/badge/license-MIT-blue.svg" alt="MIT License"></a>
</p>

This plugin installs and updates the Project Zomboid dedicated server through SteamCMD and runs it from WindowsGSM. It's based on [WindowsGSM.ProjectZomboid](https://github.com/DoctorBeardz/WindowsGSM.ProjectZomboid) by Richard Beard.

**Using our [MeFriendos WindowsGSM](https://github.com/PapaGordon/WindowsGSM)?** Then you don't need this plugin. Project Zomboid is built in there, with the same code. Just pick **Project Zomboid Dedicated Server** under **Install**. This plugin is for other WindowsGSM builds.

## What it does

- Installs and updates the server (Steam app `380870`). No Steam account needed.
- Starts the server directly with the Java that comes with Project Zomboid. You don't need to install Java.
- Passes the game port from WindowsGSM to the server.
- Keeps configs and saves inside the server's WindowsGSM folder.
- Shows the server output in **Embed Console**, where you can also type server commands.
- Shuts the server down with CTRL+C.

## Install

1. Download the ZIP from the [latest release](https://github.com/PapaGordon/WindowsGSM.ProjectZomboid/releases/latest).
2. Copy the whole `ProjectZomboid.cs` folder into `<WindowsGSM>\plugins\`.
3. Click **Reload Plugins** or restart WindowsGSM.
4. Pick **Project Zomboid Dedicated Server** and click **Install**.
5. Start the server once. Project Zomboid asks for a new admin password in the console on the very first start. Type it into the WindowsGSM console (or the server window if Embed Console is off).
6. Stop the server and adjust the settings (see below).
7. Open the game ports in the Windows firewall and on your router.

## Settings

| | Default |
| --- | --- |
| Game port | `16261` (UDP). Passed to the server as `-port`. |
| Server name | `servertest`. Add `-servername <name>` to the start parameters for another name. |
| Memory | Always 16 GB, see below |

**Max Players** from WindowsGSM is not passed to the server. Set the player limit and everything else in the server's INI file.

Project Zomboid keeps its files in `servers\<server ID>\Zomboid` instead of your Windows user folder. The server settings are in `Zomboid\Server`:

- `<server name>.ini` for the server itself, like player limit, password, ports, RCON and mods
- `<server name>_SandboxVars.lua` for the game world settings

These files appear after the first start. Only edit them while the server is stopped.

### Memory

The server always starts with 16 GB of RAM (`-Xms16g -Xmx16g`). That's fixed in the plugin and can't be changed in WindowsGSM. If your machine has less free memory, the server won't start or will be slow. Then you'd have to change the two values in `ProjectZomboid.cs` yourself and reload the plugin.

## Updating

1. Stop the server.
2. Back up your save (`Zomboid\Saves`) and settings (`Zomboid\Server`).
3. Click **Update** in WindowsGSM.
4. Start the server and check the log.

The update only replaces the server files. Your saves, INI, sandbox settings and mod lists stay.

## Stopping

**Stop** sends CTRL+C, so Project Zomboid saves and closes, and waits 10 seconds for it. If CTRL+C can't be sent, the process is ended right away. Large worlds may need longer to save. Then use the `quit` command in the console first.

## Ports and firewall

The plugin doesn't create or remove firewall rules. Use WindowsGSM's **Auto Firewall** if your build has it, or open the ports yourself. Router port forwarding is always up to you.

Open the UDP ports your server INI uses for players. If you use RCON, keep its TCP port closed to the internet and only allow it from your local network or a VPN. On Windows that means: allow RCON only on the **Private** network profile and block it on **Public**.

## Troubleshooting

**The server doesn't start.** Check the error in WindowsGSM and the server log. If memory is the issue, see [Memory](#memory).

**There are no config files.** Start the server once so Project Zomboid creates them, then stop it before editing.

**Players can't connect.** Check that the UDP ports from your INI are open in the Windows firewall and forwarded on your router or at your hosting provider.

**RCON doesn't work over the VPN.** Check that the VPN network adapter uses the **Private** profile in Windows and that the RCON rule allows the right TCP port and network.

## Links

- [Releases](https://github.com/PapaGordon/WindowsGSM.ProjectZomboid/releases)
- [MeFriendos WindowsGSM](https://github.com/PapaGordon/WindowsGSM)
- [Original plugin by DoctorBeardz](https://github.com/DoctorBeardz/WindowsGSM.ProjectZomboid)
- [Project Zomboid](https://projectzomboid.com)
- [MeFriendos](https://mefriendos.de)

This is a community plugin. It's not affiliated with or endorsed by The Indie Stone or the WindowsGSM project.

## License

The original plugin and this version are under the [MIT License](LICENSE). The original copyright notice stays in it. You can use, change and share the plugin, also commercially, as long as the copyright and license notice stay with it.

The game icon is the original Steam artwork, converted to PNG. It has its own rights, see [artwork credits](licenses/Native-artwork.txt).
