# Ticket 004 — Reverse Shell Connection Investigation

## Objective

Establish and verify a remote shell connection between Kali Linux and a Windows system within the virtual lab environment.

---

# Lab Environment

| Machine    | Role                    | IP Address     |
| ---------- | ----------------------- | -------------- |
| Kali Linux | Security Testing System | 192.168.56.101 |
| Windows 10 | Target Workstation      | 192.168.56.105 |

Network: **192.168.56.0/24**

---

# Step 1 — Initial Connection Attempt

An attempt was made to connect from Kali Linux to the Windows system using Netcat.

Command used:

```
nc 192.168.56.105 4444
```

Screenshot:
[View Screenshot](Screenshots/15_Kali_Connection_Refused.png)

Observation:

The connection attempt failed with a **connection refused** message, indicating that no service was listening on the target port.

---

# Step 2 — Configure Listener on Windows

A listener was configured on the Windows system to accept incoming connections.

Command used:

```
powershell -c "Start-Process nc -ArgumentList '-lvnp 4444'"
```

Screenshot:
[View Screenshot](Screenshots/17_Powershell_Listener.png)

Observation:

The listener began waiting for inbound connections on port **4444**.

---

# Step 3 — Establish Connection from Kali

Kali Linux initiated a connection to the Windows listener.

Command used:

```
nc 192.168.56.105 4444
```

Screenshot:
[View Screenshot](Screenshots/19_Kali_Connection.png)

Observation:

The connection was successfully established between the attacker system and the target workstation.

---

# Step 4 — Verify Active Connection

The connection was verified on the Windows system using the netstat command.

Command used:

```
netstat -ano
```

Screenshot:
[View Screenshot](Screenshots/20_Established.png)

Observation:

The output shows an **ESTABLISHED** connection between:

```
192.168.56.101
192.168.56.105
```

This confirms that the remote session is active.

---

# Tools Used

```
netcat
powershell
netstat
```

---

# Findings

A remote connection was successfully established between Kali Linux and the Windows system using Netcat.

The session was confirmed using netstat, which showed an **ESTABLISHED TCP connection** between the two hosts.

Port used for the connection:

• TCP 4444

---

# Skills Demonstrated

• Reverse shell setup
• Netcat listener configuration
• Troubleshooting connection errors
• Verifying active network connections
• Investigating active sessions using netstat

---

# Conclusion

The reverse shell connection was successfully established between Kali Linux and the Windows workstation. The investigation demonstrated how attackers can create remote command sessions and how defenders can identify active connections using network monitoring tools.

