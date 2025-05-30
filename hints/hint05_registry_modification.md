# Hint 05 – Registry Modification (Persistence Simulation)

## ✅ Simulated Activity
Simulated a registry-based persistence technique often used by malware and threat actors, and capture it using **Sysmon Event ID 13**.

---

## Technique: Registry Persistence via PowerShell

We add a new registry value under the `Run` key in `HKCU` (HKEY_CURRENT_USER). This causes an executable to launch every time the user logs into Windows.

---

### Command Used:
```powershell
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" -Name "evil" -Value "C:\temp\malware.exe"
```
---

## Verification
To confirm the registry key was added:
```powershell
Get-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run"
```
---

### Output:
```powershell
evil : C:\temp\malware.exe
```
![powershell commands](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint05_registry_modification_powershell.png)

---

## Logs
Sysmon logs captured
![sysmon logs](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint05_registry_modification_sysmon_logs.png)
- Event ID: 13
- Event Name: Registry value set
- Registry Path: HKCU\Software\Microsoft\Windows\CurrentVersion\Run
- Value Name: evil
- Value Data: C:\temp\malware.exe
- Process: powershell.exe
