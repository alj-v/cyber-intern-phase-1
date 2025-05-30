# Hint 03 - USB Drive Insertion

## ✅Simulated Activity
This experiment focuses on capturing **USB insertion logs**, **file transfer logs**, and **execution logs** using **Sysmon** and **Windows Event Viewer**.

---

## Steps Performed
### 1️⃣ **Enable USB Insertion Logging**
To ensure **Windows logs USB activity**, I enabled **Event Viewer USB logging** at:
## Applications and Services Logs > Microsoft > Windows > DriverFrameworks-UserMode > Operational

To verify logging, I used:
```powershell
Get-EventLog -LogName "Microsoft-Windows-DriverFrameworks-UserMode/Operational" -Newest 5
```

---

### 2️⃣ Insert USB & Execute .bat Test File
- Inserted USB drive into Windows VM.
- Executed .bat test file (usb_drive_insertion.bat)
- Test file used:
```powershell
@echo off
echo.         
echo               hi      
echo.
echo [WARNING: Fake Malware Simulation Running]
echo.
ping 8.8.8.8 -n 5
curl example.com
exit
```
---

### Logs Captured
- Event Viewer Logs
  - USB insertion timestamps
![usb insertion detected log](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint03_usb_drive_insertion_log.png)
  
- Sysmon Logs
  - File creation log (Event ID: 11) when copying the file
![file creation log generated](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint03_file%20dreation_log_from_usb_drive.png)
  - Sysmon Event ID 1 → Process execution from USB
![process execution](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint03_file_executed_from_usb_drive.png)
  - Process execution log generated
![process execution log](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint03_file_execution_from_usb_log.png)

