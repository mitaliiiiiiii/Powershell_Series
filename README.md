# Powershell_Series
#22


..................................................................................................................................................................



📌 What is PowerShell?

PowerShell is a task automation and configuration management tool developed by Microsoft. It is widely used in system administration, penetration testing, and SOC operations.

Based on .NET framework
Uses cmdlets (command-lets)
Works with objects (not just text like CMD)
⚙️ Why PowerShell in Cybersecurity?
Log analysis 🧾
Incident response 🚨
Malware analysis 🦠
Automation of security tasks 🤖
Used by both defenders AND attackers
🔑 Basic PowerShell Commands
🔹 1. Get Help
Get-Help Get-Process

👉 Shows usage and details of commands

🔹 2. Get Commands
Get-Command

👉 Lists all available commands

🔹 3. Get Running Processes
Get-Process

👉 Shows all running processes (useful in malware detection)

🔹 4. Get Services
Get-Service

👉 Check running/stopped services

🔹 5. Check System Info
Get-ComputerInfo

👉 Displays OS, BIOS, hardware info

🔍 File & Directory Investigation
🔹 List Files
Get-ChildItem
🔹 Find Specific Files
Get-ChildItem -Path C:\ -Recurse -Filter *.exe

👉 Find all executable files (useful in threat hunting)

🔹 Read File Content
Get-Content file.txt
🧠 Process Monitoring (SOC Use)
🔹 Find Suspicious Process
Get-Process | Where-Object {$_.CPU -gt 100}

👉 Detect high CPU usage (possible malware)

🔹 Kill Process
Stop-Process -Name notepad

⚠️ Use carefully in real environments

🌐 Network Analysis Commands
🔹 View Network Connections
Get-NetTCPConnection

👉 Shows active connections (important for detecting backdoors)

🔹 Check Open Ports
Get-NetTCPConnection | Select-Object LocalAddress,LocalPort
🔹 Test Connectivity
Test-Connection google.com

👉 Similar to ping

📊 Event Log Analysis (VERY IMPORTANT 🔥)
🔹 View Security Logs
Get-EventLog -LogName Security
🔹 Find Failed Logins
Get-EventLog -LogName Security | Where-Object {$_.EventID -eq 4625}

👉 Event ID 4625 = Failed login attempt

🔹 Recent Logs
Get-EventLog -LogName Security -Newest 10
🛑 Execution Policy (Security Feature)
Get-ExecutionPolicy
Set-ExecutionPolicy RemoteSigned

👉 Controls script execution (prevents malicious scripts)

⚔️ PowerShell in Attacks (Red Team)

Attackers use PowerShell for:

Fileless malware
Credential dumping
Remote execution

Example:

Invoke-Expression (IEX)

⚠️ Often used in malicious scripts

🛡️ Detection Tips (Blue Team)
Monitor PowerShell logs:
Get-WinEvent -LogName Microsoft-Windows-PowerShell/Operational
Look for:
Encoded commands
Unusual scripts
Suspicious network calls
📌 Useful Shortcuts
Task	Command
List files	ls
Change directory	cd
Clear screen	cls
Copy file	Copy-Item
Delete file	Remove-Item
🚀 Real-World SOC Use Cases

✔ Investigating suspicious login attempts
✔ Checking running malware processes
✔ Monitoring network activity
✔ Automating incident response

📚 Conclusion

PowerShell is a powerful cybersecurity tool used for:

🔍 Threat hunting
⚙️ Automation
🛡️ Defense & Attack

..................................................................................................................................................................
