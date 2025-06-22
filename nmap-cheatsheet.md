# Nmap Cheat Sheet
Quick reference for Nmap commands.

## Basic scans
- `nmap -sV -A -O <target_IP>`  
  - `-A` : (OS detection, Version detection, NSE scripts, Traceroute)

- `nmap -F <target_IP>` : fast 100 ports scan

- `nmap -p <port> <target_IP>` : scan port specification or port range

- `nmap -top-ports 2000 <target_IP>` : scan 2000 popular ports 

- `nmap -sn -PR <target_IP/CIDR>` : hosts discovery

- `nmap -sC <target_IP>` : default NSE scripts

- `nmap -iL <target.txt>` : scan targets from file

- `nmap -exclude <IP>` : exclude this host 

- `nmap -oX <output.xml> <target_IP>` : export xml file

## Advanced scans

- `sudo nmap -sV -O -p<ports> --script=default,vuln <target_IP\CIDR>` : Nmap – Recon & Vuln Scan

- `sudo nmap -sS -n --min-parallelism 50 192.168.1.0/24` : Performance Boost

- `nmap -sS --top-ports 100 <target_IP/CIDR> -oG lan_ports.txt` : grepable output

- `nmap --spoof-mac <MAC> <target_IP>` : MAC spoofing (convert MAC address '-' to ':')

- `sudo nmap -sS -T4 -Pn 10.0.0.0/16` : Large Network Handling 

- **Bypassing firewall , IDS , SIEM:**
  - `nmap -T2 <target_IP>` : Timing Template - Polite
  - `nmap -D RND:5 <target_IP>` : Decoy Scan
  - `nmap -f <target_IP>` : break packet into smaller fragments making it harder for firewall to understand and analyze
  - `nmap -sS -f <target_IP>` : stealth SYN scan with packet fragmentation
  
> Note: Combining multiple stealth techniques can bypass detection but may slow down scans.



