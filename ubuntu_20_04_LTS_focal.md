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

# Latest Google Chromium as a package (not a snap)

[How to install Chromium from the Linux Mint repositories in Ubuntu?](https://askubuntu.com/a/1386740)

## Linux Mint 20.3 Una

> Create an apt source file for the Mint repository:
> 
> ~~~
> echo "deb http://packages.linuxmint.com una upstream" | sudo tee /etc/apt/sources.list.d/mint-una.list
> ~~~
> 
> To prevent NO\_PUBKEY you have to add the GPG key:
> 
> ~~~
> sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A1715D88E1DF1F24 40976EAF437D05B5 3B4FE6ACC0B21F32 A6616109451BBBF2
> ~~~
> 
> Then update package lists:
> 
> ~~~
> sudo apt update
> ~~~
> 
> Prevent installation of other packages with a pin-file:
> 
> ~~~
> cat <<EOF | sudo tee /etc/apt/preferences.d/pin-chromium
> Package: *
> Pin: release o=linuxmint
> Pin-Priority: -1
> 
> Package: chromium
> Pin: release o=linuxmint
> Pin-Priority: 1000
> EOF
> ~~~
> 
> Install chromium:
> 
> ~~~
> sudo apt install chromium
> ~~~

Or you may pin only release `linuxmint` and install Google Chromium it like this:

~~~
sudo apt install -t linuxmint chromium
~~~

The resulting pin file:

```
Package: *
Pin: release o=linuxmint
Pin-Priority: -1

# vim: ft=conf
```
