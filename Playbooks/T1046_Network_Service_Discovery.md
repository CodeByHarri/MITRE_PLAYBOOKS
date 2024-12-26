# Network_Service_Discovery - T1046

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Discovery |
| MITRE TTP | T1046 |
| MITRE Sub-TTP | T1046 |
| Name | Network Service Discovery |
| Log Sources to Investigate | Network traffic logs, especially those from intrusion detection systems (IDS) and intrusion prevention systems (IPS), can be pivotal. Monitor for abnormal increases in traffic from a single host, particularly to a wide range of ports, which is indicative of network scanning. Collect logs from firewalls and network devices to identify unauthorized service access attempts. In cloud environments, cloud service provider logs (such as AWS CloudTrail or Azure Activity Logs) may reveal attempts to probe services. Additionally, endpoint logs on macOS may show usages of commands like 'dns-sd' and could include logs from security tools that monitor for Bonjour service activities. |
| Key Indicators | Unusual network scan patterns such as SYN requests to multiple IP addresses across many ports. Use of 'dns-sd' command in macOS logs indicating multicast DNS queries, particularly looking for services like '_ssh._tcp'. Significant access to services shortly after instances of network scanning. In cloud environments, activities such as attempts to list resources or services without authorization. |
| Questions for Analysis | Has there been unusual network traffic originating from a particular host? Have there been any detections correlated with the use of the 'dns-sd' command on macOS systems? Are there unauthorized attempts to access services or network nodes? Are the discovered services critical or have known vulnerabilities? |
| Decision for Escalation | Escalate to Tier 2 if there is confirmed evidence of network scans from external or unauthorized internal sources, if there are detected successful connections to sensitive services which could lead to exploitation, or if the scanning activity correlates with other suspicious or malicious behaviors. |
| Additional Analysis Steps for L1 | Collect and review logs for the time frame around the detected scanning activity. Validate whether the network scan originated from internal legitimate software or a known scheduled scan. Cross-reference detected network scans with vulnerability databases to assess if any exposed services have known vulnerabilities. |
| T2 Analyst Actions | Conduct a deeper network traffic analysis to confirm the scope and source of the scan. Analyze related endpoint security alerts to determine the initial point of compromise. Investigate whether any unauthorized access was achieved as a result of the discovered services. If the scanning activity was from within the organization, identify the user and investigate any associated activities or intentions. |
| Containment and Further Analysis | Block the scanning IP address on the firewall to prevent further reconnaissance activities. If internal, quarantine the compromised system to prevent lateral movement. Conduct a thorough vulnerability assessment of all discovered services; implement patches or mitigations for high-risk services. Review security policies and configurations to ensure any vulnerabilities related to unauthorized service discovery or exploitation are addressed. |