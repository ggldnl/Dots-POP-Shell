# GNOME + POP shell + rofi + custom keybindings

So I'm very lazy and rather than reinventing the wheel and configuring a desktop environment, a status bar, an application launcher and so on, this time I decided to give a shot to [pop shell](https://github.com/pop-os/shell) and it did not disappoint me.
There are a few bugs but the overall experience is really pleasing.

I changed a few keybindings and kept rofi as application launcher since the default one was not working for me.

To generate the file that holds all the keybindings (general procedure):
```
dconf dump / | sed -n -e '/\[org.gnome.desktop.wm.keybindings/,/^$/p' -e '/\[org.gnome.settings-daemon.plugins.media-keys/,/^$/p' >> shortcuts.conf
```

[reference](https://askubuntu.com/questions/26056/where-are-gnome-keyboard-shortcuts-stored)

To restore this configuration place all the folders inside `.config`. Clone the code for [styli.sh](https://github.com/thevinter/styli.sh) inside the same folder:

```
cd ~/.config && git clone https://github.com/thevinter/styli.sh.git stylish
```

To import the keybindings:
```
dconf load / < ~/.config/dconf/shortcuts.conf
```