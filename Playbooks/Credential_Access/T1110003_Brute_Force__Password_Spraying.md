# Brute_Force:_Password_Spraying - T1110003

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Credential Access |
| MITRE TTP | T1110.003 |
| MITRE Sub-TTP | T1110.003 |
| Name | Brute Force: Password Spraying |
| Log Sources to Investigate | Examine authentication logs from domain controllers for failed logon attempts (Event ID 4625 in Windows Security logs), access logs from targeted services such as SSH, FTP, and RDP concentrators, application logs from cloud services like Office 365 (Azure AD sign-in logs), and firewall logs for unusual patterns of access or connection attempts on management ports. Examples include Windows Event Viewer, Azure AD logs, and network intrusion detection systems (NIDS). |
| Key Indicators | Multiple failed login attempts with the same password across different accounts (e.g., Event ID 4625 in Windows). High volume of authentication attempts from a single IP address within a short time frame. Unusual attempts to access management services on non-standard or unusual hours, especially from foreign or unknown IP addresses. Attempts targeting known, external-facing applications like Office 365. |
| Questions for Analysis | Are the failed login attempts distributed across multiple accounts rather than focusing on one? Is the same password or a small set of passwords being tried against various accounts? Is there a common IP source for these attempts? Are there anomalies in login attempts such as unusual time frames or geographic locations? |
| Decision for Escalation | Escalate to Tier 2 if multiple accounts experience repeated failed login attempts from a single IP. Consider the scale and regularity of the attempts, especially if they target different protocols or services. Escalate if unusual network traffic patterns are corroborated with logon events, or once legitimate accounts show a compromise after password spraying activity. |
| Additional Analysis Steps for L1 | Correlate logs across different sources to verify patterns of failed login attempts, focusing on identifying common characteristics across impacted accounts. Review network-level logs to determine if there are anomalous access patterns suggesting external probing. Report findings to Tier 2 for deeper analysis. |
| T2 Analyst Actions | Conduct a thorough examination of affected accounts and conduct behavioral analysis on any successfully authenticated sessions after suspected password spraying attempts. Analyze the source IP addresses in threat intelligence databases to check for known malicious actors. Collaborate with IT to perform deeper analysis on affected machines or networks using endpoint detection and response (EDR) tools. |
| Containment and Further Analysis | Advise for temporary blocking of suspicious IPs or IP ranges identified as sources of password spraying attempts. Ensure MFA is enforced on all accounts where possible. Evaluate current password policies and educate users about strong password guidance. Consider implementing Intrusion Prevention Systems (IPS) and configure alerts for unusual authentication attempts on sensitive services. |