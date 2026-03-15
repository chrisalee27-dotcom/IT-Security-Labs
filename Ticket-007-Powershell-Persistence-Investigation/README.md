# Ticket 006 — Suspicious Port Investigation

## Objective

Investigate filtered ports discovered during a network scan and determine whether a host firewall is preventing visibility of open services.

---

## Lab Environment

| Machine    | Role                    | IP Address     |
| ---------- | ----------------------- | -------------- |
| Kali Linux | Security Testing System | 192.168.56.101 |
| Windows 10 | Target Workstation      | 192.168.56.105 |

Network: **192.168.56.0/24**

---

## Step 1 — Initial Port Scan

A port scan was performed against the Windows workstation to identify accessible services.

Command used:

```
nmap -sT -p 135,139,445 192.168.56.105
```

Screenshot:
[View Screenshot](Screenshots/11_Ports_Filtered.png)

Observation:

The Nmap scan reported the ports as **filtered**, meaning the scanner could not determine whether the ports were open or closed. This behavior commonly indicates that a firewall or filtering device is blocking the scan results.

---

## Step 2 — Disable Windows Firewall for Testing

To verify whether the Windows firewall was responsible for filtering the scan results, the firewall was temporarily disabled on the Windows system.

Command used:

```
netsh advfirewall set allprofiles state off
```

Screenshot:
[View Screenshot](Screenshots/12_Disable_Firewall.png)

Observation:

The firewall was successfully disabled, allowing the port scan to be repeated without host-based filtering.

---

## Step 3 — Verify Port Availability

The port scan was performed again after disabling the firewall.

Command used:

```
nmap -sT -p 135,139,445 192.168.56.105
```

Screenshot:
[View Screenshot](Screenshots/13_Ports_Open.png)

Observation:

The ports were now reported as **open**, confirming that the Windows Defender Firewall was previously blocking the scan results.

---

## Tools Used

```
nmap
netsh
windows defender firewall
```

---

## Findings

The investigation determined that the Windows Defender Firewall was responsible for filtering inbound port scan attempts.

Key observations:

• Ports initially appeared **filtered** during the scan
• Disabling the firewall allowed the scan to identify open services
• Ports **135, 139, and 445** were confirmed open on the Windows host

These ports are associated with **Windows RPC and SMB services**.

---

## Skills Demonstrated

• Network scanning using Nmap
• Identifying filtered vs open ports
• Firewall troubleshooting
• Host-based security analysis

---

## Conclusion

The investigation confirmed that the Windows Defender Firewall was preventing Nmap from identifying open services during the initial scan. After disabling the firewall, the scan successfully revealed open ports on the Windows workstation within the lab network.

