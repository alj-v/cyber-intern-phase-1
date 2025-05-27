# 🔧 Lab Environment Setup – Cyber Internship Phase 1

This file documents the complete lab environment I set up for completing the Phase 1 internship tasks.

---

## 🖥️ Virtual Machines

- **Windows 10 VM**
  - Platform: VMware Workstation
  - Tools Installed:
    - Wazuh Agent
    - Sysmon
    - Winlogbeat (initially used for testing)
  - Logs Sent To: Wazuh Manager (via Wazuh agent)

- **Wazuh Manager (OVA)**
  - Platform: VirtualBox
  - Role: Central log collection and analysis (SIEM)
  - Components:
    - Wazuh Dashboard (Kibana)
    - Wazuh Manager
    - Internal Elasticsearch (service not exposed directly)
    - Logstash not installed by default
   
- **Kali Linux VM**
  - Platform: VirtualBox

---

## 🔗 Network Configuration

- **Kali**, **Win10**, and **Wazuh Manager** are all on the same internal network (NAT or Host-only).
- Verified connectivity using `ping` and `Test-NetConnection`.

---

## 📦 Agent & Log Configuration

- **Sysmon Logs:**
  - Configured directly via `ossec.conf` on the Wazuh agent.
  - Sysmon logs are successfully sent using:
    ```xml
    <localfile>
      <location>Microsoft-Windows-Sysmon/Operational</location>
      <log_format>eventchannel</log_format>
    </localfile>
    ```

- **Security Logs (e.g., 4625, 4688):**
  - Captured via Wazuh agent and sent to Wazuh dashboard.

- **PowerShell Logs:**
  - Script Block Logging and process creation captured.

---

## 🖼️ Screenshots

Screenshots of the environment are located in the `screenshots/` folder.

---

## 🧠 Notes

- Winlogbeat was originally set up to send logs to Elasticsearch, but due to service issues and closed ports, I switched to using the native Wazuh agent configuration — which worked perfectly.
- Sysmon logs were not visible in Wazuh until I configured them in `ossec.conf` and restarted the Wazuh agent.
- Event ID filtering was later added using Wazuh's `<query>` option for fine-tuned collection.

---

📌 *Setup complete. All systems green.* ✅
