## Newly-Linux-802.11n-CSI-toolkit

The purpose of this repository is to provide support for building the CSI-enabled TP-Link AC1750 Wi-Fi drivers for Intel Wireless Link Intel 5300 NIC adapters on Linux distributions with Unbuntu 14.01 versions. At this point this code has been tested on Ubuntu 14.01 and 16.04.

The code presented here comprises of a modified version of the Linux kernel, such as NIC firmware command, and fixed error line of the baseline. The modifications were made by examining the code provided by [dhalperi/linux-80211n-csitool](https://github.com/dhalperi/linux-80211n-csitool) and adapting them to more recent Linux kernel versions "- iwlwifi" and "wlp1s0" modules. The building and installation instructions were taken from [the original Linux 802.11n CSI Tool website](https://dhalperi.github.io/linux-80211n-csitool/) and adapted accordingly.
