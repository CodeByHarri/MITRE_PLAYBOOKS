# Obfuscated_Files_or_Information:_Dynamic_API_Resolution - T1027007

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Defense Evasion |
| MITRE TTP | T1027.007 |
| MITRE Sub-TTP | T1027.007 |
| Name | Obfuscated Files or Information: Dynamic API Resolution |
| Log Sources to Investigate | Investigate logs from Endpoint Detection and Response (EDR) solutions, which can track API function calls and their resolutions. Look at process execution logs to identify unusual use of functions like GetProcAddress() and LoadLibrary(). Examine logs from file integrity monitoring systems that can detect changes in executable files’ IATs. Additionally, scrutinize network logs for anomalous behavior potentially correlated with dynamically loaded modules or functions. |
| Key Indicators | Presence of obfuscated or hashed API function names within binaries. Unusual frequency or patterns of calls to GetProcAddress() or LoadLibrary() by processes that do not normally use these functions. Suspicious changes or anomalies in IATs of processes known to be targeted by malware or during periods of high threat activity. Existence of strings in the memory that are decoded or decrypted during runtime. |
| Questions for Analysis | Is the process exhibiting behaviors consistent with known benign applications, or is it out of character? Are the API calls associated with known and legitimate modules, or do they point to non-standard libraries? Has the process exhibited similar behavior before without malicious activity, or is this a new pattern? |
| Decision for Escalation | Escalate to Tier 2 if API function calls are observed in processes not typically associated with dynamic API resolution. If decoded strings reveal known malicious functions or hashes associated with existing threat intelligence, escalate immediately. Also, escalate if process execution coincides with known indicators of compromise (IOCs) or if linked modules are considered suspect. |
| Additional Analysis Steps for L1 | Check for known hashes of function names against threat intelligence databases to discern malicious intent. Review the process and parent-child relationships to see if a legitimate process could have been hijacked. Temporarily quarantine the suspicious binary for further analysis without disrupting the entire system. |
| T2 Analyst Actions | Conduct an in-depth examination of the memory space of the suspected process, looking for dynamically resolved API calls. Use reverse engineering techniques to analyze suspect binaries for further obfuscation or encrypted API strings. Collaborate with threat intelligence teams to match function hashes or resolved APIs against latest threat actor TTPs. |
| Containment and Further Analysis | Isolate the affected host from the network to prevent lateral movement and data exfiltration. Perform deeper forensic analysis of the file system and registry changes related to the process. Deploy YARA rules for automated detection of similar activity across the network. Furthermore, prepare and implement a remediation plan in case the threat is part of a broader compromise. |