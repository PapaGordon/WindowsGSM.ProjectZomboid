VERSION 0.1.2

WindowsGSM.ProjectZomboid - MeFriendos build
================================================

Installation
------------
1. Copy the complete ProjectZomboid.cs folder into the WindowsGSM plugins folder.
2. Reload plugins or restart WindowsGSM.
3. Add or import the Project Zomboid server.
4. Configure the required game and RCON ports manually in Windows Firewall.

Firewall behavior
-----------------
Firewall management follows WindowsGSM's per-server Auto Firewall setting.
The plugin does not create, remove or inspect firewall rules and does not block startup for a plugin firewall check.

Use MeFriendos WindowsGSM v1.25.3.0 with Auto Firewall:
https://github.com/PapaGordon/WindowsGSM/releases/tag/v1.25.3.0
For manual port rules, turn Auto Firewall off for this server in WindowsGSM and configure the required ports yourself. Router forwarding remains separate.

MeFriendos setup
----------------
- Game UDP ports: Public profile
- RCON TCP port: Private profile, VPN/local subnet only
- RCON TCP port: blocked on Public

Use the ports configured for your own server.

Credits
-------
Based on WindowsGSM.ProjectZomboid by Richard Beard.
MeFriendos build by PapaGordon / MeFriendos.

https://github.com/PapaGordon/WindowsGSM.ProjectZomboid-MeFriendos
https://mefriendos.de
