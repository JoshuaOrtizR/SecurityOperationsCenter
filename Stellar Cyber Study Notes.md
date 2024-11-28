### Stellar Cyber Study Notes

**Case Score **
* **Phases:** Detection, Analysis, Response
* **Case Investigation Tools:**
  * **Key Investigation Elements:**
    * **Questions to Address:** Who, What, When, Where, Severity, Status
    * **Associated Alerts:** Chronological alerts, scanner behaviors, exploration patterns, bad behaviors
    * **Kill Chain:** Initial attempts, persistent foothold, exploration, propagation, exfiltration & impact, propagation via administrative privileges
  * **Features:**
    * **Scanner Behavior Analysis:** Encrypted command and control behaviors, hover for detailed context
  * **Response and Actions:** Contain the host, block IPs, disable users, run custom scripts
  * **Case Activity View:** IP blocking details, Evidence Locker (attach files: CSV, PDF, EML)

**Alert Management**
* **Custom Alerts:** Curate components to detect and respond to potential threats, employs Machine Learning (ML), fidelity scoring, severity levels, and threat intelligence
* **Alert Metrics and Views:** Organized by type and severity, metrics showing critical alerts, customizable table views for arranging and filtering alerts, grouping and correlating alerts to reduce redundancy
* **Alert Correlation:** Triage based on risk tolerance, escalate or combine alerts into cases or queues

**Investigation and Threat Hunting**
* **View all alerts across the system for commonalities**
* **Create custom cases or consolidate them into actionable steps**
* **Leverages the MITRE ATT&CK Framework** (Example: DLL Overwrite scenarios)

**Key Operational Views**
* **Kill Chain View:** Tracks the full lifecycle of an attack (Initial Attempt → Persistent Foothold → Propagation → Impact)
* **Alerts View:** Organized display of all alert types for efficient triage
* **Threat Hunting View:** Deep investigation into behaviors and anomalies

**Notes**
* **Prioritize and address all kill chain stages equally**
* **Focus on the lifecycle of attacks:**
  * **Initial Attempts:** Identify early indicators of compromise (IOC)
  * **Persistent Foothold:** Detect and disrupt persistent mechanisms
  * **Propagation:** Limit lateral movement and data exfiltration
  * **Impact:** Mitigate damage and restore systems

