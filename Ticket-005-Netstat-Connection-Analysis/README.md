# Ticket 005 — Netstat Connection Analysis

## Objective

Investigate active network connections on a Windows system to identify suspicious activity and determine which process is responsible for the connection.

---

# Lab Environment

| Machine    | Role               | IP Address     |
| ---------- | ------------------ | -------------- |
| Kali Linux | Attacker System    | 192.168.56.101 |
| Windows 10 | Target Workstation | 192.168.56.105 |

Network: **192.168.56.0/24**

---

# Step 1 — Identify Active Network Connections

The Windows system was examined using **netstat** to identify active network connections.

Command used:

```
netstat -ano
```

Screenshot:
[View Screenshot](Screenshots/20_Established.png)

Observation:

The output revealed an **ESTABLISHED TCP connection** between:

```
192.168.56.105
192.168.56.101
```

This indicated that the Windows system had an active network session with the Kali machine.

---

# Step 2 — Filter for Suspicious Port Activity

To investigate further, the output was filtered to search specifically for traffic on port **4444**, which is commonly used in reverse shell connections.

Command used:

```
netstat -ano | findstr 4444
```

Screenshot:
[View Screenshot](Screenshots/18_Find_Str_4444.png)

Observation:

The filtered results confirmed that port **4444** was actively being used for the connection.

---

# Step 3 — Identify the Responsible Process

The process associated with the suspicious connection was identified using the **tasklist** command.

Command used:

```
tasklist
```

Screenshot:
[View Screenshot](Screenshots/21_Powershell_exe.png)

Observation:

The connection was associated with a **PowerShell process**, indicating that the shell session was initiated using PowerShell on the Windows system.

---

# Tools Used

```
netstat
findstr
tasklist
powershell
```

---

# Findings

The investigation identified an active reverse shell connection between the Windows workstation and the Kali Linux system.

Key observations:

• An ESTABLISHED connection existed between the two hosts
• Port **4444** was being used for communication
• The responsible process was **PowerShell**

This indicates that the system was running a remote command session.

---

# Skills Demonstrated

• Network connection analysis
• Identifying suspicious ports
• Process investigation
• Command-line forensic analysis
• Incident investigation methodology

---

# Conclusion

The investigation successfully identified a suspicious network session on the Windows system. By analyzing netstat output and identifying the associated process, the source of the remote connection was traced to a PowerShell process communicating over port **4444** with the Kali Linux host.
