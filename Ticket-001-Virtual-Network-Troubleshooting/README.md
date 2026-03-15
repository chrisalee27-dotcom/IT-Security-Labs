# Ticket 001 — Virtual Lab Network Connectivity Troubleshooting

## Objective

Verify network connectivity between Kali Linux, Windows 10, and Metasploitable within a VirtualBox host-only network before beginning security testing.

---

# Lab Environment

| Machine        | Role                    | IP Address     |
| -------------- | ----------------------- | -------------- |
| Kali Linux     | Security Testing System | 192.168.56.101 |
| Metasploitable | Vulnerable Target       | 192.168.56.103 |
| Windows 10     | Workstation             | 192.168.56.105 |

Network Type: **VirtualBox Host-Only Adapter**

Subnet: **192.168.56.0/24**

---

# Step 1 — Verify IP Configuration

Each machine's IP configuration was verified to confirm that all systems were assigned addresses within the same subnet.

### Windows 10 IP Configuration

Screenshot:
[View Screenshot](Screenshots/01_Windows_10_IP.png)

Command used:

```
ipconfig
```

---

### Kali Linux IP Configuration

Screenshot:
[View Screenshot](Screenshots/02_Kali_Linux_IP.png)

Command used:

```
ip a
```

---

### Metasploitable IP Configuration

Screenshot:
[View Screenshot](Screenshots/03_Metasploitable_IP.png)

Command used:

```
ifconfig
```

---

# Step 2 — Connectivity Testing

After confirming IP addresses, ICMP connectivity tests were performed between machines.

---

### Windows → Kali

Screenshot:
[View Screenshot](Screenshots/04_Windows_10_Ping.png)

Command used:

```
ping 192.168.56.101
```

---

### Kali → Windows

Screenshot:
[View Screenshot](Screenshots/05_Kali_Ping.png)

Command used:

```
ping 192.168.56.105
```

---

### Metasploitable → Kali

Screenshot:
[View Screenshot](Screenshots/06_Metasploitable_Ping.png)

Command used:

```
ping 192.168.56.101
```

---

# Tools and Commands Used

```
ipconfig
ip a
ifconfig
ping
```

---

# Findings

All systems received valid IP addresses within the **192.168.56.0/24 network**.

ICMP connectivity testing confirmed that the systems were able to communicate successfully within the isolated VirtualBox host-only network.

The lab environment is now ready for further security testing, enumeration, and vulnerability analysis.

---

# Skills Demonstrated

• Virtual machine networking
• Host-only networking in VirtualBox
• IP address verification
• Network troubleshooting
• Connectivity validation using ICMP

---

# Conclusion

The virtual lab network was successfully configured and validated. All machines are able to communicate across the host-only network, establishing a stable environment for future cybersecurity exercises.


