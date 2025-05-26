# Hint 02 – Suspicious PowerShell Usage

## ✅ Simulated Activity:
Executed an encoded PowerShell command using Base64-encoded input.

### Command Used:
```powershell
powershell -enc UwB0AGEAcgB0AC0AUAByAG8AYwBlAHMAcwAgACIAcwBtAG8AYwBoAC4AZQB4AGUAIgA=
```
![suspisious powershell usage](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint02_suspicious_powershell_usage.png)

## Screenshot of log generated for suspicious powershell usage
![suspicious powershell usage logs](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/hint02_suspicious_powershell_usage_log.png)

## Observed Logs:
- Sysmon Logs (Event ID 1)
- Showed process creation: powershell.exe with encoded string
