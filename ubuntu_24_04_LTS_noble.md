# Disable Super+N shortcuts (switch to application)

<https://askubuntu.com/a/968110>

This will disable the **Dash to Dock** extension hotkeys:

```
gsettings set org.gnome.shell.extensions.dash-to-dock hot-keys false
```

And this will clear the Gnome default shortcuts for those combos:

```
for i in {1..9}; do gsettings set "org.gnome.shell.keybindings" \
  "switch-to-application-$i" "[]"; done
```

# Gnome shell extensions

Extend functionality of GNOME Shell. The following package contains a few useful
extensions:

~~~
sudo apt install gnome-shell-extensions
~~~

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

## Wayland Google Chrome/Chromium

Set **Preferred Ozone platform** to "Auto" or "Wayland" on `chrome://flags`.
