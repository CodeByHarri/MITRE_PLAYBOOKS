# Command_and_Scripting_Interpreter - T1059

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Execution |
| MITRE TTP | T1059 |
| MITRE Sub-TTP | T1059 |
| Name | Command and Scripting Interpreter |
| Log Sources to Investigate | Monitor logs that capture command-line activities, such as Sysmon (Windows Event ID 1 for process creation), PowerShell logs (Windows Event ID 4104 for script blocks), Bash and Shell Command history for Linux/macOS (/var/log/auth.log and /var/log/secure), and HTTP request logs if scripts are delivered via web. Look for centralized logging solutions like SIEM that capture processes, user activities, and network traffic in context to identify suspicious execution patterns. For cross-platform scripting like Python or JavaScript, check application logs or web proxy logs if scripts are being executed through web applications. |
| Key Indicators | Unusual command-line usage, such as instances of PowerShell invoking obfuscated scripts or downloads (e.g., .Invoke-Expression or IEX), the use of 'cmd.exe' with Scripting Host commands like 'cscript' or 'wscript', or shell scripts in non-typical directories. Network traffic to unusual domains following script execution, rapid sequential command execution from the same process, or scripting engines launching unexpected applications can also be key indicators. |
| Questions for Analysis | Did the command originate from an authorized user's device? Are there any related alerts or incidents associated with the user or device? Is the command or script executing in a known folder or path typically used by trusted applications? Are there signs of execution over a remote connection? Is there any evidence of lateral movement post execution? |
| Decision for Escalation | Escalate to Tier 2 if the script or command executed shows signs of obfuscation, downloads from suspicious URLs, invokes unexpected processes or binaries, or if there's an absence of normal logging/attribution (e.g., no command line or script block logging attributed to a responsible process). If correlations show potential lateral movement or privileged account usage, escalate immediately. |
| Additional Analysis Steps for L1 | Correlate script execution with network traffic patterns to identify potential C2 communications. Verify the integrity of script logs by checking for inconsistencies or expected attribute changes. Research any external network destinations accessed. Check for recent changes in user privileges or group memberships around the timeframe of the script execution. |
| T2 Analyst Actions | Conduct deeper analysis of the processes linked to the script or command execution. Investigate file hashes against threat intelligence databases. Examine user activity for abnormal patterns or signs of compromised credentials. Cross-reference with other security tools like endpoint protection alerts or network detection systems for more contextual information on the threat. |
| Containment and Further Analysis | Isolate affected systems from the network to prevent further spread or data exfiltration. Use endpoint detection and response tools to conduct a forensic analysis of the script's origin and impact. Implement network segmentation if necessary to limit access. Report malicious domains or IPs to network administrators to block them. Document actions taken during the incident and update security policies or configurations as needed to reduce future risk. |