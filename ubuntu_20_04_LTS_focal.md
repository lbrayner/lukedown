# Session startup

`.gnomerc` is sourced indirectly by `/etc/gdm3/Xsession`, when it sources all
files in `/etc/X11/Xsession.d`, specifically
`/etc/X11/Xsession.d/55gnome-session_gnomerc`.

# Gnome shell extensions

Extend functionality of GNOME Shell.

~~~
sudo apt install gnome-shell-extensions
~~~

## Gnome tweaks

<https://askubuntu.com/a/1325739>

Tool to adjust advanced configuration settings for GNOME.

~~~
sudo apt install gnome-tweaks
~~~

## Permanent notifications

Keep notifications on the message tray until clicked.

<https://extensions.gnome.org/extension/41/permanent-notifications/>
