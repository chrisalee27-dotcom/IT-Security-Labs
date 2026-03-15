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

The scan indicated that the ports were **filtered**, meaning that a firewall or filtering device was blocking the scan results.

---

# Step 2 — Disable Windows Firewall for Testing

To determine if the firewall was responsible for blocking the ports, the Windows Defender Firewall was temporarily disabled.

Command used:

```
netsh advfirewall set allprofiles state off
```

Screenshot:
[View Screenshot](Screenshots/12_Disable_Firewall.png)

Observation:

The firewall was successfully disabled, allowing the network scan to be repeated without filtering.

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

The scan now showed the ports as **open**, confirming that the firewall was responsible for filtering the scan results.

---

# Tools Used

```
nmap
windows firewall
netsh
```

---

# Findings

The investigation determined that the Windows Defender Firewall was filtering inbound scan attempts.

Key observations:

• Ports initially appeared filtered
• Disabling the firewall exposed the open services
• The host firewall was responsible for the filtered scan results

---

# Skills Demonstrated

• Network scanning with Nmap
• Firewall troubleshooting
• Identifying filtered vs open ports
• Host-based security analysis

---

# Conclusion

The investigation confirmed that the Windows Defender Firewall was preventing Nmap from identifying open services on the host. After disabling the firewall, the scan revealed that the ports were open and accessible within the lab network.

