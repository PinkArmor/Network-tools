# sslscan Cheat Sheet
Quick reference for sslscan commands.

## Protocols and their ports
- `HTTPS` : 443
- `FTPS (Implicit)` : 990 (File transfer protocol to SSL)
- `FTPS (Explicit)` : 21 (auth TLS)
- `SMTPS` : 465 (SMTP sending mail via SSL)
- `POP3S` : 995 (POP receiving mail via SSL)
- `IMAPS` : 993 (IMAP receiving mail via SSL)
- `LDAPS` : 636 (LDAP to SSL domain, AD)
- `RDP (TLS)` : 3389 (Remote Desktop Protocol)
- `Custom SSL services` : 8443, 9443, ...

## Basic commands

- `sslscan <IP:port>`

- `sslscan --xml-output=result.xml --no-failed --color --show-certificate example.com` : Enhanced Scan with XML Output

- `sslscan --heartbleed example.com` : Heartbleed Vulnerability Check

- `sslscan --starttls-smtp example.com` : StartTLS Testing for SMTP

- `sslscan --cipher-details example.com` : Cipher Suite Details

## Advance commands

- `sslscan --xml-output=result.xml --no-failed --color --show-certificate --starttls-smtp --heartbleed example.com` : Advanced Scan with Detailed Output