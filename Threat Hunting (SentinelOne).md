
## Incident Analysis: Inbound RDP Connection and Suspected Compromise

An external RDP connection was established to an internal endpoint, indicating a potential initial access vector. Activities suggest a multi-stage attack involving remote execution, lateral movement, persistence, and data exfiltration.

### Observed Attack Chain:

* **Inbound RDP Connection:** An external IP address connected to an internal endpoint via **port 3389 (RDP)**. This is an initial observation as RDP should ideally be restricted from external access or secured with strong authentication and multi-factor authentication (MFA).

* **PowerShell Execution and External Communication:** Following the RDP connection, **`powershell.exe`** was launched. A command was executed via PowerShell to connect to an external website, attempting to download or execute a script named **archive.zip**. This suggests an attempt to retrieve additional malicious tooling or establish command and control.

* **PsExec Attempt and Lateral Movement:** An attempt was made to use **`PsExec`**. Although `PsExec` aborted, a second internal endpoint received incoming connections on **ports 135 (MSRPC)** and **445 (SMB/NetBIOS)** from the first compromised endpoint. This indicates an attempt at **lateral movement** using administrative shares or services, common in post-exploitation phases. Then, **`cmd.exe`** was launched on the second endpoint, suggesting successful code execution or further reconnaissance.

* **Persistence and Exfiltration:**
    * **Scheduled Task Creation:** A scheduled task was created, likely for **persistence** to maintain access to the compromised system even after reboots or user logoffs.
    * **Data Exfiltration Attempt:** **`powershell.exe`** connected to an external IP address over **port 21 (FTP)**. This suggests an attempt to **exfiltrate data** from the compromised network. FTP is often used by attackers for data transfer due to its common allowance through firewalls and its clear-text nature for easy analysis (though attackers often encrypt data before exfiltration).

### Next Steps for Investigation and Remediation:

1.  **Isolate Compromised Endpoints:** Isolation both identifies endpoints from the network to prevent further compromise or exfiltration.
2.  **Forensic Image Creation:** Create forensic images of both compromised endpoints for detailed analysis.
3.  **Log Analysis:**
    * Review RDP logs for successful and failed login attempts, focusing on the source IP of the initial connection.
    * Analyze PowerShell logs (Module Logging, Script Block Logging, Transcription) for the exact commands executed.
    * Examine network logs (firewall, proxy, DNS) for connections to the external IP addresses and `archiv`.
    * Review event logs for scheduled task creation, `PsExec` activity, and `cmd.exe` launches.
4.  **Threat Intelligence:** Research the external IP addresses and domain `archiv` for known malicious associations.
5.  **Malware Analysis:** Analyze any downloaded files or scripts (e.g., `archiv.zio`) to understand their capabilities.
6.  **User Account Compromise:** Investigate if any user accounts were compromised during the RDP connection or subsequent lateral movement.
7.  **Vulnerability Assessment:** Identify how the initial RDP connection was made (weak credentials, exposed RDP port, unpatched vulnerability).
8.  **Remediation:** Implement remediation steps, including patching vulnerabilities, reinforcing RDP security, resetting compromised credentials, and deploying monitoring.

---
