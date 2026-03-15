# IT Security Labs

## Overview

This repository contains a series of **hands-on cybersecurity investigation labs** performed within a self-built virtual lab environment. Each lab is documented as an individual **IT/SOC investigation ticket**, replicating how incidents and troubleshooting tasks are handled in real security operations environments.

The goal of this project is to develop and demonstrate practical skills in:

* Network troubleshooting
* Security investigation
* Host analysis
* Incident documentation
* Security tooling and command-line investigation

Each ticket documents the **problem, investigation steps, tools used, findings, and conclusions**.

---

# Lab Environment

The lab environment was built using **VirtualBox** with three virtual machines connected through an isolated network.

| System         | Role                               | IP Address     |
| -------------- | ---------------------------------- | -------------- |
| Kali Linux     | Security testing / attacker system | 192.168.56.101 |
| Windows 10     | Target workstation                 | 192.168.56.105 |
| Metasploitable | Vulnerable target system           | 192.168.56.102 |

Network: **192.168.56.0/24**

This environment allows safe testing of:

* Network scanning
* Service enumeration
* Reverse shells
* Host investigation
* Firewall behavior
* Persistence techniques

---

# Investigation Workflow

Each lab follows a structured troubleshooting and investigation methodology similar to what is used in **SOC, NOC, and IT support environments**.

Typical workflow:

1. Identify the issue or suspicious activity
2. Gather system and network information
3. Investigate processes and connections
4. Analyze findings
5. Document results and conclusions

---

# Investigation Tickets

| Ticket     | Investigation                        |
| ---------- | ------------------------------------ |
| Ticket-001 | Virtual Network Troubleshooting      |
| Ticket-002 | Nmap Host Discovery                  |
| Ticket-003 | Port Scanning Investigation          |
| Ticket-004 | Reverse Shell Investigation          |
| Ticket-005 | Netstat Connection Analysis          |
| Ticket-006 | Suspicious Port Investigation        |
| Ticket-007 | PowerShell Persistence Investigation |

Each ticket contains:

* Investigation steps
* Commands used
* Screenshots of findings
* Analysis and conclusions

---

# Tools Used

```
nmap
netcat
netstat
powershell
tasklist
windows firewall
kali linux tools
virtualbox
```

---

# Skills Demonstrated

* Network troubleshooting
* Host discovery and enumeration
* Port scanning analysis
* Reverse shell investigation
* Firewall troubleshooting
* Process and connection analysis
* Security incident documentation

---

# Purpose

This repository serves as a **practical cybersecurity portfolio** demonstrating hands-on investigation skills for entry-level roles such as:

* Help Desk
* Network Operations Center (NOC)
* Security Operations Center (SOC)
* Junior Security Analyst

---

# Author

Christopher Lee

