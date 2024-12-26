# Obfuscated_Files_or_Information:_Steganography - T1027003

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Defense Evasion |
| MITRE TTP | T1027.003 |
| MITRE Sub-TTP | T1027.003 |
| Name | Obfuscated Files or Information: Steganography |
| Log Sources to Investigate | To investigate the use of steganography techniques in obfuscating files and information, consider reviewing the following log sources: <br>1. **File Access Logs**: Monitor for unusual access to image, audio, video, or text files that might be used to hide data. For example, analyze logs for image files being modified or accessed in unexpected ways. <br>2. **Network Traffic Logs**: Review outbound traffic for files frequently sent to external destinations. Check for patterns of image file uploads to external IPs or domains. <br>3. **PowerShell Logs**: Since PowerShell can be used to encode and execute hidden commands, scrutinize PowerShell execution logs for any obfuscated or unexpected command activity related to images. <br>4. **Endpoint Detection and Response (EDR) Tools**: These can provide insights into processes interacting with media files in odd ways, including command execution tied to these files. |
| Key Indicators | Key indicators for this TTP include: <br>1. **Unexpected Modifications to Media Files**: Changes to image, audio, or video files that might suggest data hiding. <br>2. **Out-of-Place PowerShell Execution**: Detection of base64-encoded PowerShell scripts or suspicious commands derived from image file payloads. <br>3. **Unusual Network Activity**: Look for anomalies in file upload patterns, especially involving large or misnamed image files sent to known C2 domains or IP addresses. <br>4. **File Hashes**: Known hashes associated with steganography tools or altered media files could also indicate suspicious activity. |
| Questions for Analysis | Tier 1 analysts should ask: <br>1. Are there any recent changes or accesses to media files that are inconsistent with standard user behavior? <br>2. Does the PowerShell execution log reveal encoded commands or accesses indicating attempts to decode data from media files? <br>3. Is there any abnormal network activity that could suggest exfiltration tied to modified media files? <br>4. Are there relevant threat intelligence indicators or signatures identified that match observed activity? |
| Decision for Escalation | Escalate to Tier 2 if: <br>1. Altered media files are confirmed to be associated with network activity pointing to malicious IPs or C2 domains. <br>2. There is verified execution of encoded PowerShell commands linked with image files. <br>3. Tools or TTPs identified in logs match known steganography patterns or existing threat intelligence profiles. <br>4. Additional anomalies persist that cannot be explained by legitimate use cases or business requirements. |
| Additional Analysis Steps for L1 | Tier 1 analysts should take the following steps: <br>1. Correlate logs from multiple sources to build a clearer picture of potential activity. <br>2. Check hash values of suspect files against known malicious file databases. <br>3. Validate if file modifications align with typical user behavior or contexts. <br>4. Communicate findings with intent to gather more contextual information concerning network patterns or user activities. |
| T2 Analyst Actions | Tier 2 analysts should: <br>1. Conduct deeper forensic analysis of the modified media files, including metadata examination and extracting hidden data. <br>2. Use threat intelligence tools to match network patterns and PowerShell activity against known attack signatures. <br>3. Confirm whether the encoded data in suspect commands results in further malicious activity or links to known C2 structures. <br>4. Recommend altering firewall rules or scripts to prevent further exfiltration if confirmed. |
| Containment and Further Analysis | To contain and prevent the threat: <br>1. Isolate affected systems from the network to prevent data leakage. <br>2. Block known malicious IP addresses and domains identified during the investigation. <br>3. Update antivirus and EDR solutions with any new threat intelligence gathered during the analysis. <br>4. Conduct a complete system scan and consider restoring from known good backups if data integrity is a concern. <br>5. Communicate findings and updates to incident response teams to enhance awareness and prevent recurrence. |