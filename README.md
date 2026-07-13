## wazuh-siem-detection-lab 
A Wazuh SIEM lab with 5 custom detection rules for authentication, privilege escalation, and account changes, deployed across a Kali/Ubuntu VirtualBox environment.
A hands on Wazuh SIEM deployment monitoring a Kali Linux endpoint from an Ubuntu Server manager, featuring 5 custom detection rules covering SSH authentication, password changes, privilege escalation, and account activity. 
# Project Overview
This project simulates a Security Operations Center (SOC) monitoring setup. A Wazuh Manager, Indexer, and Dashboard were deployed on an Ubuntu Server VM, with a Kali Linux VM enrolled as a monitored agent. Five custom detection rules were written, tested, and validated against real triggered events, and each alert was documented with a triage walkthrough explaining what a SOC analyst would investigate next.
The goal was to move beyond default/out-of-the-box Wazuh rules and demonstrate the ability to write, debug, and validate custom detection rules through to live alert verification in the dashboard.
# Tools Used
1-Wazuh 4.9 (Manager, Indexer, Dashboard)                                                   
2-Ubuntu Server (Wazuh Manager host)                                                 
3-Kali Linux (Wazuh Agent)  
4-Oracle VirtualBox (Host Only network connecting VMs)  
5-draw.io (network architecture diagram)
# Environment Setup
1-Two VMs connected via a VirtualBox Host-Only network (192.168.56.0/24), each also configured with a NAT adapter for internet access.  
2-Ubuntu Server VM - 192.168.56.103 - running the Wazuh Manager, Indexer, and Dashboard.  
3-Kali Linux VM - 192.168.56.101 - running the Wazuh Agent, enrolled and reporting to the manager.  
4-SSH connectivity was configured between both VMs for remote administration.  
# Steps Taken
1-Deployed Wazuh on a fresh Ubuntu Server VM using the official installer script, tuned for a lab environment.  
2-Installed and enrolled the Wazuh Agent on Kali Linux, confirming successful agent registration via the dashboard.  
3-Wrote 5 custom detection rules in local_rules.xml, each built on a verified base Wazuh rule ID and tested against real triggered events rather than assumed behavior:  
	.	100001 - Multiple failed SSH logins  
	.	100002 - New user account created  
	.	100003 - Password change command executed  
	.	100004 - Failed attempt to switch user (su)  
	.	100005 - Sudo session opened by user  
4-Triggered each rule live on the Kali agent and confirmed detection in the Wazuh Dashboard’s Threat Hunting view.  
5-Documented an alert triage walkthrough for all 5 rules, covering what triggered each alert, why it matters from a security perspective, and what a SOC analyst would investigate next.  
6-Produced a network architecture diagram showing both VMs, their IP addresses, the Host-Only network, and the direction of log flow from agent to manager.  

Repository Contents: An xml file containing all the local rules,an alert triage walkthrough document,a wazuh archictecture diagram and screenshots showing each step.
