Notes: install script needs to be run to compile tklpatch; it's intended to then launch the patch process. Until tonight, that part is broken. After running the install script, manually apply the patch:
1. cd to location of webide.tar.gz
2. enter: tklpatch-apply / webide.tar.gz

Raspian remixed to match Turnkey Linux Core 12.0. GUI packages extirpated (prolly still room to shrink).


Add to the server Core Adafruit's WebIDE and you have a server appliance fashioned after Turnkey Linux 12.0.

Assumptions:
1. You've used raspi-config to configure Raspian with SSH on start and without X on start.
2. You've created a password for root with sudo passwd root.
3. You've logged all other users out and are now logged in as root.
4. You're using a fresh sd card with Raspian written to it. It's running on a raspi.

Features:
Shellinabox web access to terminal on port 12320 (Turnkey Linux style)
Webmin and modules configured; root account synced; access on port 12321 (Turnkey Linux style) (Webmin modules match those in the Turnkey Linux 12 manifest.
Adafruit-WebIDE configured as a service and listening on port 80.
Confconole: If your server has a head, confconsole tells you what is being served where (TKL style)
Inithooks: Resets or sets root password on first boot.

Method:
Conservatively purges packages that are obviously serving the purposes of LXDE. There's more to strip that I haven't been brave enough to puge out.

Installs packages from TurnKey Linux Core 12.0 manifest (in some cases, the closest match) and dependencies.

To Use:
1. Login as root.
2. git cone; apt-get install git. git clone git://github.com/ghoulmann/Adafruit-WebIDE-Appliance.git
3. Run install_tklpatch.sh script. This script compiles TKLPatch, Turnkey Linux's SDK. At the end of the script, the patch process is launched.
4. If you've compiled tklpatch and want to apply the patch manually, here's the command: tklpatch-apply / webide.tar.gz
5. Wait. Quite a while. The output is verbose so you'll know what's keeping you.
6. Reboot: shutdown -r now
7. Certicates are refreshed on first boot and you're prompted for a root password.

Notes
Unlike TKL Core, sudo package is maintained solely because Adafruit's WebIDE depends on it.
License needs commited.
Shellinabox cannot be accessed by root: this is a problem to be fixed.
There are three python modules in /usr/bin that belong someplace else; however, the code that relies on these modules (confconsole IIRC) doesn't work when the files are placed in a more appropriate directory. This needs fixed.

To Do
License, Credits
List of Webmin Modules
Fix poorly placed python modules.
Make shellinabox accessible by root.
Revise based on feedback.
