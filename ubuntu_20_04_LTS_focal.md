# Session startup

`.gnomerc` is sourced indirectly by `/etc/gdm3/Xsession`, when it sources all
files in `/etc/X11/Xsession.d`, specifically
`/etc/X11/Xsession.d/55gnome-session_gnomerc`.
