# Ticket 004 — Reverse Shell Connection Investigation

## Objective

Establish and verify a reverse shell connection between Kali Linux and a Windows workstation within the virtual lab environment.

---

# Lab Environment

| Machine    | Role               | IP Address     |
| ---------- | ------------------ | -------------- |
| Kali Linux | Attacker System    | 192.168.56.101 |
| Windows 10 | Target Workstation | 192.168.56.105 |

Network: **192.168.56.0/24**

---

# Step 1 — Initial Connection Attempt

An initial connection attempt was made from Kali Linux to the Windows system using Netcat.

Command used:

```
nc 192.168.56.105 4444
```

Screenshot:
[View Screenshot](Screenshots/15_Kali_Connection Refused.png)

Observation:

The connection attempt failed with a **connection refused** message, indicating that no process was listening on port **4444**.

---

# Step 2 — Configure Listener on Windows

A listener was configured on the Windows system using PowerShell.

Command used:

```
nc -lvnp 4444
```

Screenshot:
[View Screenshot](Screenshots/17_Powershell_Listener.png)

Observation:

The system began listening for incoming connections on port **4444**.

---

# Step 3 — Establish Connection from Kali

After configuring the listener, Kali Linux attempted the connection again.

Command used:

```
nc 192.168.56.105 4444
```

Screenshot:
[View Screenshot](Screenshots/19_Kali_Connection.png)

Observation:

The connection was successfully established between the attacker system and the Windows workstation.

---

# Step 4 — Verify Active Connection

The active connection was verified on the Windows system using netstat.

Command used:

```
netstat -ano
```

Screenshot:
[View Screenshot](Screenshots/20_Established.png)

Observation:

The output shows an **ESTABLISHED TCP connection** between:

```
192.168.56.101
192.168.56.105
```

This confirms the reverse shell connection was successfully created.

---

# Tools Used

```
netcat
powershell
netstat
```

---

# Findings

The investigation confirmed that a remote connection could be established from Kali Linux to the Windows workstation using Netcat.

Key observations:

• Initial connection attempts fail if no listener is present
• A listener must be configured on the target system
• Once configured, the attacker system can successfully connect
• Active sessions can be verified using **netstat**

---

# Skills Demonstrated

• Reverse shell setup
• Netcat listener configuration
• Troubleshooting connection errors
• Network session verification
• Investigating active connections

---

# Conclusion

A reverse shell connection was successfully established between Kali Linux and the Windows workstation. The session was confirmed using network monitoring tools, demonstrating how remote command sessions can be created and detected within a network environment.


