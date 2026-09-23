# Nmap

Nmap (Network Mapper) is a free open source tool used to scan networks. It's one of the first things you run when you're doing recon on a target — it tells you what ports are open, what services are running, and can even give you OS information.

---

## Why It Matters

Before you can attack or defend anything you need to know what's actually there. Nmap answers that. Open ports = potential attack surface. Knowing what's running on a machine is step one of literally everything in pentesting and security work.

---

## Commands

`nmap <ip>` — basic scan, checks the 1000 most common ports

`nmap -sV <ip>` — version detection, tells you what software is actually running on each port

`nmap -A <ip>` — aggressive scan, grabs OS info, versions, runs scripts. Noisy but thorough

`nmap -p- <ip>` — scans all 65535 ports. Slower but you won't miss anything hiding on a weird port

`nmap -sC <ip>` — runs default NSE scripts, useful for grabbing extra info automatically

`nmap -p 80,443,22 <ip>` — scan specific ports only

`sudo nmap -sS <ip>` — SYN scan (stealth scan), faster and less likely to show in logs. Needs root

`nmap -oN output.txt <ip>` — saves results to a file, useful habit to get into

---

## Common Ports Worth Knowing

| Port | Service | Why It Matters |
|------|---------|----------------|
| 21 | FTP | File transfers, often misconfigured |
| 22 | SSH | Remote access |
| 23 | Telnet | Old, unencrypted, big red flag if open |
| 25 | SMTP | Email |
| 80 | HTTP | Web server |
| 443 | HTTPS | Encrypted web |
| 445 | SMB | Windows file sharing, common attack target |
| 3306 | MySQL | Database |
| 3389 | RDP | Remote desktop, Windows |

---

## Things That Caught Me Out

Running without sudo gives incomplete results on certain scan types — always use sudo when you can

Scanning all ports with -p- takes ages on a slow connection, be patient

-A is loud, in a real engagement you wouldn't just blast this at a target without thinking

---

## Scan States

Nmap will tell you a port is open, closed, or filtered. Filtered usually means a firewall is blocking it which is itself useful information.

---

## Resources

- nmap.org/book — the actual Nmap documentation, genuinely useful
- TryHackMe Nmap room — good hands on intro
