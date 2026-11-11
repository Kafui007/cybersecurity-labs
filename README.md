# Cybersecurity Labs

Hands-on cybersecurity coursework: vulnerability scanning, reconnaissance, exploitation
of a lab target, password cracking, phishing simulation, and incident-response planning.

All offensive labs were run in an isolated home lab — Kali Linux on VirtualBox against
Metasploitable, a deliberately vulnerable virtual machine — or against public
reconnaissance targets. The phishing exercise was a controlled simulation with
participants who were briefed about the experiment. Nothing here was run against a
real system without permission.

## Labs

| # | Lab | Tools | What it covers |
|---|-----|-------|----------------|
| 01 | [Vulnerability scan with Nessus](labs/01-nessus-vulnerability-scan.md) | Nessus Essentials, Nmap, Kali, VirtualBox | Installing Nessus, scanning Metasploitable, reading a 70-finding report |
| 02 | [Subdomain enumeration](labs/02-subdomain-enumeration.md) | Sublist3r, Maltego, Netcraft | Mapping bbc.com subdomains three ways |
| 03 | [Wayback Machine](labs/03-wayback-machine.md) | web.archive.org | Reading archived versions of a website |
| 04 | [Connecting to a LAN via Wi-Fi](labs/04-wifi-lan-connection.md) | Kali | Joining a local network over Wi-Fi |
| 05 | [Privilege escalation on Metasploitable](labs/05-privilege-escalation-metasploitable.md) | Nmap, Metasploit, Hydra | FTP, SSH, Telnet and SMB exploitation to root / Meterpreter |
| 06 | [Password cracking with John the Ripper](labs/06-password-cracking-john-the-ripper.md) | John the Ripper, OpenSSL | Hashing a password and cracking it |
| 07 | [Simulated phishing attack](labs/07-simulated-phishing-attack.md) | CamPhish, ngrok | Running a controlled phishing simulation — and how to stop real ones |
| 08 | [Data breach response plan](labs/08-data-breach-response-plan.md) | — | A full incident-response plan framework |
| 09 | [WEP vs WPA vs WPA2 vs WPA3](labs/09-wifi-security-wep-wpa-wpa2-wpa3.md) | — | How Wi-Fi security evolved, and why WPA3 wins |

## Lab environment

- **Attacker:** Kali Linux virtual machine ("learning") on VirtualBox
- **Target:** Metasploitable 2 virtual machine at `192.168.100.9` (lab subnet `192.168.100.0/24`)
- **Scanner:** Tenable Nessus Essentials (free)

## About

Coursework labs by Shaker — IT Support Specialist working toward CompTIA Security+.
Google IT Support and Google Cybersecurity Professional Certificates.
