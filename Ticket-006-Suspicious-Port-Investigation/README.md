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
[View Screenshot](./Screenshots/11_Ports_Filtered.png)

Observation:

The scan indicated that the ports were **filtered**, meaning a firewall or filtering device was preventing Nmap from determining the port state.

---

# Step 2 — Disable Windows Firewall for Testing

To determine whether the host firewall was responsible for filtering the scan results, the Windows Defender Firewall was temporarily disabled.

Command used:

```
netsh advfirewall set allprofiles state off
```

Screenshot:
[View Screenshot](./Screenshots/12_Disable_Firewall.png)

Observation:

The firewall was successfully disabled, allowing the port scan to be repeated without host-based filtering.

---

# Step 3 — Verify Port Availability

After disabling the firewall, the port scan was performed again to verify whether the services were accessible.

Command used:

```
nmap -sT -p 135,139,445 192.168.56.105
```

Screenshot:
[View Screenshot](./Screenshots/13_Ports_Open.png)

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

The investigation determined that the Windows Defender Firewall was responsible for filtering inbound port scan attempts.

Key observations:

• Initial Nmap scan showed ports as **filtered**
• Disabling the firewall allowed the scan to identify services
• Ports **135, 139, and 445** were confirmed open on the Windows host

These ports are commonly associated with **Windows RPC and SMB services**.

---

# Skills Demonstrated

• Network scanning using Nmap
• Identifying filtered vs open ports
• Firewall troubleshooting
• Host security configuration analysis

---

# Conclusion

The investigation confirmed that the Windows Defender Firewall was preventing the initial Nmap scan from identifying open services. After disabling the firewall, the scan revealed that several Windows service ports were accessible within the lab network.

