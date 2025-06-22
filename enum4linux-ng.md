# enum4linux-ng Cheat Sheet
Quick reference for enum4linux-ng commands.
Reconnaissance SMB and Windows Domain.

## Command options

- `-A` : full enum modules
- `-u <user>` : username
- `-p <password>` : password
- `-d <domain>` : domain name
- `-oJ <file>` : Json format
- `-v` : verbose
- `--no-pass` : anonymous login
- `-q` : quite
  
## Basic commands

- `enum4linux-ng -A --no-pass <IP>`

- `enum4linux-ng -oJ output.json -A <IP>`
