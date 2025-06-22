# tshark Cheat Sheet
Quick reference for tshark commands.

## Basic commands
- `tshark -i <interface> -c <number> -w <output_file>`

- `tshark -r <file>` : read file .pcap
  - `-V` : detail information

- `T` : type
  - `tshark -r <.pcap> -T fields -e <ip.src> -e <ip.dst>` : export data to field 
  - `-T json` : export data to json
  - `-T pdml` : export data to pdml (detail xml)
  - `-T psml` : export data to psml (summary)
  - `-T text` : default text like wireshark

- `tshark -i <interface> -f "filter" <.pcap>` : capture filter 
  - `-f "arp"` : capture arp traffic (layer 2) 
  - `-f "tcp"` : capture tcp traffic (layer 1)
  - `-f "icmp"` : capture icmp traffic (like ping) (layer 3)
  - `-f "port 21"` : capture traffic on port 21 
  - `-f "tcp port 80 or tcp port 443"` : capture tcp traffic on port 80 or port 443 (HTTP or HTTPS) (layer 4)
  - `-f "tcp port 445"` : capture traffic SMB on port 445 (layer 5)
  - `-f "src port 53"` : capture traffic on source port 53 (DNS response) (layer 7)
  - `-f "udp port 5060"` : capture udp traffic on port 5060 (SIP or VoIP) (layer 7)
  - `-f dst net <IP/CIDR>` : capture traffic to network range IP/CIDR

- `-Y "display_filter"` : filter
  - `tshark -r <.pcap> -Y "display_filter"`
  - `-Y "smb.server_version == 1"` : detect SMBv1 (layer 5)
  - `-Y "ssl.record.version == 0x0002"` : filter weak SSLv2 (layer 6)
  - `-Y "ssl.record.version == 0x0300"` : filter weak SSLv3 (layer 6)
  - `-Y "ssl.record.version == 0x0301"` : filter weak TLS 1.0 (layer 6)
  - `-Y "ssl.record.version == 0x0302"` : filter weak TLS 1.1 (layer 6) 
  - `-Y "tcp.port == 80"` : filter packet tcp on port 80 (layer 4)
  - `-Y "http.request.method == \"GET\""` : filter packet http with GET method (layer 7)
  - `-Y "tcp.flags.syn == 1 && tcp.flags.ack == 0"` : filter packet tcp syn, a sign of port scanning (layer 4)
  - `-Y "http contains \"password\""` : filter packet http contains "password" (layer 7)
  - `tshark -r <.pcap> -Y "arp" -T fields -e <arp.src.proto_ipv4> -e <arp.src.hw_mac> | sort | uniq -c > arp_check.txt` : check arp spoofing (layer 2)
  - `tshark -r <.pcap> -Y "arp" -T fields -e <eth.src> -e <eth.dst> > mac_list.txt` : export source and destination mac (layer 2)
  - `tshark -r <.pcap> -Y "sip.Method == \"INVITE\"" -T fields -e <sip.from> -e <sip.to>` : filter packet SIP INVITE (layer 7) 

## Advanced commands

- `tshark -r <.pcap> -q -z io,phs` : Protocol Hierarchy Statistics

- `tshark -r <.pcap> -q -z conv,tcp` : Statistics of 2 IPs talking over TCP

- `tshark -r <.pcap> -q -z endpoints,ip` : List IPs appearing in pcap file

- `tshark -r <.pcap> -o ssl.keys_list:"<ip>,<port>,<protocol>,<keyfile>"` : SSL/TLS Decryption

- `tshark -r <file.pcap> -Y "http.content_type" -T fields -e http.file_data` : Automatically dump file data sent via HTTP (layer 7)

- `tshark -i eth0 -b filesize:5000 -b files:10 -w capture` : ring buffer - When the file reaches 5MB, it will rotate, maximum 10 files

- `timeout 60s tshark -i eth0 -w capture.pcap` : stop after 60s