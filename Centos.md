### To Install Graphical Display
```
# yum groupinstall "GNOME Desktop" "Graphical Administration Tools"
# ln -sf /lib/systemd/system/runlevel5.target /etc/systemd/system/default.target
# reboot
```
### Screen Commands
```
# screen --> To invoke screen
# screen -ls --> See the list of screens running
# Ctrl + a + d --> detach from a screen
# screen -r <screenname> --> Attach back to a screen.
````
