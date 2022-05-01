# Simple-Ubuntu-Setup-For-Gaming
Simple Ubuntu Setup for Gaming
So in this tutorial we will be optimizing Ubuntu 22.04 for gaming and installing firefox properly
# Formatting the SSD/HDD properly before installing Ubuntu Linux or any other Linux distribution or operating system,use Live USB:
* sudo cfdisk /dev/sda 
* sudo cfdisk /dev/nvme0n1
* Delete everything you see then Write>>Yes
# Wipping the partition schemes 
* sudo wipefs -a /dev/sda
* sudo wipefs /dev/nvme0n1
# Deleting everything properly so no forencisc recovery is possible
* sudo shred -f -v /dev/sda
* sudo shred -f -v /nvme0n1
# Also this works but it does not show the process:
* sudo shred /dev/sda
* sudo shred /dev/nvme0n1

# 1.Installing Firefox-Developer-Edition (the best browser from Firefox so far) instead of the annoying snap version.
# Download the firefox*.tar.bz2 file from Mozilla’s website.https://www.mozilla.org/en-US/firefox/developer/
# Go into the Downloads folder,open terminal and copy firefox*.tar.bz2 file to the /opt folder.
*  sudo cp -rp firefox*.tar.bz2 /opt
# Delete the tar file from Downloads:
* sudo rm -rf firefox*.tar.bz2
# Go to the opt directory
* cd
* cd /opt
# Unpack the copied tar file
* sudo tar xjf firefox*.tar.bz2
# Delete the firefox tar file from opt folder:
* sudo rm -rf firefox*.tar.bz2
# Change ownership of the folder containing Firefox Developer Edition /opt/firefox
* sudo chown -R $USER /opt/firefox
# Create the Firefox Developer Edition shortcut:
*  nano ~/.local/share/applications/firefox_dev.desktop
# The content of the file should be all the lines below without the(*) in the beginning they are for github formating:
* [Desktop Entry]
* Name=Firefox Developer 
* GenericName=Firefox Developer Edition
* Exec=/opt/firefox/firefox %u
* Terminal=false
* Icon=/opt/firefox/browser/chrome/icons/default/default128.png
* Type=Application
* Categories=Application;Network;X-Developer;
* Comment=Firefox Developer Edition Web Browser.
* StartupWMClass=Firefox Developer Edition
# Ctrl+O to save,Ctrl+X to exit!
# Mark the Firefox Developer Edition launcher as trusted and make it executable.
* chmod +x ~/.local/share/applications/firefox_dev.desktop
# Remove the snap Firefox by using this command:
* sudo snap remove firefox
# 2.Install additions to NVIDIA drivers in the terminal:
 * sudo apt install vulkan-tools libvulkan-dev vulkan-validationlayers-dev vulkan-tools vulkan-validationlayers vulkan-validationlayers-dev
 * sudo apt update
 * sudo apt upgrade
# Or check for latest and greatest and install the full blown NVIDIA Driver package:
* sudo add-apt-repository ppa:graphics-drivers/ppa && sudo apt-get upgrade
* apt search nvidia-driver
* sudo apt install nvidia-driver-510 nvidia-settings vulkan-tools libvulkan-dev vulkan-validationlayers-dev vulkan-tools vulkan-validationlayers vulkan-validationlayers-dev
* sudo apt update
* sudo apt upgrade 
# 3.Install dependencies and apps like sdl2,mingw64,wine,additional,codecs x264,x265,libxvidcore4,flv,mpg123,ffmpeg:
* sudo apt install fizmo-sdl2 libsdl2-2.0-0 libsdl2-dev libsdl2-gfx-1.0-0 libsdl2-gfx-dev libsdl2-image-2.0-0 libsdl2-mixer-2.0-0 libsdl2-net-2.0-0
* sudo apt install mingw-w64 gcc-9-locales wine wine64 ffmpeg2theora flvmeta mencoder mjpegtools x265 x264 mpv mpg123 libxvidcore4 ffmpeg
* sudo apt update
* sudo apt upgrade
* sudo add-apt-repository multiverse
* sudo apt update
* sudo apt install ubuntu-restricted-extras
# 4. Install dxvk
* sudo apt install dxvk
* sudo apt update
* sudo apt upgrade
# 5. Install Lutris
* sudo apt install lutris
* sudo apt update
* sudo apt upgrade
# 6 Install flatpak
* sudo apt install flatpak
* sudo apt install gnome-software-plugin-flatpak
* flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

# 7.(Optional) Install optional apps like obs-studio,shotcut,celluloid,mpv,steam
* sudo apt install obs-studio shotcut mpv celluloid steam

# (Optional) Install Glourious Eggroll Proton GE the easy way:
 * Download the latest release here: https://github.com/GloriousEggroll/proton-ge-custom/releases
 * Extract,enable hidden files and folders 
 * Create a folder in your /home/user/config/.steam/root/compatibilitytools.d if it does not exist.
 * Copy/paste the extracted GE folder into /home/user/config/.steam/root/compatibilitytools.d
 * Restart Steam,enjoy the custom GE build
 
# 8.Install NVIDIA Shadowplay(same quality as Geforce Experience) with OBS-Studio on Linux Mint:
# Get nvidia-patch: https://github.com/keylase/nvidia-patch
# Extract and go to the folder
# Open in terminal
* sudo ./patch-fbc.sh
# Get obs-nvfbc: https://gitlab.com/fzwoch/obs-nvfbc
* Extract and go to folder
# Open in terminal 
* sudo apt-get install libgl-dev libobs-dev meson ninja-build
* meson build
* ninja -C build
# Go back to GUI and copy nvfbc.so
# Enable hidden files and fodlers in View>Show Hidden Files
# Launch OBS Studio at least once.
# Go to /home/user/.config/obs-studio
# NB!Create the following folders plugins->nvfbc->bin->64bit
# paste nvfbc.so into 64bit
# Go to OBS Studio and add the NvFBC Source to your scene
# Optional similar to mkinitcpio:
* sudo update-initramfs -u

That is it,you should be good for most use cases.Hope it helps!
#silentgamepls
