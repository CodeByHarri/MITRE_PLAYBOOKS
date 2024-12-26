# Account_Manipulation:_Device_Registration - T1098005

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Persistence, Privilege Escalation |
| MITRE TTP | T1098.005 |
| MITRE Sub-TTP | T1098.005 |
| Name | Account Manipulation: Device Registration |
| Log Sources to Investigate | Monitor MFA system logs, specifically Duo or Okta, for suspicious device enrollment activities. Check Microsoft Intune and Entra ID logs for recent device registrations. Look into Active Directory logs for sign-ins from new devices or locations. Analyze email gateway logs for potential internal spearphishing campaigns originated from newly registered devices. |
| Key Indicators | 1. Unusual device registration activities in MFA systems linked to dormant or high-profile accounts.<br>2. First-time device enrollments that do not fit the routine MFA self-enrollment patterns.<br>3. Multiple device registrations in a short time span, which could indicate a Service Exhaustion Flood. 4. New devices accessing sensitive resources without prior authorization history. 5. Sudden surge in intra-organizational emails from newly registered devices. |
| Questions for Analysis | 1. Does the device registration activity align with the user's typical behavior?<br>2. Were there any anomalies in the user's recent login history, such as unusual locations or times?<br>3. Is there evidence of compromised user credentials being abused? 4. Are there any concurrent or related incidents reported that might suggest coordinated activity? 5. Have there been any recent policy changes in MFA or device registration processes that might explain the activity? |
| Decision for Escalation | Escalate to Tier 2 if the device registration is for a high-profile account, involves a large number of devices in a short period, or if there is any indication of simultaneous credential compromise or related suspicious activities. Escalation is also warranted if new devices are accessing high-value resources or when internal spearphishing signs are detected. |
| Additional Analysis Steps for L1 | 1. Verify the legitimacy of the new device registration by contacting the affected user.<br>2. Cross-reference the device's IP address and location data with known user activity and login history.<br>3. Check for related alerts or anomalies in login attempts around the device registration time. 4. Review recent changes in MFA device enrollment policies for any potential security gaps. |
| T2 Analyst Actions | 1. Conduct a deeper investigation into account activity, focusing on any evidence of compromise.<br>2. Analyze network traffic associated with the newly registered device for any suspicious data exfiltration attempts.<br>3. Review user account permissions and recent activities for any signs of privilege abuse. 4. Coordinate with IT to re-assess and possibly tighten MFA policies and device management controls. |
| Containment and Further Analysis | 1. If suspicious activity is confirmed, immediately disable the registered device and reset the affected user's credentials.<br>2. Implement a temporary block on further device enrollments to prevent escalation.<br>3. Conduct a retrospective analysis of similar past events to identify any potential patterns or overlooked threats. 4. Educate users on recognizing and reporting potential phishing attempts or credential theft. |