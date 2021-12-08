# Unfreeze UI

```
# https://stackoverflow.com/questions/38878883/ubuntu-16-04-screen-completely-freezes-only-mouse-moves
1. Open the GRUB configuration

sudo vi /etc/default/grub
2. Change the value of GRUB_CMDLINE_LINUX_DEFAULT from "quiet splash" to

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_idle.max_cstate=1"
and save the file.

3. Update & Reboot

sudo update-grub
sudo reboot
```

```
# https://askubuntu.com/questions/1199236/ubuntu-19-10-freeze-the-sidebar-and-top-bar-until-restart
# as a temporary remedy instead killall gnome panel try Alt+F2 dialogue box will open then type r and hit enter key

1) Alt+F2
2) r
3) Enter


```

