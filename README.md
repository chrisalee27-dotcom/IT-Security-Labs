# Ticket 001 – Virtual Lab Network Connectivity Troubleshooting

## Overview

A three-machine cybersecurity lab was deployed using **Oracle VirtualBox** consisting of **Kali Linux, Windows 10, and Metasploitable**.
Before conducting security testing and investigations, the network connectivity between the machines needed to be validated.

This ticket documents the process of verifying IP configuration and testing connectivity across the virtual network to ensure all systems could communicate properly.

---

## Lab Environment

| Machine        | Role                             | IP Address     |
| -------------- | -------------------------------- | -------------- |
| Kali Linux     | Attacker / Security Testing      | 192.168.56.101 |
| Metasploitable | Vulnerable Target                | 192.168.56.103 |
| Windows 10     | Workstation / Investigation Host | 192.168.56.105 |

All machines were connected using a **VirtualBox Host-Only Network Adapter** to isolate the lab from the external network.

---

## Step 1 – Verify IP Configuration

Each machine’s network configuration was verified to confirm they were assigned IP addresses within the same subnet.

Screenshot:

[01_Windows_10_IP](Screenshots/01_Windows_10_IP.png)

[02_Kali_Linux_IP](Screenshots/02_Kali_Linux_IP.png)

[03_Metasploitable_IP](Screenshots/03_Metasploitable_IP.png)

---

## Step 2 – Test Connectivity Between Hosts

Connectivity between the machines was tested using **ping** to ensure the network was functioning correctly.

### Windows → Kali

Screenshot:

[04_Windows_10_Ping](Screenshots/04_Windows_10_Ping.png)

---

### Kali → Windows

Screenshot:

[05_Kali_Ping](Screenshots/05_Kali_Ping.png)

---

### Metasploitable → Kali

Screenshot:

[06_Metasploitable_Ping](Screenshots/06_Metasploitable_Ping.png)

---

## Tools and Commands Used

```
ipconfig
ifconfig
ping
```

---

## Findings

* All machines were successfully assigned IP addresses within the **192.168.56.0/24** subnet.
* Connectivity between the virtual machines was verified using **ICMP echo requests (ping)**.
* Successful responses confirmed that the **VirtualBox Host-Only network was configured correctly**.

---

## Skills Demonstrated

* Virtual machine network configuration
* IP address verification
* Basic network troubleshooting
* Connectivity validation using ICMP
* VirtualBox host-only network configuration

---

## Conclusion

The lab network was successfully validated and confirmed operational.
All machines were able to communicate within the isolated virtual subnet, enabling further security testing and investigation activities.

This connectivity validation serves as the foundation for future investigations including **network scanning, firewall analysis, and attacker simulation exercises**.
