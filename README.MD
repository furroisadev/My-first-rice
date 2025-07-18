Dotfiles You’d Need to Copy:

    ~/.config/bspwm/ — your bspwm config (bspwmrc and rules)

    ~/.config/sxhkd/ — your hotkey daemon config (sxhkdrc)

    ~/.config/picom/ — for blur, rounded corners, transparency

    ~/.config/polybar/ — your status bar configs & launch scripts

    ~/.config/wal/ — pywal cache & related scripts (optional but recommended)

    ~/.config/alacritty/ — terminal colors & config (to pick up pywal colors)

    ~/.xinitrc — to start bspwm when you run startx

    Shell config file (~/.bashrc or ~/.zshrc) — for pywal auto-color loading

    ~/.local/share/applications/spotify.desktop — so rofi can launch Spotify (if you want that)

🧰 Commands & Fixes You’d Run (in order)
1. Install essentials (adjust package manager as needed):

sudo apt install bspwm sxhkd picom rofi alacritty polybar feh x11-xserver-utils xinit python3-pywal

2. Set GPU driver fix for your R9 290X:

sudo nano /etc/default/grub
# Add to GRUB_CMDLINE_LINUX_DEFAULT:
# amdgpu.cik_support=1 radeon.cik_support=0
sudo update-grub

echo -e "blacklist radeon\noptions amdgpu cik_support=1\noptions radeon cik_support=0" | sudo tee /etc/modprobe.d/amdgpu.conf

sudo reboot

3. Setup ~/.xinitrc to launch bspwm:

echo 'exec bspwm' > ~/.xinitrc
chmod +x ~/.xinitrc

4. Add pywal color auto-load to shell config:

echo '[[ -f "$HOME/.cache/wal/sequences" ]] && cat "$HOME/.cache/wal/sequences"' >> ~/.bashrc
source ~/.bashrc

5. Create ~/.local/share/applications/spotify.desktop if you want Spotify in rofi:

mkdir -p ~/.local/share/applications
cat > ~/.local/share/applications/spotify.desktop <<EOF
[Desktop Entry]
Name=Spotify
Exec=spotify
Icon=spotify
Terminal=false
Type=Application
Categories=AudioVideo;Player;Music;
StartupNotify=true
EOF

chmod +x ~/.local/share/applications/spotify.desktop

6. Run startx to launch bspwm
7. After logging into bspwm, launch your bar (polybar) and compositor (picom):

~/.config/polybar/launch.sh &
picom &

Or add those lines to your bspwmrc to launch them automatically on session start.
Bonus: Set wallpaper and generate colors

wal -i ~/Pictures/Wallpapers/starfield.jpg

