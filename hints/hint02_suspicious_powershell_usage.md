# Hint 02 – Suspicious PowerShell Usage

## ✅ Simulated Activity:
Executed an encoded PowerShell command using Base64-encoded input.

### Command Used:
```powershell
powershell -enc UwB0AGEAcgB0AC0AUAByAG8AYwBlAHMAcwAgACIAcwBtAG8AYwBoAC4AZQB4AGUAIgA=
```
![suspisious powershell usage](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint02_suspicious_powershell_usage.png)

## Screenshot of Sysmon log generated for suspicious powershell usage
![suspicious powershell usage logs](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint02_suspicious_powershell_usage_log.png)
Although Sysmon captured Event ID 1 for PowerShell process creation locally, the log was not visible in Wazuh due to a missing configuration entry in winlogbeat.yml. However, Event ID 4688 from Windows Security logs confirmed the encoded PowerShell execution.

## Observed Logs:
- Sysmon Logs (Event ID 1)
- Showed process creation: powershell.exe with encoded string

## Logs created in wazuh
![suspicious powershell usage lgs in wazuh](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint02_suspicious_powershell_usage_logs_in_wazuh.png)
