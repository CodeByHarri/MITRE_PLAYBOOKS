# Hardware_Additions - T1200

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Initial Access |
| MITRE TTP | T1200 |
| MITRE Sub-TTP | T1200 |
| Name | Hardware Additions |
| Log Sources to Investigate | Investigate network and endpoint logs to identify unusual activities. Examples include: USB connection logs, network traffic logs for anomalies, logs from network intrusion detection/prevention systems (IDS/IPS), and endpoint detection and response (EDR) logs. Look for unexpected devices being connected to the network or system and unusual network traffic patterns. |
| Key Indicators | Newly connected hardware devices without prior authorization, unexpected network traffic patterns potentially indicating adversary-in-the-middle activities, signs of keystroke injection, and unexplained changes to system or network configurations. Also, observe for potential DMA-related alerts indicating hardware-level access. |
| Questions for Analysis | 1. Are there any logs indicating the connection of unauthorized devices?<br>2. Is there any unusual outbound or lateral network traffic following the connection of a device?<br>3. Have any changes been made to system configurations or network settings that cannot be accounted for? 4. Is there any evidence of data exfiltration or manipulation consistent with adversary-in-the-middle activities? |
| Decision for Escalation | Escalate to Tier 2 if: 1. There is confirmation of unauthorized hardware attached to critical systems.<br>2. Network traffic indicates possible data exfiltration or adversary-in-the-middle activity.<br>3. Unusual and unexplained system behavior is detected post connection of a new device, especially in sensitive environments. |
| Additional Analysis Steps for L1 | 1. Verify the identity and purpose of connected devices with system administrators.<br>2. Cross-reference logs from EDR and IDS/IPS for any correlating incidents.<br>3. Check for any indicators of compromise in anti-malware logs. 4. Document evidence of unauthorized device usage or changes to configurations. |
| T2 Analyst Actions | 1. Conduct a comprehensive analysis of logs to confirm the presence and type of unauthorized hardware additions.<br>2. Review historical data to determine past occurrences or patterns indicating similar activities.<br>3. Coordinate with IT to inspect physical devices if necessary. 4. Analyze any captured network traffic for signs of exploitation or malicious control. |
| Containment and Further Analysis | 1. Immediately quarantine suspicious devices from the network to prevent further unauthorized access.<br>2. Conduct a full network sweep to ensure no other unauthorized devices are present.<br>3. Perform a detailed forensic analysis of impacted systems to identify potential data compromise. 4. Notify all stakeholders and possibly involve physical security teams to handle insider threats. 5. Implement stricter controls for physical device connections and enhance network monitoring for real-time alerts. |