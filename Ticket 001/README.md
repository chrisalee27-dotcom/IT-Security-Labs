# Ticket 001 – Virtual Lab Network Connectivity

## Overview

This ticket documents the initial setup and connectivity verification of a three-machine cybersecurity lab using Oracle VirtualBox.

The goal of this exercise was to confirm that all virtual machines could communicate across the isolated host-only network before beginning security testing and investigations.

---

## Lab Environment

| Machine | Role | IP Address |
|-------|------|-----------|
| Kali Linux | Security Testing System | 192.168.56.101 |
| Metasploitable | Vulnerable Target | 192.168.56.103 |
| Windows 10 | Workstation | 192.168.56.105 |

All machines were connected using a **VirtualBox Host-Only Network Adapter**.

---

# Step 1 – Verify IP Configuration

### Windows 10 IP Configuration

![Windows IP](Screenshots/01_Windows_10_IP.png)

### Kali Linux IP Configuration

![Kali IP](Screenshots/02_Kali_Linux_IP.png)

### Metasploitable IP Configuration

![Metasploitable IP](Screenshots/03_Metasploitable_IP.png)

---

# Step 2 – Connectivity Testing

## Windows → Kali

![Windows Ping](Screenshots/04_Windows_10_Ping.png)

## Kali → Windows

![Kali Ping](Screenshots/05_Kali_Ping.png)

## Metasploitable → Kali

![Metasploitable Ping](Screenshots/06_Metasploitable_Ping.png)

---

# Commands Used

---

# Findings

- All machines were assigned addresses within the **192.168.56.0/24 subnet**
- ICMP connectivity was confirmed between all hosts
- The VirtualBox **Host-Only network successfully isolated the lab**

---

# Skills Demonstrated

- Virtual machine networking
- IP address verification
- Connectivity testing
- Network troubleshooting
- VirtualBox host-only configuration

---

# Conclusion

The virtual cybersecurity lab network was successfully configured and verified. All systems were able to communicate across the isolated subnet, allowing future security labs to proceed safely within the contained environment.
