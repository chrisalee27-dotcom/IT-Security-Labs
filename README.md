# Ticket 001 – Virtual Lab Network Connectivity Troubleshooting

## Overview

A three-machine cybersecurity lab was deployed using **Oracle VirtualBox** consisting of **Kali Linux, Windows 10, and Metasploitable**. Before conducting security testing and investigations, network connectivity between the machines needed to be verified.

This ticket documents the process of confirming IP configuration and validating connectivity across the virtual network.

---

## Lab Environment

| Machine        | Role                             | IP Address     |
| -------------- | -------------------------------- | -------------- |
| Kali Linux     | Attacker / Security Testing      | 192.168.56.101 |
| Metasploitable | Vulnerable Target                | 192.168.56.103 |
| Windows 10     | Workstation / Investigation Host | 192.168.56.105 |

All machines were connected using a **VirtualBox Host-Only Network Adapter** to isolate the lab network from external systems.

---

## Step 1 – Verify IP Configuration

Each system's IP configuration was reviewed to confirm they were assigned addresses within the same subnet.

Screenshot:

[Windows IP Configuration](Screenshots/01_Windows_10_IP.png)

[Kali Linux IP Configuration](Screenshots/02_Kali_Linux_IP.png)

[Metasploitable IP Configuration](Screenshots/03_Metasploitable_IP.png)

---

## Step 2 – Test Network Connectivity

Connectivity between systems was verified using **ICMP echo requests (ping)**.

### Windows → Kali

Screenshot:

[Windows Ping Kali](Screenshots/04_Windows_10_Ping.png)

---

### Kali → Windows

Screenshot:

[Kali Ping Windows](Screenshots/05_Kali_Ping.png)

---

### Metasploitable → Kali

Screenshot:

[Metasploitable Ping Kali](Screenshots/06_Metasploitable_Ping.png)

---

## Tools and Commands Used

```
ipconfig
ifconfig
ping
```

---

## Findings

* All machines received IP addresses within the **192.168.56.0/24 subnet**.
* Successful ICMP responses confirmed that the systems could communicate across the virtual network.
* The **VirtualBox Host-Only Adapter** provided an isolated environment suitable for security testing and investigation labs.

---

## Skills Demonstrated

* Virtual machine networking configuration
* IP address verification
* Network connectivity testing
* Basic network troubleshooting
* VirtualBox host-only networking

---

## Conclusion

The virtual lab network was successfully configured and verified. All systems were able to communicate across the isolated subnet, providing a stable environment for future exercises involving **network enumeration, vulnerability scanning, and security investigations**.

