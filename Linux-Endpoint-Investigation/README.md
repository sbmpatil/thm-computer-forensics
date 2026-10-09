# Linux Endpoint Investigation

## Linux Incident Surface
- Processes found (intro query): `3`
- Remote IP the netcom process connects to: `68.53.23.246`
- Remote port netcom communicates to: `443`
- Default path for installed services: `/etc/systemd/system`
- Suspicious service running: `benign.service`
- Process the service points to: `benign`
- Number of running processes (benign): `7`
- Log entries in dpkg.log for the install: `6`
- Package installed on 17 Sept 2024: `c2comm`
- User who attempted SSH on 11 Sept 2024: `saqib`
- IP of the failed SSH attempt: `10.11.75.247`

## Linux Process Analysis
- Flag from check-env: `THM{8c860435f00c943c21f6b6e0f1b2f854}`
- Command listing open files and the processes that opened them: `lsof`
- Parent of the nc processes (pstree): `abzkd83o4jakxld`
- Full C2 URL in the system-level cronjob: `http://c2.intelligent-software.thm:8310/beacon`
- Hidden flag in a user-level cronjob script: `THM{4682786cf2d92f01c4d30a2bbf4621f7}`
- Decoded flag echoed every 15s (pspy64): `THM{851a981445dbfb9485c3771510a53568}`
- Flag in the backdoor service's description: `THM{4922066dc6494e8d4d507eef2205c262}`
- Flag in journalctl logs for the backdoor service: `THM{053c12e620acea8a77b4bdcba578ca19}`
- URL receiving Janice's SSH key on startup: `http://aabab.best-it-services.thm/id_rsa`
- Command in the Show Network Interfaces autostart script: `ifconfig`
- Flag in Janice's Vim search history: `THM{4a8fd984228d89999342d189e6b916de}`
- Flag in Eduardo's Firefox bookmarks (DumpZilla): `THM{5d5cb0ffe8369ab08f1e90aa9e9bc24e}`

## Linux Logs Investigations
### Task 2 — Logging Levels and Kernel Logs
- Logs for hardware events and system errors: `kernel`
- Memory space used to store system messages: `Kernel ring buffer`
- Default log level for non-imminent errors: `warning`

### Other reference answers
- Log file that records failed login attempts only: `btmp`
- Severity keyword for immediate action needed: `alert`
- Facility code for cron jobs: `9`
- Parameter to configure journal log persistence (journald.conf): `Storage`
- Utility to search auditd logs: `ausearch`
- Command to search logs for a session opened for a user: `sudo grep -i "session opened" /var/log/auth.log`
- Folder containing Apache2 logs: `/var/log/apache2`

### Task 9 — Capstone
- IP the application was exploited from: `10.10.190.69`
- File containing the reverse shell: `cmd.php`
- Port the reverse shell was running on: `5000`
- File executed with sudo privileges: `tests.sh`
- User created using the service: `attacker`
- Was the new account ever logged in to? `n`

## Linux Live Analysis
- Hostname returned for address 0.0.0.0: `attacker.thm`
- Tables listed for Linux OS on the osquery site: `154`
- Machine ID: `dc7c8ac5c09a4bbfaf3d09d399f10d96`
- Architecture: `x86_64`
- Process running from /tmp (not hidden): `sshdd`
- Suspicious process in memory: `.systm_updater`
- Process running from the user directory: `rdp_updater`
- State of the local port listening on 80: `ESTABLISHED`
- File opened by the suspicious process: `keylogger.log`
- Process associated with that file: `sshdd`
- Hidden binary in the root directory: `.systmd`
- Suspicious package installed: `datacollector`
- Code hidden in the package description: `{NOT_SO_BENIGN_Package}`
- Suspicious service installed via netcat: `systm.service`
- Full path of the process in the cron table: `/home/badactor/storage/.secret_docs/rdp_updater`

> Note: newer versions add a "System Profiling" task and an `authorized_keys` comment question whose values are lab-specific — read them from your osquery output.

## IronShade (challenge)
- Machine ID: `dc7c8ac5c09a4bbfaf3d09d399f10d96`
- Backdoor user account created: `mircoservice`
- Cronjob set up for persistence: `@reboot /home/mircoservice/printer_app`
- Suspicious hidden process from the backdoor account: `.strokes`
- Processes running from the backdoor account's directory: `2`
- Hidden file in memory from the root directory: `.systmd`
- Suspicious services installed (alphabetical): `backup.service, strokes.service`
- When the backdoor account was created: `Aug 5 22:05:33`
- IP with multiple SSH connections against the backdoor account: `10.11.75.247`
- Failed SSH login attempts on the backdoor account: `8`
- Malicious package installed: `pscanner`
- Secret code in the package metadata: `{_tRy_Hack_ME_}`
