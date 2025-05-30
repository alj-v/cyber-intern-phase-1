# Hint 06 – Suspicious Network Connection

## ✅Simulated Activity
Simulated a suspicious outbound HTTP connection using PowerShell and detect it using **Sysmon Event ID 3** (Network Connection).

---

## Technique: Simulate a Network Beacon
Using PowerShell, we mimic an attacker's script reaching out to an external domain — a common behavior in malware or command-and-control (C2) activity.

---

### Command Used:

```powershell
Invoke-WebRequest -Uri http://testphp.vulnweb.com
```
---

## Verification
To confirm the request succeeded, check for:
- HTML output in the terminal
- No connection errors
![suspicious network connection powershell](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint06_suspicious_network_connection_powershell.png)

---

## Logs

Sysmon logs generated
![suspicious network connection sysmon log generated](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint06_suspicious_network_connection_sysmon_log.png)
- Event ID: 3
- Image: powershell.exe
- Destination Host: testphp.vulnweb.com
- Destination IP: (44.228.249.3)
- Destination Port: 80
- Protocol: TCP
