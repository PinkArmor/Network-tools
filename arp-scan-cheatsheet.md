# arp-scan Cheat Sheet
Quick reference for arp-scan commands.

## Basic commands

- `sudo arp-scan --interface=eth0 <target_IP/CIDR>`

- `sudo arp-scan --interface=eth0 --ouifile=/usr/share/arp-scan/ieee-oui.txt --macfile=/etc/arp-scan/mac-vendor.txt <target_IP/CIDR>`

- `sudo arp-scan --interface=eth0 <target_IP/CIDR> > output.txt`

- `sudo arp-scan --interface=eth0 --timeout=100 <target_IP/CIDR>`