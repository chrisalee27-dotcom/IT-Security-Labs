# Ticket 007 — PowerShell Persistence Investigation

## Objective

Investigate PowerShell activity on a Windows workstation to identify potential persistence mechanisms used to maintain remote access.

---

## Lab Environment

| Machine    | Role               | IP Address     |
| ---------- | ------------------ | -------------- |
| Kali Linux | Attacker System    | 192.168.56.101 |
| Windows 10 | Target Workstation | 192.168.56.105 |

Network: **192.168.56.0/24**

---

## Step 1 — Persistence Mechanism Identified

During the investigation, a persistence mechanism was identified on the Windows system. Persistence techniques allow an attacker to maintain access to a compromised system even after the initial connection is terminated.

Screenshot:
[View Screenshot](Screenshots/16_Persistance.png)

Observation:

The system configuration indicates that a command or service was configured to allow the attacker to maintain continued access to the system.

---

## Step 2 — Investigate Running Processes

Running processes were examined to determine which application was responsible for the suspicious activity.

Command used:

```
tasklist
```

Screenshot:
[View Screenshot](Screenshots/21_Powershell_exe.png)

Observation:

The investigation revealed that **PowerShell.exe** was running and associated with the suspicious activity. Attackers frequently use PowerShell because it is a built-in Windows administrative tool capable of executing scripts and remote commands.

---

## Tools Used

```
powershell
tasklist
windows command prompt
```

---

## Findings

The investigation identified PowerShell as the process responsible for maintaining activity on the system.

Key observations:

• PowerShell was running as an active process
• The system previously had an active reverse shell connection
• Persistence techniques may allow the connection to re-establish

This behavior is consistent with common attacker techniques that leverage legitimate Windows tools.

---

## Skills Demonstrated

• Process investigation
• PowerShell activity analysis
• Persistence concept identification
• Host-based investigation techniques

---

## Conclusion

The investigation identified PowerShell as the process responsible for suspicious activity on the Windows workstation. This demonstrates how attackers can use legitimate system tools to maintain persistence and control over compromised systems.


