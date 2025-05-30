# Hint 8: Suspicious Scheduled Task

## ✅Simulated Activity
Created a scheduled task that simulates a suspicious fileless attack by invoking PowerShell with stealthy parameters.

## Command Used:
```bash
schtasks /create /tn "MidnightWatcher" /tr "powershell.exe -nop -w hidden -c IEX 'Write-Output HelloFromTask'; Start-Sleep -Seconds 10" /sc minute /mo 1
```
![suspicious scheduled task created](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint08_suspicious_scheduled_task_created.png)

---

## Logs generated
- Windows Security logs of Event ID 4698 generated when new scheduled task is created
![security log generated for new sheduled task](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint08_suspicious_scheduled_task_security_log.png)
- Sysmon logs Process creation event
![sysmon logs process creation](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint08_suspicious_scheduled_task_creation_sysmon_log.png)
- Wazuh log for the event
![wazuh log of suspicious scheduled task creation](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint08_suspicious_scheduled_task_created_wazuh_log.png)

---

> Don’t forget to delete your task afterward:
```bash
schtasks /delete /tn "MidnightWatcher" /f
```
