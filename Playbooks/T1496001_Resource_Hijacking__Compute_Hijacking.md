# Resource_Hijacking:_Compute_Hijacking - T1496001

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Impact |
| MITRE TTP | T1496.001 |
| MITRE Sub-TTP | T1496.001 |
| Name | Resource Hijacking: Compute Hijacking |
| Log Sources to Investigate | 1. System performance logs (e.g., CPU, memory utilization metrics) to identify unusual spikes or continuous high usage.<br>2. Network traffic logs to detect abnormal outbound connections, potentially to known cryptocurrency mining pools.<br>3. Application logs for unauthorized processes or applications that are not typically executed by the system. 4. Container infrastructure logs (e.g., Docker, Kubernetes) to check for unauthorized container deployments or API calls. 5. Cloud monitoring services logs (e.g., AWS CloudTrail, Azure Monitor) to identify unexplained resource consumption or instances being started in unexpected regions. |
| Key Indicators | 1. Sustained high CPU or GPU usage without corresponding legitimate processes.<br>2. Network activity with destinations linked to cryptocurrency mining pools.<br>3. Unusual spikes in resource utilization logs, lacking explanation from legitimate applications. 4. Unauthorized processes that match known cryptocurrency mining executable signatures. 5. Rapid creation and scaling of containers incongruent with normal operational patterns. |
| Questions for Analysis | 1. Are there any legitimate business processes associated with the observed resource consumption?<br>2. Is there known reputation or threat intelligence linked to the external IP addresses observed in network traffic logs?<br>3. Have there been any recent administrative changes or deployments that could explain the high resource use? 4. Are there identifiable known vulnerabilities in the environment that could have been exploited for compute hijacking? |
| Decision for Escalation | Escalate to Tier 2 if: 1. Unauthorized high CPU/GPU usage is confirmed with no valid explanation.<br>2. Network connections to known cryptocurrency mining addresses are identified.<br>3. Evidence of unauthorized container or virtual machine deployments is present. 4. Conflicting processes are terminating each other, suggesting competing malware. |
| Additional Analysis Steps for L1 | 1. Confirm abnormal resource usage through corroborating logs from cloud or on-premises monitoring tools.<br>2. Cross-reference network logs with threat intelligence sources to identify suspicious IPs or domains.<br>3. Review recent administrative logs or system change records for any unapproved actions or modifications. |
| T2 Analyst Actions | 1. Deep dive into the system and network logs to determine the full scope of the compromise.<br>2. Conduct memory analysis to identify running processes indicative of mining activities.<br>3. Collaborate with IT to isolate and inspect affected systems for forensic artifacts indicating TTP execution. |
| Containment and Further Analysis | 1. Immediately contain the affected systems by disconnecting them from the network to prevent further resource hijacking.<br>2. Remove or disable any unauthorized containers or processes identified.<br>3. Forensically preserve logs and system snapshots for detailed analysis and threat actor behavior identification. 4. Patch any identified vulnerabilities that enabled the attack and review/revise access policies to exposed APIs. 5. Monitor affected systems for recurrence post-cleanup and validate the integrity of system binaries and configurations. |