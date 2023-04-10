# Session startup

`.gnomerc` is sourced indirectly by `/etc/gdm3/Xsession`, when it sources all
files in `/etc/X11/Xsession.d`, specifically
`/etc/X11/Xsession.d/55gnome-session_gnomerc`.

# Gnome shell extensions

Extend functionality of GNOME Shell. The following package contains a few useful
extensions:

~~~
sudo apt install gnome-shell-extensions
~~~

Via <https://linuxhint.com/installing_gnome_extensions_ubuntu>:

> Gnome shell extensions can also be downloaded from its official website using a
> web browser. Open any web browser in your system and navigate to the following
> address:
>
> <https://extensions.gnome.org>
>
> To install Gnome shell extensions from your browser, you will need a browser
> extension (add-on). Hit **Click here to install browser extension**.

## Unite

<https://extensions.gnome.org/extension/1287/unite/>

> *Unite is a GNOME Shell extension which makes a few layout tweaks to the top*
> *panel and removes window decorations to make it look like Ubuntu Unity Shell.*

## Permanent notifications

<https://extensions.gnome.org/extension/41/permanent-notifications/>

Keep notifications on the message tray until clicked.

<https://askubuntu.com/a/1325739>

## Panel Date Format

<https://extensions.gnome.org/extension/3465/panel-date-format/>

Allows for customizing of the date format on the panel.

<https://askubuntu.com/a/1345588>

## Vitals

<https://extensions.gnome.org/extension/1460/vitals/>

> *A glimpse into your computer's temperature, voltage, fan speed, memory usage,*
> *processor load, system resources, network speed and storage stats. This is a one*
> *stop shop to monitor all of your vital sensors. Uses asynchronous polling to*
> *provide a smooth user experience.*


## AATWS - Advanced Alt-Tab Window Switcher

<https://extensions.gnome.org/extension/4412/advanced-alttab-window-switcher/>

> Highly customizable replacement for the Alt/Super+Tab window/app switchers
> that offers 'type to search' mode, various filtering and sorting options,
> workspace and monitor navigation, configurable hotkeys for navigation and
> window/app control and an app launcher.

# Gnome tweaks

Tool to adjust advanced configuration settings for GNOME, including extensions.

~~~
sudo apt install gnome-tweaks
~~~

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

Or you may pin only release `linuxmint` and install Google Chromium like this:

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

# Screenkey: key cast your keys

It's best to get straight from the official repository:

<https://gitlab.com/screenkey/screenkey>

It comes with a `.desktop` file (in the `data` folder). Copy that to
`~/.local/share/applications` and set _Exec_ to the full path of the `screenkey`
script.

# Media keys slow/delayed on Ubuntu Gnome 3

Open `/usr/share/X11/xkb/symbols/br` and comment the line:

~~~
    modifier_map Mod3   { Scroll_Lock };
~~~

Run:

```
setxkbmap br
```

<https://askubuntu.com/a/1072160>

# Automatically connect to VPN

<https://askubuntu.com/a/1401042>

[This
page](https://manpages.debian.org/testing/network-manager/nm-settings.5.en.html)
says that you can't use autoconnect with VPN profiles, but `secondaries` can be
used instead.

List all existing connections:

```
ls -lh /etc/NetworkManager/system-connections/
```

Get the `uuid` of the corresponding VPN connection (my-VPN in my case):

```
sudo grep uuid /etc/NetworkManager/system-connections/my-VPN
```

Then copy `uuid`. It should look like this `5a9bde6f-54ge-4h41-8754-f1a2977fa564`.

Open your Wi-fi connection file:

```
sudo -e /etc/NetworkManager/system-connections/My-Wi-Fi
```

And add `secondaries` property with copied `uuid`. It should look like this:

```
[connection]
id=My-Wi-Fi
uuid=1ab56231-9401-48c7-82de-a9ffghtyeac4
type=wifi
interface-name=wlo1
permissions=
secondaries=5a9bde6f-54ge-4h41-8754-f1a2977fa564;
timestamp=1649182910

[wifi]
...
```

After that restart NetworkManager or your computer:

```
sudo systemctl restart NetworkManager
```
