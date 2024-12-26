# Hijack_Execution_Flow:_COR_PROFILER - T1574012

| Column Name | Value |
|-------------|-------|
| MITRE Tactic | Defense Evasion, Persistence, Privilege Escalation |
| MITRE TTP | T1574.012 |
| MITRE Sub-TTP | T1574.012 |
| Name | Hijack Execution Flow: COR_PROFILER |
| Log Sources to Investigate | 1. Windows Event Logs: Specifically look for events related to process creation and module loads. Event ID 4688 (Process Creation) can help identify any suspicious DLLs being loaded.<br>2. Registry Change Logs: Monitor modifications to registry keys associated with environment variables, such as HKLM\System\CurrentControlSet\Control\Session Manager\Environment.<br>3. File Monitoring Logs: Use file integrity monitoring solutions to track changes and the presence of suspicious DLLs specified in the COR_PROFILER_PATH. 4. Sysmon Logs: Check for Sysmon Event IDs 1, 7, and 10 that reflect process creation, image loaded, and registry object changes. 5. Application Logs: Review .NET application logs for unusual behavior or errors associated with CLR initialization. |
| Key Indicators | 1. Modification of the COR_PROFILER or COR_PROFILER_PATH environment variables.<br>2. Registration of unusual or unauthorized DLLs in registry paths related to COR_PROFILER.<br>3. Execution of processes with unexpected or unauthorized profilers being loaded. 4. Unrecognized or unexpected file paths specified in COR_PROFILER_PATH. 5. High frequency of .NET runtime loading events that coincide with suspicious DLL loading activity. |
| Questions for Analysis | 1. Is there a legitimate application that should be modifying the COR_PROFILER environment variable?<br>2. Are there known profiles or applications that match the loaded DLL paths?<br>3. Does the timing of the environment variable modification or DLL loading correlate with other suspicious activities? 4. Have there been any recent changes in installed .NET applications or updates that could explain the environment variable configuration? 5. Is there evidence of privilege escalation or bypass attempts coinciding with these activities? |
| Decision for Escalation | Escalate to Tier 2 if: 1. There is an unauthorized or unknown DLL registered via COR_PROFILER_PATH or seen loaded in abnormal processes.<br>2. Registry changes are detected without a legitimate software update or administrative action.<br>3. Initial investigation indicates intentional modification likely linked to malicious behavior, such as persistence or privilege escalation indicators. 4. Patterns or correlations are seen with known attack campaigns or TTPs involving COR_PROFILER. |
| Additional Analysis Steps for L1 | 1. Verify the source and legitimacy of the DLLs specified in COR_PROFILER and COR_PROFILER_PATH.<br>2. Review user and system activity logs around the time of the registry/env variable changes.<br>3. Correlate with recent patches, changes, or application installs that may explain the activity. 4. Utilize threat intelligence databases to match any suspicious DLLs or file paths against known indicators of compromise. |
| T2 Analyst Actions | 1. Perform in-depth analysis of the suspicious DLLs using static and dynamic malware analysis techniques.<br>2. Utilize endpoint detection and response (EDR) tools to trace the execution flow and identify the parent process of the malicious activity.<br>3. Engage with threat intelligence platforms to gather more context about potential campaigns involving COR_PROFILER. 4. Collaborate with the IT team to identify legitimate processes and applications that could be impacted by containment actions. |
| Containment and Further Analysis | 1. Isolate affected hosts to prevent further potential malicious actions.<br>2. Remove or quarantine suspicious DLLs to prevent further execution via COR_PROFILER.<br>3. Update and tighten security policies related to environment variable changes and .NET profiling permissions. 4. Conduct a comprehensive review of affected systems to identify any additional persistent mechanisms or lateral movement activity. 5. Update detection rules to flag similar activities in the future, based on findings from the analysis. |