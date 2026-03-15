# Ticket 003 — Port Scanning Investigation

## Objective

Identify open ports on systems within the virtual lab network and investigate the effect of firewall filtering on scan results.

---

# Lab Environment

| Machine        | Role                    | IP Address     |
| -------------- | ----------------------- | -------------- |
| Kali Linux     | Security Testing System | 192.168.56.101 |
| Metasploitable | Vulnerable Target       | 192.168.56.103 |
| Windows 10     | Workstation             | 192.168.56.105 |

Network: **192.168.56.0/24**

---

# Step 1 — Initial Port Scan

An initial Nmap scan was conducted against the Windows host to identify open services.

Command used:

```
nmap -sT -p 135,139,445 192.168.56.105
```

Screenshot:
[View Screenshot](Screenshots/11_Ports_Filtered.png)

Observation:

The scan results indicated that the ports were **filtered**, suggesting that a firewall or network filtering mechanism was preventing the scanner from determining the port state.

---

# Step 2 — Firewall Investigation

The Windows firewall configuration was reviewed and temporarily disabled to determine whether it was responsible for the filtered results.

Command used:

```
netsh advfirewall set allprofiles state off
```

Screenshot:
[View Screenshot](Screenshots/12_Disable_Firewall.png)

---

# Step 3 — Port Scan After Firewall Change

After disabling the firewall, the Nmap scan was repeated to determine whether port visibility changed.

Command used:

```
nmap -sT -p 135,139,445 192.168.56.105
```

Screenshot:
[View Screenshot](Screenshots/13_Ports_Open.png)

Observation:

The ports were now identified as **open**, confirming that the Windows firewall had been filtering the initial scan.

---

# Tools Used

```
nmap
netsh
```

---

# Findings

Initial scans indicated that several ports on the Windows system appeared **filtered**.

After disabling the Windows firewall, the same ports were successfully detected as **open**, confirming that the firewall was responsible for blocking the initial scan results.

Ports identified:

• TCP 135 — RPC
• TCP 139 — NetBIOS
• TCP 445 — SMB

---

# Skills Demonstrated

• Network port scanning
• Firewall troubleshooting
• Interpreting Nmap scan results
• Identifying filtered vs open ports
• Windows firewall management

---

# Conclusion

Port scanning revealed that the Windows firewall was filtering scan results during the initial investigation. Once the firewall was disabled, previously filtered ports became visible to the scanner. This demonstrates how host-based firewalls can impact network reconnaissance results.

