## Ubuntu WiFi Script | *script.sh*

This script runs when you place the script.sh file in the directory that Ubuntu is in. This is meant for server versions of Ubuntu. This can create/edit network-config (with your wifi information) and enable ssh (creates a file called ssh)

---

#### Features:

Functions that the script can do are:
- Create/edit a file with your network information.
- Enable SSH on startup.
- Self-destruct when finished.

---

#### Script. (**MUST CALL THE SCRIPT: *script.sh***)

```
#/bin/bash

echo "This script auto enters the network information for your HOME wifi."
echo "Do not share your WiFi information with anyone."
echo "This script doesn't collect any information and you are free to edit it."
echo "This script only works in UBUNTU."
echo "This script may also enable ssh if you want it to."

# lines
echo "


"
echo "This script only works when you place the script in the directory in which you want the files to be created."
echo "Do you wish to continue the script?"
read -p "Type Y or N:" accept
if [ $accept == Y ]
then
clear
echo "Starting."


# wifi information
# wifi ssid
echo "What is the SSID?"
read -p "Type the SSID:" ssid
echo "

"
echo "SSID is $ssid"

# wifi password
echo "What is the password for $ssid?"
read -s -p "Type the password:" password
echo "
"
# directory information
# this isn't meant to be used however you can use it as you wish.
# echo "Where is the directory where you have UBUNTU installed?"
# read -p "Enter the directory here:" directory

# line
#echo "
#"

# file edit
echo "Editing network-config."
echo "

"
# This deletes network-config, then creates a new file with the information.

sudo rm -rf network-config

echo "wifis:
  wlan0:
  dhcp4: true
  optional: true
  access-points:
    \"$ssid\":
      password: \"$password\"" >> network-config

# ssh enable?

echo "Do you want to enable ssh?"
read -p "Type Y or N:" ssh_ask

if [ $ssh_ask == Y ]
then
echo "" >> ssh
else
echo "Not enabling SSH on startup."
fi

else
# exited the script.
echo "Exited."
fi

echo "Do you want to destory the script?"
echo "The script must be called script.sh."
read -p "Type Y or N:" kill

if [ $kill == Y ]
then
rm -rf script.sh
else
fi
```

### Issues

If you have any issues please DM on Discord Biune#0001 or create an issue.
