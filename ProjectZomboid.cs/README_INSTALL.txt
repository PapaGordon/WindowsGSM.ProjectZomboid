WindowsGSM.ProjectZomboid 0.1.3
===============================

Runs a Project Zomboid dedicated server with WindowsGSM.

If you use MeFriendos WindowsGSM, you don't need this plugin.
Project Zomboid is already built in there.

Install
-------
1. Copy this whole ProjectZomboid.cs folder into the "plugins" folder
   of WindowsGSM.
2. Click "Reload Plugins" or restart WindowsGSM.
3. Pick "Project Zomboid Dedicated Server" and click Install.
   No Steam account needed.
4. Start the server once and enter a new admin password in the console.
5. Stop it and edit the settings in servers\<server ID>\Zomboid\Server.

Good to know
------------
- The server always starts with 16 GB RAM (-Xms16g -Xmx16g in ProjectZomboid.cs).
- Max Players from WindowsGSM isn't used. Set the limit in the server INI.
- The plugin doesn't change firewall rules. Open the game UDP ports and keep
  RCON closed to the internet (local network or VPN only).

Full guide: https://github.com/PapaGordon/WindowsGSM.ProjectZomboid

Based on WindowsGSM.ProjectZomboid by Richard Beard.
MeFriendos build by PapaGordon. https://mefriendos.de
