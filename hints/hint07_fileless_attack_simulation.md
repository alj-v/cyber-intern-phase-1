# Hint 07 - Fileless Attack Simulation

## ✅Simulated Activity
Simulate a **fileless attack** using PowerShell to execute code directly from memory — a technique often used by threat actors to avoid detection and bypass traditional file-based defenses.

---

## Command

```powershell
powershell -NoProfile -ExecutionPolicy Bypass -Command "IEX 'Write-Output HelloFromMemory'; Start-Sleep -Seconds 5"
```
![fileless attack simulation](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint07_fileless_attack_simulation.png)
- The **Invoke-Expression (IEX)** cmdlet executed a command stored in memory.
- **Write-Output** displayed a message:
```powershell
HelloFromMemory
```
- **Start-Sleep** gave enough time for logs to register the PowerShell process.

---

## Logs
- Sysmon Event ID 1 — Process Create
![sysmon logs of fileless attack](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint07_fileless_attack_simulation_sysmon_log.png)
- Windows PowerShell Logs
![windows powershell logs of fileless attack](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint07_fileless_attack_powershell_log.png)
- No Files Written to Disk — This was a memory-only execution

---

> This technique mirrors how attackers load scripts into memory to evade detection. Although we used a harmless command, the logging behavior mimics real-world fileless malware.


