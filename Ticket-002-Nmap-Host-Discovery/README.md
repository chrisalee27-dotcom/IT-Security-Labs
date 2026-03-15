# Ticket 002 — Nmap Host Discovery

## Objective

Identify active hosts within the virtual lab network using Nmap host discovery techniques.

---

# Lab Environment

| Machine        | Role                    | IP Address     |
| -------------- | ----------------------- | -------------- |
| Kali Linux     | Security Testing System | 192.168.56.101 |
| Metasploitable | Vulnerable Target       | 192.168.56.103 |
| Windows 10     | Workstation             | 192.168.56.105 |

Network: **192.168.56.0/24**

---

# Step 1 — Perform Host Discovery Scan

A ping sweep was performed across the subnet to identify active hosts.

Command used:

```
nmap -sn 192.168.56.0/24
```

Screenshot:
[View Screenshot](Screenshots/01_Nmap_Host_Discovery.png)

---

# Step 2 — Identify Live Systems

The scan identified multiple active hosts within the network.

Typical output shows:

```
Host is up
MAC Address
Device type
```

Screenshot:
[View Screenshot](Screenshots/02_Discovered_Hosts.png)

---

# Tools Used

```
nmap
```

---

# Findings

The Nmap host discovery scan successfully identified active systems within the lab network.

Active hosts discovered included:

* Kali Linux
* Windows 10
* Metasploitable

This confirms that the systems are reachable and ready for further enumeration and security testing.

---

# Skills Demonstrated

• Network host discovery
• Subnet scanning
• Nmap reconnaissance techniques
• Identifying active systems on a network

---

# Conclusion

Nmap successfully identified active hosts within the virtual lab environment. This reconnaissance step is essential before performing service enumeration or vulnerability scanning.

