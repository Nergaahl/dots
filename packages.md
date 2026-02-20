Pacstrap Install:

base linux linux-firmware sof-firmware sudo vim man-db man-pages intel-ucode

Chroot Installs:

zram-generator limine efibootmgr base-devel git networkmanager pipewire pipewire-pulse wireplumber mesa swayidle greetd greetd-regreet polkit-gnome

  configure limine
  
  configure zram-generator
  
  systemctl enable NetworkManager

Setting up yay - /home/user

git clone "https://aur.archlinux.org/yay.git"

cd yay

makepkg -si

pacman: alacritty niri pcmanfm/thunar quickshell ttf-jetbrains-mono-nerd xdg-desktop-portal-wlr xdg-desktop-portal-gtk vivaldi nwg-look font-manager btop fastfetch hyfetch featherpad

yay: noctalia-shell

First Boot:

  systemctl start /dev/zram0
  
  systemctl enablde greetd.service

Potential niri config changes:

spawn-at-startup "/usr/lib/polkit-gnome/polkit-gnome-authentication-agent-1"

spawn-at-startup "dbus-update-activation-environment" "--systemd" "WAYLAND_DISPLAY" "XDG_CURRENT_DESKTOP"

spawn-at-startup "swayidle" "-w" \
    "timeout" "300" "qs -c noctalia-shell ipc call lockScreen lock" \
    "timeout" "600" "niri msg action power-off-monitors" \
    "resume" "niri msg action power-on-monitors" \
    "before-sleep" "qs -c noctalia-shell ipc call lockScreen lock"
