# Obtain_Capabilities:_Code_Signing_Certificates - T1588003

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Resource Development |
| MITRE TTP | T1588.003 |
| MITRE Sub-TTP | T1588.003 |
| Name | Obtain Capabilities: Code Signing Certificates |
| Log Sources to Investigate | Investigate logs from Web Proxy for unusual websites visited related to certificate providers or marketplaces that host certificates. Monitor Certificate Management Systems logs for any unexpected requests or transactions. Investigate endpoint security logs for attempts to export or access certificate store. Review logs from identity and access management systems for any suspicious behaviors or escalations of privileges related to certificate access. Example: Review logs with origins from Certificate Authority such as DigiCert, Comodo, or Symantec for unusual activity. |
| Key Indicators | Unusual or unauthorized requests for code signing certificates. Network traffic to known certificate marketplaces. Spikes or patterns in certificate signing requests by previously inactive or low-activity user accounts. Attempts to download/export certificates or access certificate stores from unusual locations or times. Failed login attempts followed by successful logins possibly indicating brute force on accounts with certificate access. |
| Questions for Analysis | Are there any recently initiated network connections to known domains associated with certificate marketplaces or exchanges? Has there been any unusual or increased activity related to certificate signing activities, particularly by accounts not typically associated with these operations? Are there any matching behaviors that correlate with suspicious attempts to access or export certificates from the store or cache? |
| Decision for Escalation | Escalate to Tier 2 if there is evidence of unauthorized certificate acquisition or export, especially if it involves high-value certificates sideloaded on key applications or systems. Also, consider escalation if there's confirmation of a breach indicating stolen or misused certificate access credentials. |
| Additional Analysis Steps for L1 | Correlate IP addresses to known threat intelligence reports regarding certificate theft. Verify the legitimacy of certificate acquisition requests with the Certificate Authority records. Check for related alerts triggered by endpoint detection systems to ensure no indicators of compromise associated with malware use of stolen certificates. |
| T2 Analyst Actions | Deeper network traffic analysis to identify hidden channels of certificate export. Validate account usage and history for users flagged in certificate acquisition logs. Collaborate with 2FA security admins to force token resets for any users suspected of unauthorized certificate actions. If necessary, engage with certificate providers to obtain detailed logs on certificate transactions/deals. |
| Containment and Further Analysis | Revoke and replace any suspected compromised certificates immediately. Enhance monitoring on exposed accounts, particularly focusing on users with certificate issuance authority. Conduct full endpoint analysis to identify potential breaches or malware making use of fraudulently obtained certificates via code signing. Collaborate with digital forensics experts to ensure full traceability and mitigation of unauthorized certificate usage. |