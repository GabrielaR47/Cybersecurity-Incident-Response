
# Incident Report: Insider Threat & Impersonation Analysis

## 1. Incident Overview
*   **Objective:** Investigate a potential insider threat and impersonation claim by correlating network traffic, DHCP logs, and system security logs to attribute malicious activity to a specific user.
*   **Scenario:** On April 19, 2023, at 12:50 PM, highly sensitive company data was broadcasted via email. The apparent sender claimed impersonation. The objective was to hunt for the rogue user within the Boring Office corporate network.
*   **Tools Used:** Wireshark, Text Editor, Word Processor.
*   **Artifacts Analyzed:** `SMTP.pcap`, `DHCP.txt`, `Security_log.rtf`.

## 2. Investigation Methodology & Three-Layer Correlation

### Layer 1: Network Traffic Analysis (Identifying the Source IP)
The investigation began by analyzing the packet capture of the malicious email transmission. 
*   **Tool:** Wireshark
*   **Action:** Ingested the `SMTP.pcap` file containing 60 raw packets.
*   **Filtering:** 
		Applied the display filter `smtp` to isolate mail routing traffic, 
		followed by the specific query `smtp contains "FROM"` to identify the sender packet.
*   **Finding:** The filter isolated a single packet confirming the email originated from the compromised account. Crucially, the packet data revealed the source IP address executing the transmission was **`10.10.1.4`**.

### Layer 2: DHCP Log Correlation (Mapping IP to Host Device)
With the malicious IP identified, the next step was to map the IP address to a specific machine on the internal network at the time of the attack.
*   **Tool:** Text Editor
*   **Action:** Analyzed the `DHCP.txt` log, focusing on lease events occurring immediately prior to the 12:50 PM attack window.
*   **Finding:** Reviewed a cluster of six DHCP lease events around 12:11 PM. At exactly 12:11:27 PM, a DHCP lease assignment mapped the malicious IP address (`10.10.1.4`) to the host device hostname: **`USER2`**.

### Layer 3: System Security Logs (Attributing Host to User Account)
The final step required determining which employee was physically authenticated to the `USER2` machine during the 12:50 PM attack window.
*   **Tool:** Word Processor
*   **Action:** Parsed the `Security_log.rtf` access logs to review logon/logoff sessions across the network.
*   **Finding:** The logs detailed two sessions. The first was Jane Doe on `USER1`. The second session showed a successful authentication on host device `USER2`. The logged-in user during the exact time frame of the malicious email broadcast (12:50 PM) was **John Doe**. 

## 3. Conclusion & Findings
Through a three-layer correlation technique, the malicious network activity was successfully attributed to a specific individual.
1.  **Network Capture:** Confirmed the attack originated from IP `10.10.1.4`.
2.  **DHCP Records:** Mapped IP `10.10.1.4` to the workstation `USER2`.
3.  **Security Logs:** Confirmed the account **John Doe** was actively authenticated to `USER2` during the attack window.

**Final Attribution:** John Doe is the primary suspect in the unauthorized data broadcast.