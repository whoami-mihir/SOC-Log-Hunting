# Findings Summary
## Brute Force (T1110)
- Multiple 4625 failures for `labadmin` from `192.168.56.50`
- Later 4624 success from same IP
- Linux logs showed failed sshd attempts then success for `root`
## Lateral Movement (T1021.*, T1569.002)
- RDP logon (4624 LogonType=10) from rare IP
- Admin share access (5140) observed
- Service install (7045) named `UpdaterSvc` executed from `C:\ProgramData\Updater\upd.exe`
## Persistence (T1136.001, T1053.005, T1547.001, T1543.003)
- New user `backupsvc` created and added to Administrators
- Scheduled task `ChromeUpdateDaily` created pointing to AppData binary
- Sysmon detected Run key modification for `Chrome Helper`
## Analyst Assessment
The dataset represents a realistic attack chain: **brute force → RDP → admin share → service install → persistence**.  
Recommended actions: disable `backupsvc`, remove scheduled task and service, reset `labadmin` credentials, enforce MFA, restrict RDP/admin shares.
