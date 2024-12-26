# Remote_Services:_VNC - T1021005

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Lateral Movement |
| MITRE TTP | T1021.005 |
| MITRE Sub-TTP | T1021.005 |
| Name | Remote Services: VNC |
| Log Sources to Investigate | Collect logs from systems that support VNC connections, specifically authentication logs, connection logs, and system activity logs. Examples include:<br>1. Network logs: Capture VNC traffic, look for unexpected or unusual IP addresses accessing VNC services.<br>2. Authentication logs: Check for successful and failed login attempts, specifically focusing on anomalies, such as brute force attempts.<br>3. System logs: Monitor changes in processes, files accessed, and any command executions that occurred during VNC sessions.<br>4. Application logs: Capture VNC server and client logs to identify unauthorized access patterns. |
| Key Indicators | 1. Unusual account logins during non-business hours from external IP addresses or unauthorized locations.<br>2. Multiple failed login attempts may indicate a brute force attack.<br>3. Unexpected or unauthorized applications or processes initiated during VNC sessions.<br>4. Anomalous traffic patterns related to systems with VNC enabled, especially if coupled with data transfer activity. |
| Questions for Analysis | 1. Are login attempts to VNC services coming from known, authorized IP addresses?<br>2. Are there any patterns in login attempts that suggest brute force techniques?<br>3. Do the actions taken during VNC sessions match expected user behavior and times?<br>4. Is there any evidence of data exfiltration during these VNC sessions? |
| Decision for Escalation | Escalate to T2 if:<br>1. There is evidence of suspicious or unauthorized access to VNC services.<br>2. Indicators of brute force attempts or multiple failed logins are detected.<br>3. Any anomalous data transfer activity is observed during a VNC session.<br>4. Any suspicious changes in system configurations or files due to VNC actions. |
| Additional Analysis Steps for L1 | 1. Verify if the VNC service is configured securely (e.g., password protection, network restrictions).<br>2. Cross-reference VNC activity with known user work patterns to identify anomalies.<br>3. Check recent changes in user accounts or credentials specific to the system(s) involved.<br>4. Verify if VNC connection logs align with regular operational needs and schedules. |
| T2 Analyst Actions | 1. Perform deeper forensic analysis on VNC session metadata and any associated logs.<br>2. Analyze network flow data to trace the origin of VNC connections.<br>3. Consult with the affected user(s) to confirm if VNC access was legitimate.<br>4. Review firewall and network configuration settings for potential misconfigurations.<br>5. Correlate VNC activity with other security alerts or incidents to identify broader patterns. |
| Containment and Further Analysis | 1. If unauthorized VNC access is confirmed, disconnect affected devices from the network to prevent further malicious activity.<br>2. Change passwords and monitoring accounts that were accessed during the suspicious VNC session.<br>3. Review and enhance VNC configurations to ensure tighter security controls.<br>4. Deploy network segmentation or updated access policies to limit VNC access where possible.<br>5. Conduct a review of external access policies to strengthen remote service security posture.<br>6. Recommend periodic reviews and penetration testing of VNC services. |