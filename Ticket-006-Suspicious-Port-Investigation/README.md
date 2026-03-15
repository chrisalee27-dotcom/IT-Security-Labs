# Ticket 006 — Suspicious Port Investigation

## Objective

Investigate filtered ports discovered during a network scan and determine whether a host firewall is preventing visibility of open services.

---

# Lab Environment

| Machine    | Role                    | IP Address     |
| ---------- | ----------------------- | -------------- |
| Kali Linux | Security Testing System | 192.168.56.101 |
| Windows 10 | Target Workstation      | 192.168.56.105 |

Network: **192.168.56.0/24**

---

# Step 1 — Initial Port Scan

A port scan was performed against the Windows workstation to identify accessible services.

Command used:

```
nmap -sT -p 135,139,445 192.168.56.105
```

Screenshot:
[View Screenshot](Screenshots/11_Ports_Filtered.png)

Observation:

The scan results indicated that the ports were **filtered**, suggesting that a firewall or filtering mechanism was blocking the scan.

---

# Step 2 — Disable Windows Firewall for Testing

To verify whether the firewall was responsible for filtering the scan results, the Windows Defender Firewall was temporarily disabled.

Command used:

```
netsh advfirewall set allprofiles state off
```

Screenshot:
[View Screenshot](Screenshots/12_Disable_Firewall.png)

Observation:

The firewall was successfully disabled, allowing the port scan to be repeated without host-based filtering.

---

# Step 3 — Verify Port Availability

The port scan was performed again after disabling the firewall.

Command used:

```
nmap -sT -p 135,139,445 192.168.56.105
```

Screenshot:
[View Screenshot](Screenshots/13_Ports_Open.png)

Observation:

The ports were now reported as **open**, confirming that the Windows firewall had previously been filtering the scan results.

---

# Tools Used

```
nmap
windows firewall
netsh
```

---

# Findings

The investigation determined that the Windows Defender Firewall was responsible for filtering inbound scan attempts.

Key observations:

• Ports initially appeared **filtered**
• Disabling the firewall allowed the scan to detect open services
• Ports **135, 139, and 445** were confirmed open

These ports are associated with **Windows RPC and SMB services**.

---

# Skills Demonstrated

• Network scanning with Nmap
• Firewall troubleshooting
• Identifying filtered vs open ports
• Host-based security investigation

---

# Conclusion

The investigation confirmed that the Windows Defender Firewall was preventing the initial Nmap scan from identifying open services. Once the firewall was disabled, the scan revealed that the services were accessible within the lab network.

