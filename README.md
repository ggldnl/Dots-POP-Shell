# GNOME + POP shell + Rofi + custom keybindings

<!-- ![sample](./images/sample.gif) markdown syntax only-->

<p align="center">
  <img src="./images/preview.gif" />
</p>

So I'm very lazy and rather than reinventing the wheel and configuring a desktop environment, a status bar, an application launcher and so on, this time I decided to give a shot to [pop shell](https://github.com/pop-os/shell) and it did not disappoint me. Pop Shell is a keyboard-driven layer for gnome shell.
There are a few bugs but the overall experience is really pleasing.
The only negative aspect is that gnome draws hell of a lot of RAM.

I changed a few keybindings and kept rofi as application launcher since the default one was not working for me.

To generate the file that holds all the keybindings (general procedure):
```
dconf dump / | sed -n -e '/\[org.gnome.desktop.wm.keybindings/,/^$/p' \
-e '/\[org.gnome.settings-daemon.plugins.media-keys/,/^$/p' > shortcuts.conf
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

You also have to add Rofi to the Floating Window Exception List (navbar) and make applications start in the center of the screen:
```
gsettings set org.gnome.mutter center-new-windows true
```

# Current keybindings

- close active window (`Alt+q`)

- switch to workspace 1 (`Alt+1`)
- switch to workspace 2 (`Alt+2`)
- switch to workspace 3 (`Alt+3`)
- switch to workspace 4 (`Alt+4`)
- switch to next workspace (`Alt+d`)
- switch to previous workspace (`Alt+a`)

- move window to workspace 1 (`Shift+Alt+1`)
- move window to workspace 2 (`Shift+Alt+2`)
- move window to workspace 3 (`Shift+Alt+3`)
- move window to workspace 4 (`Shift+Alt+4`)
- move window to next workspace (`Shift+Alt+d`)
- move window to previous workspace (`Shift+Alt+a`)

- switch to previous application (`Alt+Tab`)

- toggle minimized (`Alt+m`)

- change background (unsplash) (`Alt+b`)

- application launcher (`Alt+c`)

- launch terminal (`Alt+Return`)
