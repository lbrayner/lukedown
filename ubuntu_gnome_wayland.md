Ubuntu 20.04 LTS Focal

# Setting Wayland session environment variables

<https://www.reddit.com/r/archlinux/comments/d119v0/comment/ezkg4vn/?utm_source=share&utm_medium=web2x&context=3>

> It is popular among sway users to simply set environment variables in their
> shell profile before sway is launched, but for a login-shell agnostic
> solution, `pam_env` should work. It will read `/etc/environment` and
> `$HOME/.pam_environment` by default. See `pam_env(8)` for details.

# Wayland Firefox

Add `MOZ_ENABLE_WAYLAND=1` to `~/.pam_environment`.

# Wayland Chromium

Set **Preferred Ozone platform** to "Auto" or "Wayland" on `chrome://flags`.
