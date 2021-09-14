# Securities/packages update

```text
# https://linuxhint.com/install-security-updates-ubuntu/
# https://www.youtube.com/watch?v=a9s5NUIh42Q
# https://askubuntu.com/questions/194651/why-use-apt-get-upgrade-instead-of-apt-get-dist-upgrade

sudo apt update

#apt list --upgradable

# sudo apt-mark hold packagename  (this package won't be upgraded)
# sudo apt-mark unhold packagename  (cancelled the hold command above)
# sudo apt install packagename (it will upgrade a single package, if it already exists)
# upgrade all packages

sudo apt upgrade

#sudo apt distr-upgrade
#sudo apt autoremove

sudo reboot
```

