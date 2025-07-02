# Software-Based-Firewall-Integration-with-Wazuh-SIEM

Software-Based Firewall Integration with Wazuh SIEM

Prepared by: Muhammad Aamir
 
1. Task Summary
Objective:
Implement a firewall rule on Kali Linux using IPSet to block all incoming traffic from Sweden-based IP addresses, monitor this activity using Wazuh SIEM, and validate the effectiveness of the block with alert logs. 
________________________________________

2. Tools and Setup
Lab Environment
Component	Description
OS	Kali Linux (VirtualBox)
Firewall Tool	IPSet + IPTables
Monitoring Tool	Wazuh Agent + Wazuh Manager
Target IP Source	IPDeny Sweden IP List
Network Mode	Bridged Adapter
________________________________________
3. Step-by-Step Implementation:
A. Deploy Wazuh-agent into Kali Linux
 
 ![image](https://github.com/user-attachments/assets/ef8417d8-bbe4-4517-bec4-26383585631c)

B. Copy Paste the Commands into Kali Linux Terminal:
 
 
Agent has been connected properly:
 
Step 2: Now Install Suricata into Kali Linux
A. Update Kali & Install Suricata:
 
B. Check the info & Version:
 
C. Check your Kali OS IP:
 
D. Add you ip addr:
 
E. Installing GeoIP Tools for Country-Based Traffic Filtering on Kali Linux:
 
F. Now Download Sweden.ip set:
 
G: Setting Up IPSet for Geo-Based Blocking:
 
________________________________________
Step 3: Add IPs to IPSet from File Verify IPSet
 
________________________________________
Step 5: Block Traffic from Sweden
 
________________________________________




Step 6: Adding  Rules
 
Step 7: Configuring OSSEC to monitor Suricata logs
 
________________________________________







Step 8: Monitor in Wazuh Dashboard
 
 
________________________________________
Using Ping command to verify the logs:
 
Here are logs after ping to Facebook:
 
________________________________________

Validation Tests:
Test Scenario	Result
Ping/traceroute from Sweden IP	Blocked/Dropped
Alert visibility in Wazuh	Successful
IPSet integrity verified	Successful
________________________________________
Observations & Findings:
•	Sweden IPs successfully blocked at firewall level using IPSet.
•	Suricata/Wazuh Agent can be extended to monitor those IPs.
•	Wazuh dashboard reflected system-level alerts (if logs monitored).
•	Highly efficient method for mass-country IP blocking with low resource usage.
________________________________________
Conclusion:
Successfully implemented IPSet-based blocking for Sweden IP ranges and validated the rule through traffic blocking and alert monitoring in Wazuh. This method provides lightweight country-based control with full SOC visibility.
