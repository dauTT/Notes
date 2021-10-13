# Brave

### downgrade version

{% embed url="https://community.brave.com/t/how-to-revert-to-earlier-version-of-brave-for-linux/99490/8" %}

```
# https://community.brave.com/t/how-to-revert-to-earlier-version-of-brave-for-linux/99490/8
# If you have synaptic installed on your system, here is what should work.
# Launch synaptic (you will probably be prompted for your password)
# Click on Search and search for brave - you should find brave-browser
# Click on the brave-browser entry
# On the menu select Package and then Force version…
# From the dialog presented you can pick from the available versions. 1.0.1 should be listed
# Click on Force Version which will close the dialog.
# On the menu click Apply, answer Apply on the dialog which comes up and the old package will be downloaded and installed in place of the defective version
# Finally select the brave-browser line in the list, Click Package on the menu and select Lock version. That will hold brave at 1.0.1 until you uncheck Lock version.
# Those are the steps in synaptic on Linux Mint. The steps should be the same on Kubuntu.
# Let us know if that works.


# If you do not have synaptic you can install it from a command line (terminal)
# sudo apt-get update
# sudo apt-get install synaptic

```

### Run a specific version of brave

```
# https://www.addictivetips.com/ubuntu-linux-tips/install-brave-browser-on-linux/
# Go to the release  page: https://github.com/brave/brave-browser/releases
# chose a version 

wget https://github.com/brave/brave-browser/releases/download/v1.27.111/brave-browser-1.27.111-linux-amd64.zip && unzip brave-browser-1.27.111-linux-amd64.zip
cd ~/brave-browser-1.27.111-linux-amd64

# run brave locally
./brave'
```
