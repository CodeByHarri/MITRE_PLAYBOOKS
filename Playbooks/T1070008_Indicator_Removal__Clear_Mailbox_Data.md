# Indicator_Removal:_Clear_Mailbox_Data - T1070008

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Defense Evasion |
| MITRE TTP | T1070.008 |
| MITRE Sub-TTP | T1070.008 |
| Name | Indicator Removal: Clear Mailbox Data |
| Log Sources to Investigate | Investigate email server logs, such as Microsoft Exchange or any other mail server application logs, for mailbox export and deletion activities. Look into PowerShell logs for commands like Remove-MailboxExportRequest as well as audit logs for API interactions related to email applications. On Linux/macOS, audit syslogs that capture usage of command line utilities like 'mail' and interactions from scripts such as AppleScript. Also, review organization-wide transport rule logs that might indicate changes related to handling suspicious emails. |
| Key Indicators | Unusual mailbox export or deletion activity detected in email server logs, especially deletions following export requests. Execution of specific PowerShell commands associated with mailbox manipulation. Trace of specific CMD or shell utility usage on Unix-like systems for modifying or deleting emails. Any changes to transport rules that may correlate with phishing indicators. Anomalous or new application/API interactions possibly indicative of unauthorized email data access or manipulation. |
| Questions for Analysis | Is there a pattern of mailbox export followed by immediate deletion? Do the PowerShell or command line invocations match legitimate administrative activity or do they appear out of context? Was the activity conducted by a user account that usually does not perform such operations? Are there unusual changes in transport rules logged coinciding with detected suspicious emails? |
| Decision for Escalation | Escalate to Tier 2 if mailbox export and deletion activities lack legitimate justification, involve scripts or tools typically not used by authorized personnel, or are associated with known threat patterns. If suspicious changes in transport rules are discovered without accompanying operational necessity, escalate the incident. |
| Additional Analysis Steps for L1 | Verify the identity and access behavior of the account that performed the email-related operations. Check whether the email manipulation correlates with other network or system anomalies. Look for recent account password changes or login attempts from unusual locations related to the involved accounts. |
| T2 Analyst Actions | Conduct deeper investigation into the email server logs to map the timeline and sequence of events. Validate the legitimacy of any scripts or automated processes performing deletions. Cross-reference user activity across systems to identify possible compromise or misuse. Engage with impacted business units for potential verification of deviations from regular email management tasks. |
| Containment and Further Analysis | Revoke access if account compromise is suspected and enforce a password reset. Temporarily disable any suspicious automated tasks while further investigation is conducted. Extract and safely store email server log data for thorough forensic analysis. Work with IT and security teams to restore and preserve the manipulated mail data where possible. Enhance logging and monitoring for repeat detection and prevention. |