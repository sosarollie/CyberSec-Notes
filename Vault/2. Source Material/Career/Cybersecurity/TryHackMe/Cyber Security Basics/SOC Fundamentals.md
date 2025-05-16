A Security Operations Center is a deducated facility operated by a specialized security team. This team aims to continuously monitor an organization's network and resources and identify suspicious activity to prevent damage, 24/7


Main Focus: Keep 
- Detection
- Response
Intact

### Detection
- Vulnerabilities
- Unauthorized activity
- Policy Violations
- Intrusions

## Response
- Support with the incident response

### 3 Pillars:
- People
- Process
- Technology
A team of professional individuals working on state-of-the-art security tools in the presence of proper processes is what makes a mature SOC environment.


# People
![](../../../../../7.%20Images/6645aa8c024f7893371eb7ac-1718872774537.png)
*Soc team roles and responsibiltiies*

- SOC Analyst L1
	- Anything detected by the security solution passes through them first
	- They are the first responders to any detection
	- Basic alert triage to determine if a specific detection is harmful
	- They report these detections through proper channels
- SOC Analyst L2
	- Deeper investigation
	- Correlate data from multiple data sources to perform proper analysis
- SOC Analyst L3
	- Experienced professionals who proactively look for any threat indicators and support in the incident response activities
	- Their experience comes in handy when detailed responses are needed
		- Containment, eradication and recovery
- Security Engineer
	- All analysts work on security solutions. These solutions need deployment and configuration
	- They ensure smooth operation
- Detection Engineer
	- Security rules are the logic built behind security solutions to detect harmful activities
	- L2 and L3 create these rules, while the SOC team can sometimes also utilize the detection engineer role independently for this responsibility
- SOC Manager
	- Manages the processes the SOC team follows
	- Provides support
	- Remains in contact with the organization's CISO (Chief Information Security Officer)

# Process
## Alert Triage
It's the basis of the SOC team, the triage is focused on analyzing the specific alert. This determines the severity of the alert and helps us prioritize it
Answer the 5 Ws
- Who
- What
- Where
- When
- Why

Example: Malware detected on Host: GEORGE PC

What? 	A malicious file was detected on one of the hosts inside the organization’s network.
When? 	The file was detected at 13:20 on June 5, 2024.
Where? 	The file was detected in the directory of the host: "GEORGE PC".
Who? 	The file was detected for the user George.
Why? 	After the investigation, it was found that the file was downloaded from a pirated software-selling website. The investigation with the user revealed that they downloaded the file as they wanted to use a software for free.

The detected alerts need to be escalated to higher-level analysts for a timely response a solution
These are escalated as tickets and assigned to the relevant people

Sometimes, the alerts are critical and high-level teams initiate an incident response and a detailed forensics activity also needs to be performed


## Technology

Security Solutions:
- SIEM: Security information and Event Management. A popular tool used in almost every SOC environment
	- The tool collects logs from various network devices, referred to as log sources
	- Detection rules are configured in the SIEM solution, which contains logic to identify suspicious activity
	- Provides us with the detections after correlating them with multiple log sources and alerts us in case of a match with any of the rules
	- Modern SIEM'S surpass this rule and provide us with user behavior analytics and threat intelligence capability, machine learning algorithms support this
	- The SIEM solution only provides the DETECTION capabilities in a SOC environment.

- EDR: Endpoint Detection and Response (EDR)
	- Detailed real-time and historical visibility of the devices activities
	- Operates on endpoint level
	- Carries out automated responses
	- Extensive detection capabilities for endpoints, allowing to investigate them in detaill and respond quickly

- Firewall
	- Purely for network security and acts as a barrier between your internal and external networks
	- Monitors incoming and outgoing network traffic
	- Filters unauthorized traffic
	- Some detection rules deployed, which help identify and block suspicious traffic before it reaches the internal network

- Others:
	- Antivirus
	- EPP (Endpoint protection platform)
	- IDS/IPS (Intrusion Detection System)
	- XDR 
	- SOAR (Security Orchestration Automation and Response)
