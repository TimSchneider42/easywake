# etherwake2

Tool to create magic packets that does not require sudo for installation and execution. 

## Installation

First, configure wake-on-lan on the machine you want to wake up:

1. Install `ethtool` via `sudo apt install ethtool`

2. Enable wake-on-lan persistently. This requires you to copy the file `wol.service` of this repository to `/etc/systemd/system/wol.service` and replace "eth0" inside of this file with the name of your network interface. You can obtain this name by running `ip addr`. Enable the WOL service via 
```bash 
sudo systemctl daemon-reload
sudo systemctl enable wol
sudo systemctl start wol
```

Second, download the etherwake2 script on the machine you want to use for waking up the first machine:

```bash
wget --no-check-certificate https://raw.githubusercontent.com/TimSchneider42/etherwake2/master/etherwake2
chmod a+x etherwake2
```

## Usage

To wake your machine up, call

```bash
./etherwake2 [MAC ADDRESS] [IP ADDRESS]
```
where you replace [MAC ADDRESS] and [IP ADDRESS] with the MAC address and IP address of the machine you want to wake up. For example:

```bash
./etherwake2 DE:AD:00:BE:EF:42 192.168.0.42
```
