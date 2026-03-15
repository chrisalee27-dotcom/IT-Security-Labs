# Ticket 008 — SMB Service Enumeration

## Objective

Investigate SMB services on a Windows workstation and determine whether file shares or user accounts can be enumerated remotely.

---

## Lab Environment

| Machine    | Role                    | IP Address     |
| ---------- | ----------------------- | -------------- |
| Kali Linux | Security Testing System | 192.168.56.101 |
| Windows 10 | Target Workstation      | 192.168.56.105 |

Network: **192.168.56.0/24**

---

# Step 1 — Identify SMB Services on the Network

A network scan was performed to identify hosts exposing SMB services on port **445**.

Command used:

```
nmap -p 445 192.168.56.0/24
```

Screenshot:
[Screenshot](Screenshots/01_SMB_Port_Scan.png)

### Observation

The scan identified multiple hosts on the network, but only **192.168.56.105** had port **445 open**, indicating that the Windows system is running an SMB service.

---

# Step 2 — Attempt Anonymous SMB Connection

An attempt was made to enumerate SMB shares anonymously using `smbclient`.

Command used:

```
smbclient -L //192.168.56.105 -N
```

Screenshot:
[Screenshot](Screenshots/02_SMB_Access_Denied.png)

### Observation

The connection attempt returned:

```
NT_STATUS_ACCESS_DENIED
```

This indicates that the Windows host does **not allow anonymous SMB access**, which is a good security configuration.

---

# Step 3 — Identify SMB Protocol Versions

Next, Nmap SMB scripts were used to determine which SMB protocol versions are supported by the target.

Command used:

```
nmap -p445 --script smb-protocols 192.168.56.105
```

Screenshot:
[Screenshot](Screenshots/03_SMB_Protocols_Scan.png)

### Observation

The scan revealed that the host supports the following SMB protocol versions:

* SMB 2.0.2
* SMB 2.1
* SMB 3.0
* SMB 3.0.2
* SMB 3.1.1

These are modern SMB versions and suggest that **SMBv1 is disabled**, which helps mitigate several well-known vulnerabilities.

---

# Step 4 — Attempt SMB Share Enumeration

An enumeration attempt was made to discover available network shares.

Command used:

```
nmap -p445 --script smb-enum-shares 192.168.56.105
```

Screenshot:
[Screenshot](Screenshots/04_SMB_Share_Enumeration.png)

### Observation

No shares were returned by the scan, suggesting that share enumeration is **restricted or requires authentication**.

---

# Step 5 — Attempt SMB User Enumeration

A user enumeration script was executed to determine if any Windows user accounts could be identified remotely.

Command used:

```
nmap -p445 --script smb-enum-users 192.168.56.105
```

Screenshot:
[Screenshot](Screenshots/05_SMB_User_Enumeration.png)

### Observation

The scan did not reveal any user accounts, indicating that user enumeration is also **restricted without authentication**.

---

# Conclusion

The SMB investigation showed that:

* Port **445** is open on the Windows workstation
* Anonymous SMB access is **blocked**
* Modern SMB versions are enabled
* SMB share enumeration is **restricted**
* SMB user enumeration is **restricted**

These findings indicate that the SMB service on the Windows host is **properly hardened against anonymous enumeration attacks**.

---

# Skills Demonstrated

* SMB service discovery
* Network enumeration using Nmap
* SMB protocol analysis
* Share enumeration techniques
* User enumeration techniques
* Security posture assessment

