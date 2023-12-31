# Newly-Linux-802.11n-CSI-toolkit

* This repository is a part of an RF-based mobility detection and tracking project.
  
The purpose of this repository is to provide support for building the CSI-enabled **TP-Link AC1750** Wi-Fi drivers for Intel Wireless Link **Intel 5300 NIC** adapters on Linux distributions with **Unbuntu 14.01** versions. At this point this code has been tested on Ubuntu 14.01 and 16.04.

The code presented here comprises of a modified version of the Linux kernel, such as the firmware command, and error lines of the original baseline. The modifications were made by examining the code provided by [dhalperi/linux-80211n-csitool](https://github.com/dhalperi/linux-80211n-csitool) and adapting them to more recent Linux kernel versions **- iwlwifi** and **wlp1s0** modules. The building and installation instructions were taken from [the original Linux 802.11n CSI Tool website](https://dhalperi.github.io/linux-80211n-csitool/) and adapted accordingly.

# Contributors and Project Members
### Youngwoo Oh (Master's student, Project Leader from May 2023 to Feb. 2024) 
- developer of RF and Camera sensor fusion and HW configuration.

### Islam Helemy (Ph.D. student, Project Member)
- Responsible for the development of the Multi-modal AI and the preprocessing of RF signals and camera sensors.

### Iftikhar Ahmad (Ph.D. student, Project Member)
- Focused on developing the Teacher network in the multi-modal AI model and optimizing the neural network.

### Manal Mosharaf (Master's student, Project Member)
- Engaged in developing the Student network in the multi-modal AI model and optimizing the neural network.

### Jungtae Kang (Undergraduate student, Contributor)
- Supporting the generation of CSI samples and Camera images.

# Installation Instructions
## 1. Kernel version:
Before proceeding further, you need to check the version of your kernel. It should be **4.15**, otherwise the commands below won't work. The following command will print that information:

```ruby
$ uname -r
```

# Utilization Instructions
## 1.:
```ruby
$ iw dev wlp1s0 link
```

## 2.:
```ruby
$ make -C linux-80211n-csitool-supplementary/netlink
```

## 3.:
```ruby
$ sudo modprobe -r iwlwifi mac80211
```
```ruby
$ sudo modprobe iwlwifi connector_log=0x1
```

## 4.:
```ruby
$ sudo ls /sys/kernel/debug/ieee80211/phy0/netdev:wlp1s0/stations/
```

## 5.:
```ruby
$ sudo cat /sys/kernel/debug/ieee80211/phy0/netdev:wlp1s0/stations/XX:XX:XX:XX:XX:XX/rate_scale_table
```

## 6.:
```ruby
$ echo 0x8009 | sudo tee /sys/kernel/debug/ieee80211/phy0/netdev:wlp1s0/stations/XX:XX:XX:XX:XX:XX/rate_scale_table
```
```ruby
$ echo 0x8009 | sudo tee /sys/kernel/debug/ieee80211/phy0/iwlwifi/iwldvm/debug/bcast_tx_rate
```
```ruby
$ echo 0x8009 | sudo tee /sys/kernel/debug/ieee80211/phy0/iwlwifi/iwldvm/debug/monitor_tx_rate
```

## 7.:
```ruby
$ sudo dhclient wlp1s0
```

## 8.:
```ruby
$ sudo linux-80211n-csitool-supplementary/netlink/newly_syn_log_to_file file_name.dat
```

## 9.:
```ruby
$ ping XXX.XXX.X.XX
```
