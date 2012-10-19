Raspian remixed to match Turnkey Linux Core 12.0. GUI packages extirpated (prolly still room to shrink).

Add to the server Core Adafruit's WebIDE and you have a server appliance fashioned after Turnkey Linux 12.0.

Assumptions:
1. You've used raspi-config to configure Raspian with SSH on start and without X on start.
2. You've created a password for root with sudo passwd root.
3. You've logged all other users out and are now logged in as root.

Features:
Shellinabox web access to terminal on port 12320 (Turnkey Linux style)
Webmin and modules configured; root account synced; access on port 12321 (Turnkey Linux style) (Webmin modules match those in the Turnkey Linux 12 manifest.
Adafruit-WebIDE configured as a service and listening on port 80.
Confconole: If your server has a head, confconsole tells you what is being served where (TKL style)
Inithooks: Resets or sets root password on first boot.

Method:
Conservatively purges packages that are obviously serving the purposes of LXDE. There's more to strip that I haven't been brave enough to puge out.

Installs packages from TurnKey Linux Core 12.0 manifest (in some cases, the closest match) and dependencies.

