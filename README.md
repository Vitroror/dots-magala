# dots-magala

Personal dotfiles for my Linux desktop running the Hyprland window manager.

## What's Included

### Window Manager and Compositor

- **Hyprland** -- dynamic tiling Wayland compositor
- **hyprlock** -- lockscreen
- **hyprpaper** -- wallpaper setter for Hyprland.

### Status Bar

- **waybar** -- top bar with modules

### Notifications

- **swaync** -- notification center

### Application Launcher

- **rofi** -- fullscreen application launcher

### Logout Screen

- **wlogout** -- overlay with buttons for lock, logout, restart, and shutdown.

### Terminal

- **kitty** -- terminal emulator.

### Shell

- **fish** -- shell

### Text Editor

- **neovim** -- editor configured with lazy.nvim plugin manager

### Audio

- **cava** -- terminal-based audio visualizer
- **pipewire / wireplumber** -- audio server and session manager.
- **pamixer / libpulse** -- audio control tools.
- **playerctl** -- media player control (play, pause, next, previous) via keyboard multimedia keys.

### File Manager

- **thunar** -- graphical file manager.

### Bluetooth

- **blueman** -- Bluetooth manager with applet and manager GUI.

### Network

- **networkmanager** -- network connection management.

### System Tools

- **btop** -- system resource monitor (CPU, memory, disks, network, processes).
- **lm_sensors** -- hardware temperature monitoring.
- **hyprshot** -- screenshot tool
- **kvantum** -- Qt theme engine.
- **nwg-look** -- GTK settings manager for wayland.

### Theme and Icons

- **materia-gtk-theme** -- GTK theme (Materia-dark-compact).
- **papirus-icon-theme** / **nordzy-icon-theme** -- icon themes.
- **ttf-font-awesome** / **ttf-jetbrains-mono-nerd** / **ttf-fira-code-nerd** / **ttf-geist-mono-nerd** -- icon and monospace fonts.

### Browser

- **zen-browser-bin** -- the Zen Browser (from AUR).

---

## How to Use the Install Script

The `install.sh` script installs all required packages and copies the dotfiles into `~/.config/`. It is designed for Arch Linux systems and uses `yay` as the AUR helper.

### Prerequisites

- Arch Linux (or an Arch-based distribution)
- An internet connection
- `sudo` access

### Steps

1.  Open a terminal and clone the repository:

    ```
    git clone <repository-url>
    cd dots-gm
    ```

2.  Make the install script executable:

    ```
    chmod +x install.sh
    ```

3.  Run the script:

    ```
    ./install.sh
    ```

### What the script does, step by step

1.  Checks whether `git` and `base-devel` are installed. If not, installs them with pacman.
2.  Checks whether `yay` (the AUR helper) is installed. If not, clones the yay repository from AUR, builds it, and installs it.
3.  Installs every package in the list using `yay -S --needed`. This includes both official Arch packages and AUR packages (zen-browser-bin, nordzy-icon-theme, ttf-geist-mono-nerd).
4.  Creates a timestamped backup folder at `~/.config_backup_<date>`.
5.  For each configuration folder listed in the script, moves any existing folder in `~/.config/` to the backup directory, then copies the new configuration from the `dotconfig/` folder.
6.  Applies the Materia-dark-compact GTK theme and Nordzy-dark icon theme system-wide via `gsettings`.
7.  Changes the default login shell to Fish if it is not already the current shell.
8.  Prints a completion message and suggests rebooting the system.

### After running

- Reboot your computer or log out and back in for all changes to take effect.
- All your previous configurations are saved in the backup folder created during the install.
- You can delete the cloned repository if you no longer need it.
