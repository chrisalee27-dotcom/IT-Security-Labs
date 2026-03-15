# Ticket 006 — Suspicious Port Investigation

## Objective

Investigate filtered ports discovered during a network scan and determine whether a host firewall is preventing visibility of open services.

---

## Lab Environment

| Machine | Role | IP Address |
|--------|------|-----------|
| Kali Linux | Security Testing System | 192.168.56.101 |
| Windows 10 | Target Workstation | 192.168.56.105 |

Network: **192.168.56.0/24**

---

## Step 1 — Initial Port Scan

A port scan was performed against the Windows workstation to identify accessible services.

Command used:

```text
nmap -sT -p 135,139,445 192.168.56.105

The investigation confirmed that the Windows Defender Firewall was preventing the initial Nmap scan from identifying open services. Once the firewall was disabled, the scan revealed that the services were accessible within the lab network.

