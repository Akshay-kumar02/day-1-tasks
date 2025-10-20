# day-1
# Task 1 — Local Network Port Scan (Kali Linux)

## Overview
Scanned local network `192.168.1.0/24` using Nmap (TCP SYN scan). Goal: identify open ports and potential service exposure.

## Tools
- Kali Linux
- Nmap
- Wireshark / tcpdump (optional)

## Commands run
- `sudo nmap -sS -T4 --open -p- 192.168.1.0/24 -oN results/nmap_full_tcp_syn.txt`
- `sudo nmap -sS -sV -A -p 22,80,443 192.168.1.25 -oN results/nmap_192.168.1.25_sv.txt`
- `sudo tcpdump -i wlan0 host 192.168.1.25 -w results/capture_192.168.1.25.pcap`

## Findings (summary)
- 192.168.1.12 — ports: 22 (ssh) — OpenSSH 7.x — Risk: weak passwords possible.
- 192.168.1.25 — ports: 80 (http), 443 (https) — Apache/2.4.29 — Risk: outdated version (investigate CVEs).

*(Full details in `results/scan_report.md` and raw outputs in `results/`.)*

## How to reproduce
1. Clone repo
2. Run the commands in the Commands section (adjust IP range for your network)
3. Review outputs in `results/`

## Notes & Ethics
Only scanned devices I own / have permission to test.
