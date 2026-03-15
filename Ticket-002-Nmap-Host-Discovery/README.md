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

A host discovery scan was conducted using Nmap to identify active systems on the subnet.

Command used:

```
nmap -sn 192.168.56.0/24
```

Screenshot:
[View Screenshot](Screenshots/07_Kali_Nmap_Scan.png)

---

# Step 2 — Service Detection

Once hosts were identified, a version detection scan was performed to determine services running on discovered hosts.

Command used:

```
nmap -sV 192.168.56.103
```

Screenshot:
[View Screenshot](Screenshots/08_Kali_nmap_sV.png)

---

# Step 3 — Windows Network Verification

Network connections and listening ports were verified on the Windows system to confirm active services.

Command used:

```
netstat -ano
```

Screenshot:
[View Screenshot](Screenshots/09_Windows_Netscan_Ano.png)

---

# Tools Used

```
nmap
netstat
```

---

# Findings

The Nmap host discovery scan successfully identified active systems within the virtual lab network.

The following hosts were detected as active:

* Kali Linux — 192.168.56.101
* Metasploitable — 192.168.56.103
* Windows 10 — 192.168.56.105

Service detection confirmed several network services running on the target systems.

---

# Skills Demonstrated

• Network host discovery
• Subnet scanning
• Service enumeration using Nmap
• Verification of active connections using netstat
• Basic network reconnaissance techniques

---

# Conclusion

Nmap successfully identified active hosts within the virtual lab environment. This discovery phase provides the foundation for deeper reconnaissance activities such as port scanning, service enumeration, and vulnerability analysis.


