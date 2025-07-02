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
 ![image](https://github.com/user-attachments/assets/d7860a58-38be-4b77-8cc5-cf2430036eec)


B. Copy Paste the Commands into Kali Linux Terminal:
 
![image](https://github.com/user-attachments/assets/7321aee8-40d4-40f3-9690-eed47700104d)
![image](https://github.com/user-attachments/assets/cb37fbfa-f58b-4065-b2bc-579a6a0737cd)


Agent has been connected properly:
![image](https://github.com/user-attachments/assets/7ef42483-0724-4a8f-8f05-cde1f036fc92)

 
Step 2: Now Install Suricata into Kali Linux
A. Update Kali & Install Suricata:
 ![image](https://github.com/user-attachments/assets/4c1a00eb-006a-4f12-8e9c-33ebca4f47f0)

B. Check the info & Version:
 ![image](https://github.com/user-attachments/assets/fae01e0d-567d-4c9d-bb8e-c49d3e745f48)

C. Check your Kali OS IP:
 ![image](https://github.com/user-attachments/assets/206409e7-2dd9-4297-a7b2-e9165b776004)

D. Add you ip addr:
 ![image](https://github.com/user-attachments/assets/0b9586ec-30c2-4775-b765-b683334d500d)

E. Installing GeoIP Tools for Country-Based Traffic Filtering on Kali Linux:
 ![image](https://github.com/user-attachments/assets/5c4c2c9d-0e24-40ab-a9cf-baf8883b647c)

F. Now Download Sweden.ip set:
 ![image](https://github.com/user-attachments/assets/5e5b2d11-005f-4c0a-a69c-89d8f284082f)

G: Setting Up IPSet for Geo-Based Blocking:
 ![image](https://github.com/user-attachments/assets/4211ebf0-dd70-47e9-a331-43120baf97cc)

________________________________________
Step 3: Add IPs to IPSet from File Verify IPSet
 ![image](https://github.com/user-attachments/assets/bc87c293-2090-4618-8cdf-f00ce940a3ce)

________________________________________
Step 5: Block Traffic from Sweden
 ![image](https://github.com/user-attachments/assets/f216e7c9-36e9-4e7f-a5b0-8af8d71f3013)

________________________________________




Step 6: Adding  Rules
 ![image](https://github.com/user-attachments/assets/5a5bd94b-01a4-4d47-8d02-72e13c34f0de)

Step 7: Configuring OSSEC to monitor Suricata logs
 ![image](https://github.com/user-attachments/assets/cc2e3137-3aed-4ec4-91b1-d22a316ab4a3)

________________________________________







Step 8: Monitor in Wazuh Dashboard
 ![image](https://github.com/user-attachments/assets/8e2ccd50-280c-48bf-8921-be52791058d3)
![image](https://github.com/user-attachments/assets/29551a11-befe-49b0-aea5-e4cf649d2ed8)

 
________________________________________
Using Ping command to verify the logs:
![image](https://github.com/user-attachments/assets/23d9fdf5-97d5-4f70-b746-059350cadc6c)
 
Here are logs after ping to Facebook:
![image](https://github.com/user-attachments/assets/5d3e798b-9e5f-42a6-bd8b-aa42ed2ec40e)
 
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
