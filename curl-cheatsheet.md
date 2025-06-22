# cURL Cheat Sheet
Quick reference for cURL commands.

- `curl [options] [URL]`

## Command options

### Test web/form
- `-x <host:port>` : proxy
- `-X "METHOD"` : custom method
- `-O` or `-o <file>` : output
- `-d "string"` or `-d @file` : POST
- `--data-urlencode "[name]=val"` : POST encode
- `-T <file>` : PUT
- `-F name=value` or `-F name=@file` : multipart formpost
### Auth/Session
- `-u user:passwd` : basic auth
- `-b <file>` : read cookiejar
- `-c <file>` : write cookiejar
- `-b "c=1; d=2"`: send cookie
### Recon
- `-A "string"` : user-agent
- `-k` : insecure HTTPS
- `-I` : head
- `-s` : hide progress
- `-w "format"` : extra info
- `-m <secs>` : timeout
- `-v` : verbose

## Basic commands

- `curl http://example.com` : send GET request

- `curl -O http://example.com/file.txt` : download file

- `curl -s -o /dev/null -w "%{http_code}" http://example.com` : silent GET + status code

- `curl -I http://example.com` : HEAD request 

- `curl -A "Mozilla/5.0 (ReconBot)" http://example.com` : fake user-agent

- `curl -k https://example.com` : insecure HTTPS

- `curl -s -I -A "ReconPi" -m 5 -w "%{http_code}\n" http://example.com` : stealth recon