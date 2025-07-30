# BSPWM rice dotfiles 1

A minimal but sleek X11 rice using **bspwm**, **picom**, **polybar**, and **pywal** with a purple starry aesthetic. Designed to work without a display manager (no LightDM), and confirmed to work with AMD cards using the `amdgpu` driver.

For legal reasons, heres the link to the origianal wallpaper thats included https://4kwallpapers.com/cars/porsche-718-cayman-12180.html
Im new to git sothis is kinda like my learning thing aswell
---

## 🔧 Dependencies

Install the following packages:

```bash

sudo apt install feh bspwm sxhkd xorg xinit alacritty picom rofi polybar git curl unzip
```

Also install pywal with pipx (recommended)
```bash
pipx install pywal
```
Ensure pipx is set up in your shell
```bash
pipx ensurepath
```
Ensure you have the xinit package installed (assuming you aren't using a display manager eg. lightdm, gdm3, or sddm)

```bash
sudo apt install xinit
```
the start it with
```bash
startx
```

##Useful Notes

If startx is not starting or loading bspwm correctly, be sure to `exec bspwm` into your `.xinitrc` file

###Pywal not applying to new terminals?

Add this to your shell config (e.g. ~/.zshrc or ~/.bashrc)
```bash
[ -f "$HOME/.cache/wal/sequences" ] && cat "$HOME/.cache/wal/sequences"
```
