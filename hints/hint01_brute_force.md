# Hint 01 – Brute Force Detection

## ✅ Simulated Activity:
Simulated a brute force attack using PowerShell on the Windows 10 VM by attempting multiple failed logins.

### Command Used:
```powershell
for ($i=1; $i -le 10; $i++) {
    net use \\127.0.0.1\IPC$ /user:FakeUser WrongPassword
}
```
## Screenshot of the brute force attack simulation
![brute force attack](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/brute%20force%20attack.png)
## Screenshot of the Event Viewer showing the failed login entries
![brute force attack logs](https://github.com/alj-v/cyber-intern-phase-1/blob/main/screenshots/brute%20force%20attack%20logs.png)

## Observed Logs:
- Log Source: Windows Event Viewer
- Log Type: Security
- Event ID: 4625 (Failed Logon)
- Status: Audit Failure
- TargetUserName: FakeUser
- Logon Type: 3 (Network)
- Failure Code: 0xC000006D
