# Acquire_Infrastructure:_Domains - T1583001

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Resource Development |
| MITRE TTP | T1583.001 |
| MITRE Sub-TTP | T1583.001 |
| Name | Acquire Infrastructure: Domains |
| Log Sources to Investigate | Investigate DNS logs for unusual domain name lookups, particularly those that are newly registered or have obscure WHOIS data. Check firewall and proxy logs to identify any traffic to known suspicious domains or newly acquired domains not white-listed. Monitor domain renewal and registration logs in cloud environments like AWS Route53 for unauthorized domain creation. Analyze WHOIS lookup logs to identify usage of privacy-protected services that might hide ownership details. |
| Key Indicators | Domains similar to known trusted domains (homoglyphs, typosquatting). Domains using internationalized domain names (IDNs) with unusual character sets (Cyrillic, Greek, etc.). Repeated attempts to access newly registered domains or domains using privacy WHOIS services. Traffic to expired domains reacquired by the adversary known to have a history of malicious behavior. |
| Questions for Analysis | Is the domain newly registered, and does it resemble important business or partner domains? Is there evidence of the domain serving malicious content according to threat intelligence? Are multiple internal users accessing this domain without a clear business purpose? Was the domain registered using privacy or obscured WHOIS details? |
| Decision for Escalation | Escalate to Tier 2 if a domain is newly registered and matches patterns of known spoofed business domains. Escalate if the domain serves content flagged as malicious by threat intelligence or if internal users report phishing attempts linked to the domain. |
| Additional Analysis Steps for L1 | Verify the domain's registration date and WHOIS details. Cross-reference domain with threat intelligence repositories for known malicious activity. Confirm if the domain is expected in the organization's domain traffic patterns by checking with business units. Look for any anomaly in traffic volume or user reports related to the domain. |
| T2 Analyst Actions | Perform deeper analysis using sandbox environments to examine domain traffic and content. Utilize threat intelligence platforms to assess if similar domains have been used in recent campaigns. Engage with cloud service logs like AWS CloudTrail to assess if new domains are being registered within compromised accounts. Check for any anomalous patterns in user account behavior that may correlate with domain access. |
| Containment and Further Analysis | If malicious activity is confirmed, update security solutions to block the domain across all endpoints. Conduct internal communications to inform stakeholders about the threat and ongoing enforcement actions. Follow up with domain name service providers and law enforcement if needed to request domain takedown. Log comprehensive incident reports and lessons learned sessions to improve detection and quick response for future incidents. |