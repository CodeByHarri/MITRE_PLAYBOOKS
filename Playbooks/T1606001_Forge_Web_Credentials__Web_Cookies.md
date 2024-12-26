# Forge_Web_Credentials:_Web_Cookies - T1606001

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Credential Access |
| MITRE TTP | T1606.001 |
| MITRE Sub-TTP | T1606.001 |
| Name | Forge Web Credentials: Web Cookies |
| Log Sources to Investigate | Web server logs, especially those capturing authentication activity; Application logs from SaaS applications; Network traffic logs from both endpoints and network appliances; Security information and event management (SIEM) platforms for correlating anomalies; Endpoint detection and response (EDR) logs to analyze local processes and file access; Examples include Apache or Nginx access logs, Azure AD logs, or any authentication API usage logs. |
| Key Indicators | Unusual spikes in session creation or authentication attempts; Session cookies being used at odd times or from unexpected IP addresses/geographical locations; Multiple session creations from the same user account in a short time frame; Anomalies in user-agent strings associated with session cookies; Presence of known cookie forging tool patterns, such as those mimicking common browser strings with minor deviations. |
| Questions for Analysis | Are there anomalies in the time and location of new session activities for specific users? Do the user-agent strings in session creation logs match expected patterns for those users? Are there known indicators of cookie forging tools in the logs? Are there any known vulnerabilities in our application or login mechanisms that could facilitate cookie forging? |
| Decision for Escalation | Escalate to Tier 2 if there is evidence of sessions being created or used by a single account from multiple locations simultaneously; if forged cookie patterns consistent with malicious tools are detected; or if abnormal account activities suggest potential unauthorized access. Immediate escalation is warranted if any privilege escalation or sensitive data access is detected following a suspected forged session. |
| Additional Analysis Steps for L1 | Correlate authentication logins with expected historical patterns for the user; Verify all IP addresses accessing the same session cookies; Check for unexpected user-agent strings in logs; Look for recent failed login attempts preceding successful ones from the same IP addresses that may indicate prior reconnaissance. |
| T2 Analyst Actions | Conduct deeper analysis into suspicious IP addresses or user-agents; Examine logs for additional indicators of lateral movement or privilege escalation; Validate the absence of legitimate user confirmation for access anomalies; Utilize threat intelligence feeds to match IPs or patterns against known threat actors or campaigns. |
| Containment and Further Analysis | Revoke affected sessions and force full re-authentication for impacted accounts; If ongoing compromise is suspected, enforce a password reset and strong multi-factor authentication (MFA); Monitor for further anomalous behavior post-mitigation; Consider deploying anomaly detection solutions to better identify potential future forgery attempts; Conduct a post-incident review to improve web security configurations and employ additional logging if necessary. |