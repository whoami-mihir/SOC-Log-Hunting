# SOC Log Hunting Using SPLUNK and MITRE ATT&CK 🕵️‍♂️
## 🔎 Overview
This lab simulates a mini SOC workflow in **Splunk**:
- Ingest **sample logs** (Windows Security, Sysmon, Linux auth)
- Run **detections mapped to MITRE ATT&CK**
- Hunt threats like **Brute Force**, **Lateral Movement**, and **Persistence**
- Document findings in a SOC-style narrative
**Use cases covered:**
- Brute force → T1110
- Lateral movement → T1021.001, T1021.002, T1569.002
- Persistence → T1136.001, T1053.005, T1547.001, T1543.003
## ⚙️ How to Use
1. Clone this repo
2. Review detections in `detections/savedsearches.conf`
3. Explore log samples in `/data`
4. Review findings in `/reports/findings-summary.md`
*This is a simulation project — logs are pre-generated and detections are illustrative for study.*
## 🧩 MITRE ATT&CK Mapping
| Detection                 | Technique                           | ID        |
|---------------------------|-------------------------------------|-----------|
| Windows/Linux brute force | Brute Force                        | T1110     |
| RDP logons                | Remote Services: RDP               | T1021.001 |
| Admin share access        | Remote Services: SMB               | T1021.002 |
| Remote service creation   | Service Execution                  | T1569.002 |
| New local user            | Create Account                     | T1136.001 |
| Scheduled task creation   | Scheduled Task                     | T1053.005 |
| Registry Run key mod      | Autostart: Registry Run Keys       | T1547.001 |
| New service persistence   | Windows Service                    | T1543.003 |
## 📊 Dashboard Preview
The `dashboards/Threat_Hunting_Overview.json` file contains:
- Failed logons over time
- Brute force → success pivots
- RDP rare source logons
- Admin share access
- Persistence summary
## ✅ Results (short)
- Detected brute force attempts with eventual success
- Observed RDP lateral movement and admin share access
- Persistence established via new account, scheduled task, Run key
Full write-up: [`reports/findings-summary.md`](reports/findings-summary.md)
