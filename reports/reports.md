# 🛡️Cybersecurity SIEM Internship Program - Phase 1 Report

**Intern Name**: Aleena Joy

**Phase**: 1 – Foundation Setup  
**Start Date**: 12/05/25  
**Mentor**: Rajendra Bodda

---

## 📌Objective
The primary goal of Phase 1 was to simulate various cybersecurity attack scenarios to understand their behaviors and the corresponding system logs. This phase emphasized hands-on experience with Windows systems, PowerShell scripting, and log analysis using tools like Sysmon and Event Viewer.

---

## Completed Tasks Overview

### Hint 01: Brute Force Detection
- **Objective**: Simulated a brute force attack using PowerShell on the Windows 10 VM by attempting multiple failed logins.
- **Command Used**:
```powershell
for ($i=1; $i -le 10; $i++) {
    net use \\127.0.0.1\IPC$ /user:FakeUser WrongPassword
}
```
- **Logs Observed**:
  - Windows Security Event ID 4625: Failed login attempts.
  - Wazuh log
- **Screenshot**: ![Hint01](../screenshots/hint01.png)

---

### Hint 02: Suspicious PowerShell Usage
- **Objective**: Executed an encoded PowerShell command using Base64-encoded input.
- **Command Used**:
  ```powershell
  powershell -enc UwB0AGEAcgB0AC0AUAByAG8AYwBlAHMAcwAgACIAcwBtAG8AYwBoAC4AZQB4AGUAIgA=
  ```
- **Logs Observed**:
  - Sysmon log for Event ID 1 Process creation
  - Wazuh logs of event ID 4688

 ---

### Hint 03: USB Drive Insertion and File Execution
- **Objective**: Captured USB insertion logs, file transfer logs, and execution logs using Sysmon and Windows Event Viewer.
- **Steps Taken**:
  - Inserted USB drive into Windows VM.
  - Executed .bat test file (usb_drive_insertion.bat)
  - Verified logs using Event Viewer (eventvwr.msc)
- **Logs Observed**:
  - Sysmon Logs
    - File creation log (Event ID: 11) when copying the file
    - Sysmon Event ID 1 Process execution from USB
    - Process execution log generated
  - DriveFrameworks timestamp logs for external drive insertion

---

### Hint 04: Malware Execution Simulation
- **Objective**: Generated and analyzed Sysmon Event ID 3 logs in Windows, including observations on network connections and Wazuh logging issues.
- **Steps Taken**:
  - Created a batch script to simulate malware execution
  - Executed the script from Downloads/ to trigger process execution logs.
  - Verified Sysmon logs using Event Viewer (eventvwr.msc).
- **Logs Observed**:
  - Sysmon log for Event ID 1 Process Creation
  - Sysmon log for Event ID 3 Network Connections

---

### Hint 05: Registry Modification (Persistence Simulation)
- **Objective**: Simulated a registry-based persistence technique often used by malware and threat actors, and capture it using Sysmon Event ID 13.
- **Command Used**:
 ```powershell
Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" -Name "evil" -Value "C:\temp\malware.exe"
 ```
- **Logs Observed**:
  - Sysmon log for Event ID 13 Registry Value Setting

---

### Hint 06: Suspicious Network Connection
- **Objective**: Simulated a suspicious outbound HTTP connection using PowerShell and detect it using Sysmon Event ID 3 (Network Connection).
- **Command Used**:
 ```powershell
Invoke-WebRequest -Uri http://testphp.vulnweb.com
 ```
- **Logs Observed**:
  - Sysmon log for Event ID 3 Network Connection

---

### Hint 07: Fileless Attack Simulation
- **Objective**: Simulate a fileless attack using PowerShell to execute code directly from memory — a technique often used by threat actors to avoid detection and bypass traditional file-based defenses.
- **Command Used**:
 ```powershell
powershell -NoProfile -ExecutionPolicy Bypass -Command "IEX 'Write-Output HelloFromMemory'; Start-Sleep -Seconds 5"
 ```
- **Logs Observed**:
  - Powershell log for Event ID 4104
  - Sysmon log for Event ID 1 Process Creation

---

### Hint 08: Suspicious Scheduled Task
- **Objective**: Created a scheduled task that simulates a suspicious fileless attack by invoking PowerShell with stealthy parameters.
- **Command Used**:
 ```powershell
schtasks /create /tn "MidnightWatcher" /tr "powershell.exe -nop -w hidden -c IEX 'Write-Output HelloFromTask'; Start-Sleep -Seconds 10" /sc minute /mo 1
 ```
- **Logs Observed**
  - Windows Security logs of Event ID 4698 generated when new scheduled task is created
  - Sysmon logs for Event ID 1 Process creation event
  - Wazuh log for the event

---

## Learnings and Reflections
- Gained hands-on experience with Windows security event logs and Sysmon.
- Understood the significance of each simulated attack and its detection mechanisms.
- Improved proficiency in PowerShell scripting for both benign and simulated malicious activities.
- Recognized the importance of maintaining organized documentation and evidence for each task.

## ✅ Conclusion
Phase 1 provided a foundational understanding of common cybersecurity threats and the system's response to them. The hands-on approach reinforced theoretical knowledge and emphasized the importance of meticulous documentation and analysis in cybersecurity practices.
