# Ubuntu22.04_wifiSolved

Collection of instructions tha may solve periodic wifi disconnecting problems of ubuntu 22.04.

## Uninstall and install again the wifi driver 

Ath10k_pci is the wireless adapter for Athereos wireless network adapter. Reloading the driver can be usufull to avoid connectivity problems.

* sudo cp ath10k-reload.service /etc/systemd/system . Copy both the files, "ath10k-reload.service" and "reload_ath10k.sh", present in the repository in /etc/systemd/system. The first file is a service, which means that every time the OS is started will perform the action indicated. The second file is a bash code that execute the 2 commands necessary for the reloading of the driver.
* sudo chmod +x reload_ath10k.sh . Make the bash file executable
* sudo systemctl daemon-reload
* sudo systemctl start ath10k-reload.service
* sudo systemctl enable ath10k-reload.service
* restart the system to verify the service works

## Disable the IPV6 address

It seems that disabling the ipv6 address of the wifi network speeds up the connection. To do so simply access the settings of the network.

## Edit the power management settings

nano /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf

Change
[connection]
wifi.powersave = 3

in

[connection]
wifi.powersave = 2

save and exit.



