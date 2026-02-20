Pacstrap Install:
base linux linux-firmware sof-firmware sudo vim man-db man-pages intel-ucode

Chroot Installs:
zram-generator limine efibootmgr base-devel git networkmanager pipewire pipewire-pulse wireplumber mesa swayidle greetd greetd-regreet
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
