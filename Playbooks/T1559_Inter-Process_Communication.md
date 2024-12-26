# Inter-Process_Communication - T1559

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Execution |
| MITRE TTP | T1559 |
| MITRE Sub-TTP | T1559 |
| Name | Inter-Process Communication |
| Log Sources to Investigate | Monitor system logs for IPC activities such as Windows Event Logs, specifically focusing on DCOM (Distributed Component Object Model) event logs and Dynamic Data Exchange (DDE) logs. Check application logs for abnormal inter-process communications, especially in Windows systems. In Linux environments, investigate logs capturing socket and pipe activities, such as syslog or auditing logs. Network logs can provide insights into potential Distributed Component Object Model (DCOM) abuse if remote IPC is suspected. |
| Key Indicators | Unexpected use of IPC mechanisms or processes communicating that do not typically interact. Specific event IDs related to DCOM execution, such as Event ID 10028 in Windows Event Viewer, indicating remote method invocation failures. Abnormal data flow or communication between processes not usually connected, such as a user process interacting with a high-privilege system process. |
| Questions for Analysis | Are there unusual or unfamiliar processes utilizing IPC mechanisms? Is there a pattern of IPC that deviates from the organization's baseline behavior? Have there been any recent changes in user permissions or application installations that could explain legitimate use? Are the communicating processes typically meant to interact with each other? |
| Decision for Escalation | Escalate to Tier 2 if you identify anomalous IPC usage by processes with administrative privileges, signs of DCOM exploitation, or confirmed existence of an unknown/malicious binary using IPC channels. Escalation is also warranted if there are signs of lateral movement associated with IPC abuse. |
| Additional Analysis Steps for L1 | Review relevant logs for anomalies related to IPC communications, such as unexpected process initiation or unexpected inter-process data exchange. Attempt to correlate IPC activities with user activity logs to determine if the events align with normal user behavior. Generate a timeline of IPC events to identify patterns or bursts of activity. |
| T2 Analyst Actions | Perform deeper analysis on flagged processes to determine legitimacy, including reverse engineering if necessary. Check for known malware signatures or hashes associated with suspicious binaries. Investigate potential lateral movement activities or other techniques used in conjunction with IPC exploitation, such as suspicious network connections indicating possible DCOM abuse. |
| Containment and Further Analysis | Isolate affected systems to prevent further execution of malicious IPC communications. Patch vulnerabilities in IPC mechanisms to prevent exploitation. Conduct a full forensic investigation to determine the scope and impact of IPC abuse, potentially leading to threat eradication and reinforcement of IPC security controls. |