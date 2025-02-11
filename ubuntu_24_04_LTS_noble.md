# Disable Super+N shortcuts (switch to application)

<https://askubuntu.com/a/968110>

This will disable the **Dash to Dock** extension hotkeys:

```bash
gsettings set org.gnome.shell.extensions.dash-to-dock hot-keys false
```

And this will clear the Gnome default shortcuts for those combos:

```bash
for i in {1..9}; do gsettings set "org.gnome.shell.keybindings" \
  "switch-to-application-$i" "[]"; done
```

# Move Window to Center shortcut

<https://www.reddit.com/r/gnome/comments/1f68p1w/manually_centering_a_window_via_shortcut_in_gnome/>

```bash
gsettings set org.gnome.desktop.wm.keybindings move-to-center "['<Super>c']"
```

# Gnome shell extensions

Extend functionality of GNOME Shell. The following package contains a few useful
extensions:

```bash
sudo apt install gnome-shell-extensions
```

## Activate Window By Title

<https://extensions.gnome.org/extension/5021/activate-window-by-title>

> Expose a D-Bus interface to activate a window by its title, WM_CLASS or ID.

Leverage its power with <https://github.com/lbrayner/shell_scripts/blob/master/activate>.

## Panel Date Format

<https://extensions.gnome.org/extension/1462/panel-date-format/>

Allows to customize the date format on the panel. Follow extension homepage link
to changing format instruction.

<https://github.com/KEIII/gnome-shell-panel-date-format>

```bash
dconf write /org/gnome/shell/extensions/panel-date-format/format "'%b %e  %a  %k:%M'"
```

## Switcher

<https://extensions.gnome.org/extension/973/switcher/>

> Use the configured global hotkey (Super+w by default) to open a list of
> current windows. Type a part of the name or title of the application window
> you want to activate and hit enter or click on the item you wish to activate.

# Wayland

## Setting Wayland session environment variables

<https://www.reddit.com/r/archlinux/comments/d119v0/comment/ezkg4vn/?utm_source=share&utm_medium=web2x&context=3>

> It is popular among sway users to simply set environment variables in their
> shell profile before sway is launched, but for a login-shell agnostic
> solution, `pam_env` should work. It will read `/etc/environment` and
> `$HOME/.pam_environment` by default. See `pam_env(8)` for details.

## Wayland Firefox

Add `MOZ_ENABLE_WAYLAND=1` to `~/.pam_environment`.

## Wayland Google Chrome, Chromium, Brave Browser

Set **Preferred Ozone platform** to "Wayland" on `chrome://flags`.

## Region and Language

Gnome Settings is still buggy, does not do a good job at setting a different
language for the user vs. the system default language.

User custom locale can be defined with environment variables in
`~/.pam_environment`.

```
LANGUAGE	DEFAULT=en_US:en
LANG	DEFAULT=en_US.UTF-8
LC_NUMERIC	DEFAULT=en_US.UTF-8
LC_TIME	DEFAULT=en_US.UTF-8
LC_MONETARY	DEFAULT=en_US.UTF-8
LC_PAPER	DEFAULT=en_US.UTF-8
LC_NAME	DEFAULT=en_US.UTF-8
LC_ADDRESS	DEFAULT=en_US.UTF-8
LC_TELEPHONE	DEFAULT=en_US.UTF-8
LC_MEASUREMENT	DEFAULT=en_US.UTF-8
LC_IDENTIFICATION	DEFAULT=en_US.UTF-8
PAPERSIZE	DEFAULT=a4
```

# Bugs

## Slow shutdown

[[SOLVED] Mint 22 very slow shutdown with external display - Linux Mint
Forums](https://forums.linuxmint.com/viewtopic.php?t=436668)

> It is possible because your computer is so new that it might work better with
> the 6.11-oem kernel. You can install the latest 6.11-oem kernel with:

```bash
sudo apt-get install linux-oem-24.04b
```
