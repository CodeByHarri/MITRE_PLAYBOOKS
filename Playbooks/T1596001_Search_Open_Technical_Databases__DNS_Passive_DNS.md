# Search_Open_Technical_Databases:_DNS_Passive_DNS - T1596001

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Reconnaissance |
| MITRE TTP | T1596.001 |
| MITRE Sub-TTP | T1596.001 |
| Name | Search Open Technical Databases: DNS/Passive DNS |
| Log Sources to Investigate | DNS query logs and Passive DNS logs should be thoroughly investigated for unusual activity. Examples include DNS query tools like dnstop, dnssnoop, as well as logs from DNS servers themselves. Additionally, network traffic logs, especially any traffic involving DNS records or services, should be scrutinized for patterns indicative of bulk querying or misconfigurations. |
| Key Indicators | Presence of bulk DNS queries originating from a single IP or host, a spike in DNS traffic volume, particularly to passive DNS providers. Indicators also include requests for DNS records that are usually not accessed, a pattern of failed DNS lookups, and unexpected external IP addresses querying internal DNS misconfigurations. |
| Questions for Analysis | Are there multiple DNS queries to passive DNS providers from the same host? Is there a sudden increase in the number of DNS lookups or queries for records that are typically unchanged? Are there any anomalies in DNS queries that correspond to sensitive subdomains or services? Are there DNS requests made from unexpected or suspicious external IPs? |
| Decision for Escalation | Escalate the detection to Tier 2 if there is evidence of targeted DNS queries focusing on internal or sensitive domains, if passive DNS queries coincide with other suspicious network activities, and/or if DNS misconfigurations are observed being actively queried. Suspicious patterns like bulk DNS recon querying should be a key factor for escalation. |
| Additional Analysis Steps for L1 | Check DNS logs for frequent queries to passive DNS services by the same host. Validate any anomalies against known benign processes, and assess whether there is a legitimate need for such queries. Cross-reference passive DNS queries with any alerts from intrusion detection systems for relevant context. |
| T2 Analyst Actions | Conduct deeper investigation of any anomalies in DNS query patterns using threat intelligence to recognize potential adversary fingerprints. Look into passive DNS databases to identify historical DNS lookup patterns that could indicate preparatory work for further attacks. Evaluate DNS configuration settings for vulnerabilities or misconfigurations. Trace the originating IP addresses of suspicious queries to assess if they are part of known threat actor infrastructure. |
| Containment and Further Analysis | Block identified malicious IPs from accessing DNS services. Correct any DNS misconfigurations to prevent information leaks. Implement further network segmentation to protect sensitive DNS records. Monitor DNS queries post-action to ensure that anomalous activity ceases. Conduct a review of the incident to improve detection rules and incident response playbooks. Engage with threat intelligence services to provide updates and insights on the tools, techniques, and procedures observed. |