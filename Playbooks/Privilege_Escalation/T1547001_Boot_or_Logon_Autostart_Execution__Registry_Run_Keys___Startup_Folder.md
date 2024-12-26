# Boot_or_Logon_Autostart_Execution:_Registry_Run_Keys___Startup_Folder - T1547001

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Persistence, Privilege Escalation |
| MITRE TTP | T1547.001 |
| MITRE Sub-TTP | T1547.001 |
| Name | Boot or Logon Autostart Execution: Registry Run Keys / Startup Folder |
| Log Sources to Investigate | Investigate log sources such as the Windows Security Event Logs for any process creations (Event ID 4688) that reference suspicious files in known startup locations, or changes to critical Registry keys (Event IDs 4656, 4663 for Registry object access and modifications). Look at Sysmon events particularly for Event ID 11, which logs Registry key modifications, and Event ID 13 for image loaded. Monitor file system logs for unauthorized file creation in startup folders. Collect data from Endpoint Detection and Response (EDR) tools that track changes to startup configurations and registry modifications. |
| Key Indicators | Key indicators include unusual or unauthorized changes to Registry run keys like HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Run. Detection of new or suspicious files in startup folders, such as C:\ProgramData\Microsoft\Windows\Start Menu\Programs\StartUp. Identification of processes being started from uncommon file paths or with filenames designed to masquerade as legitimate, e.g., svchost.exe but located outside of the System32 directory. |
| Questions for Analysis | Is the modified Registry key or startup folder entry associated with known legitimate software updates or installations? Have any related files been recently added to the system, and are they signed or from a trusted source? Is there a pattern of similar modifications across other systems in the network indicating widespread infection? Are there any known vulnerabilities or exploits related to the observed behavior? |
| Decision for Escalation | Escalate if the Registry or startup changes cannot be linked to legitimate software or known updates, or if files involved are unsigned or from untrusted sources. Escalate further if analysis identifies known malware or persistence mechanisms, or if there is evidence of lateral movement in the network. Escalate if there is an ongoing exfiltration or if the environment shows other symptoms of compromise. |
| Additional Analysis Steps for L1 | Cross-reference file hashes with threat intelligence databases to identify known malware. Use network monitoring to check for unusual outbound connections originating from the affected host. Verify user activity logs to confirm whether the user initiated any recent installations or updates. Check for execution of the suspicious processes across the environment using EDR solutions. |
| T2 Analyst Actions | Perform deeper analysis on suspicious files using malware analysis tools in a controlled environment. Conduct network analysis to examine any command and control (C2) communications. Analyze system performance and network traffic for signs of additional malicious activity. Utilize heuristics and behavior analysis to determine if the activity matches known techniques used by APT groups. |
| Containment and Further Analysis | Contain the affected systems by isolating them from the network. Remove unauthorized Registry changes or startup items using administrative tools. Ensure backup mechanisms are in place before remediation. Perform a comprehensive scan of the system using updated antivirus and EDR tools. Conduct post-incident analysis to identify potential gaps in security and implement improvements in monitoring and detection capabilities. |