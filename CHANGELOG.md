# Changelog

## Unreleased

- Uses the original Project Zomboid game icon.


## 0.1.3 - 2026-10-29


- Refreshes the README links, current WindowsGSM guidance and Steam credential compatibility notes.
- Uses the current canonical repository URL. Server runtime behavior is unchanged.


## 0.1.2 - 2026-10-22

- Removed plugin firewall cleanup and its startup block. Firewall management now follows WindowsGSM's per-server Auto Firewall setting.
- Updated setup and firewall notes for WindowsGSM builds with Auto Firewall.

## 0.1.1 — 2026-09-10

- Replaced the PowerShell `NetSecurity` firewall cleanup with the Windows Firewall COM API used by WindowsGSM itself.
- Removes WindowsGSM's automatic program exception for the exact bundled Project Zomboid `java.exe` path before the server starts.
- Verifies that the automatic exception is gone before allowing Java to launch.
- Keeps manually configured port rules unchanged.
- Avoids startup failures caused by unavailable or unreliable `Get-NetFirewall*` cmdlets.

## 0.1.0 — 2026-09-09

- Created the MeFriendos build based on WindowsGSM.ProjectZomboid 1.7.
- Added MeFriendos author, description, version and repository metadata.
- Removes WindowsGSM's broad automatic inbound rule for the exact bundled Project Zomboid `java.exe` at server start.
- Prevents server startup if the firewall safety check itself fails.
- Keeps manually configured port rules unchanged.
- Added matching PZ plugin and author artwork in the MeFriendos repository style.
- Added a complete GitHub README with installation, updating, security, troubleshooting and testing guidance.
