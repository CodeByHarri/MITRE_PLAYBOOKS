# Steal_or_Forge_Kerberos_Tickets:_Kerberoasting - T1558003

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Credential Access |
| MITRE TTP | T1558.003 |
| MITRE Sub-TTP | T1558.003 |
| Name | Steal or Forge Kerberos Tickets: Kerberoasting |
| Log Sources to Investigate | 1. Windows Security Event Logs: Look for event IDs 4768 (A Kerberos authentication ticket (TGT) was granted) and 4769 (A Kerberos service ticket was granted) to identify TGS requests.<br>2. Network Traffic Monitoring: Analyze traffic specifically to and from domain controllers (DCs) for abnormal TGS-REQ and TGS-REP activity.<br>3. Authentication Logs: Review for multiple requests for TGS tickets with different SPNs or unusually high volume of such requests. 4. Active Directory Logs: Track service principal name requests that might not align with normal business operations. |
| Key Indicators | 1. A high number of TGS-REQs for SPNs being performed by a single user account.<br>2. Anomalies in the volume and frequency of Kerberos ticket requests compared to baseline behavior.<br>3. Detection of RC4 hashes being retrieved or exported. 4. Unusual changes in Active Directory, especially in service accounts' SPNs. |
| Questions for Analysis | 1. Is the account making the Kerberos ticket requests legitimate, and does its activity align with its normal behavior and role?<br>2. Is there an unusually high number of service tickets being requested for various SPNs?<br>3. Are there any related logs indicating account compromise or lateral movement attempts? 4. Is there any evidence of changes to SPNs in the Active Directory preceding this activity? |
| Decision for Escalation | Escalate to Tier 2 if: 1. The account in question has no history of making TGS requests, or its volume is significantly higher than usual.<br>2. There are correlating security alerts such as brute force attempts or other signs of compromised credentials.<br>3. Multiple SPNs are being targeted by a single account without any business justification. |
| Additional Analysis Steps for L1 | 1. Correlate the identified TGS requests with known business operations to rule out legitimate use cases.<br>2. Verify if the user accounts engaged in the activity have any associated security alerts or incidents.<br>3. Check for patterns in TGS-REQ and TGS-REP activities to identify potential brute force attempts. |
| T2 Analyst Actions | 1. Conduct deeper analysis on the Kerberos ticket requests by assessing associated network traffic logs for irregularities.<br>2. Review recent changes in user permissions or SPN configurations, particularly for high-value service accounts.<br>3. Analyze any dumped credentials for anomalies or known compromises. 4. Validate if suspicious activity aligns with known attack patterns related to Kerberoasting. |
| Containment and Further Analysis | 1. Immediately disable or break confidentiality for accounts associated with suspicious TGS requests.<br>2. Initiate password resets for potentially compromised service accounts.<br>3. Deploy network segmentation to limit potential lateral movement. 4. Use forensic tools to analyze memory or disk for dumped hashes linked to Kerberoasting. 5. Engage with IT teams to assess potential impact on business operations and notify them of necessary changes. 6. Implement additional monitoring and alerting for future TGS-REQ anomalies. |