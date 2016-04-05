Running the pacman-mirrors -g Command to Update the Mirrorlist:
sudo pacman-mirrors -g
sudo pacman-mirrors -i -c all (interactive Mode)

Pacman:
1.Updating the System
sudo pacman -Syu

2.Synchronising with the Manjaro Repositories
sudo pacman -Syy
sudo pacman -Syyu (simultaneously)

3.Searching for Software Packages
Searching the Manjaro Repositories:
pacman -Ss [software package name]

Searching Your System:
pacman -Qs [software package name]
pacman -Qi [software package name]
pacman -Qii [software package name]
pacman -Ql

4.Downloading and Installing Software Packages
Packages from the Manjaro Repositories:
sudo pacman -S [software package name]
sudo pacman -Sw [software package name] (without actually installing)

Packages from the AUR (Arch User Repository):
yaourt -S [software package name]

Packages Located Locally or From the Internet:
sudo pacman -U [/package_path/][software package name.pkg.tar.xz]
sudo pacman -U ~/Downloads/[software package name.pkg.tar.xz]

5.Removing Applications and Software Packages
sudo pacman -R [software package name]

6.Cleaning the Cache
sudo pacman -Sc  (To clear the cache of downloads that have already been installed)
sudo pacman -Scc (to clear the cache completely)



Accessing the AUR:
sudo pacman -S base-devel yaourt

Searching for and Installing Software From the AUR:
yaourt [software package name]
yaourt -S [software package name]

Upgrading the packages installed from the AUR:
yaourt -Syua



Install NVIDIA Drivers:
sudo mhwd -a pci nonfree 0300
sudo reboot
mhwd -li
Configure The Resolution/Refresh Rate:
1. Open your terminal and enter the following command:
sudo nvidia-settings

2. Change resolution and refresh rate in 'X Server Display Configuration' tab.
3. Hit the 'Save to X Configuration File' button and save to /etc/X11/mhwd.d/nvidia.conf
4. Now enter the following command into the terminal to complete the process:
sudo mhwd-gpu --setgl nvidia --setxorg /etc/X11/mhwd.d/nvidia.conf





Bumblebee and Steam:
1. Install bumblebee for nonfree nvidia. Please run in terminal command in proper order:
sudo pacman -S virtualgl lib32-virtualgl lib32-primus primus
sudo mhwd -f -i pci video-hybrid-intel-nvidia-bumblebee
sudo systemctl enable bumblebeed
2. Reboot system:
sudo reboot
3. Next run:
optirun -b none nvidia-settings -c :8
4. Verify it is working
primusrun glxspheres64
and
glxspheres64
so you can see the difference.
5a. To have all games with Steam run using the NVidia card. Run Steam with command:
primusrun steam
5b. Alternatively, you can run specific games by:
Select a game - that you want to run using your discrete Nvidia card - from the Library page of the Steam client, right-click, and select Properties. Click the SET LAUNCH OPTIONS... button and specify primusrun %command% for the command line. Save your changes.This method allows you to pick when the discrete NVidia GPU should be used on a per-game basis.


lspci | grep VGA

Install Vmware on Archlinux:
For the System service scripts directory, use /etc/init.d (the default).
To (re)build the modules from terminal later on, use:
# vmware-modconfig --console --install-all
