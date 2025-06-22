# Masscan Cheat Sheet
Quick reference for masscan commands.
Masscan for High-Speed Network Scanning.

## Basic commands

- `masscan <target IP> -p <port(s)>` : Scanning a single host

- `masscan <start IP>-<end IP> -p <port(s)>` : Scanning a range of IP addresses

- `masscan <target> -p <port-range> -oG output.txt` : Saving the results to a file

- `masscan -iL <file> -p <port(s)>` : Specifying the network interface

- `masscan <target IP> -p <port(s)> -oX <output.xml>` : Outputting results to a file

- `masscan -i <interface> <target IP> -p <port(s)>` : Using a Specific Network Interface

## Advance commands

- `masscan <target> -p <port-range> --rate <packets-per-second> --output-format <format> --output-file <output-file>`

- `masscan <target IP> -p <port(s)> --rate <packets per second>` : Set the rate at which packets are sent per second (e.g., 10000)

- `masscan <target_IP/CIDR> --top-ports --adapter-ip <adapter_IP> --rate 10000` : Scan all ports on LAN

- **Firewall Evasion Techniques**
  - `masscan <target_IP/CIDR> -p 1-1000 --fragment` : Send fragmented packets
  
  - `masscan <target_IP> -p 1-1000 --spoof-mac <MAC_ADDRESS>` : Spoof the MAC address of the scanning interface

  - `masscan 192.168.0.0/24 -p 1-1000 --source-ip 10.0.0.2` : shit option 
