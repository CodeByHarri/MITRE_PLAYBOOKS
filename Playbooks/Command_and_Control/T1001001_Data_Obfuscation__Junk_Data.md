# Data_Obfuscation:_Junk_Data - T1001001

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Command and Control |
| MITRE TTP | T1001.001 |
| MITRE Sub-TTP | T1001.001 |
| Name | Data Obfuscation: Junk Data |
| Log Sources to Investigate | Network traffic logs, firewall logs, and intrusion detection/prevention systems (IDS/IPS) are primary sources. These logs should capture packet data that could reveal anomalies in protocol communications, such as unusually lengthy payloads or packets with non-standard protocol structures that could indicate junk data. Examples of relevant logs include Zeek/Bro logs, Suricata alerts, and NetFlow data from routers and switches. |
| Key Indicators | 1. Unusually large packets or data bursts in traffic likely to be command and control (C2) communications.<br>2. Inconsistencies or anomalies in protocol headers or payloads - such as repeated patterns, non-standard formatting, or unexpected characters interspersed with legitimate data.<br>3. Frequent small increments in data size that do not match typical usage patterns for the application/protocol. 4. Known indicators of compromise (IoCs) from threat intelligence feeds particularly related to protocols commonly used for C2 such as HTTP, HTTPS, or DNS. |
| Questions for Analysis | 1. Is there an unexpected increase in outbound network traffic that cannot be attributed to legitimate user activity?<br>2. Are there any specific endpoints showing repeated communication attempts containing anomalous data structures?<br>3. Do the detected anomalies correlate with any known malicious IPs or domains from threat intelligence databases? 4. Are any internal hosts communicating over protocols they shouldn't be using according to established baselines? |
| Decision for Escalation | Escalate to Tier 2 if: 1. Anomalous traffic is confirmed to match known malicious patterns after initial analysis.<br>2. Traffic appears to be communicating with known command and control servers or suspicious external IP addresses.<br>3. There is evidence that anomalies observed are part of a coordinated attack or match profiles of advanced persistent threats (APTs). |
| Additional Analysis Steps for L1 | 1. Conduct deep packet inspection to identify and categorize the nature of anomalies within the data payloads.<br>2. Cross-reference network activity with existing threat intelligence services to identify any communications to known bad actors.<br>3. Review system logs of communicating endpoints for suspicious activities around the same time anomalies were detected. |
| T2 Analyst Actions | 1. Perform a detailed analysis of the affected endpoints to identify potential exploitation of vulnerabilities.<br>2. Use advanced threat detection tools to correlate network anomalies with endpoint behaviors.<br>3. Investigate any persisted modifications or services that may suggest ongoing compromise, such as rootkits or malicious processes. 4. Develop a more comprehensive assessment of the lateral movement or data exfiltration if detected. |
| Containment and Further Analysis | 1. Isolate affected systems from the network to prevent further compromise.<br>2. Conduct a forensic examination of isolated systems to identify the root cause and method of intrusion.<br>3. Patch systems and update security configurations to prevent recurrence. 4. Monitor for recurrence of similar patterns and adjust detection rules to improve early detection of similar techniques in future attacks. |