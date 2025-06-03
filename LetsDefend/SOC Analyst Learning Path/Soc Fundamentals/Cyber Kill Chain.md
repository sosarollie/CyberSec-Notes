Cyber Kill Chain is a framework created by Lockheed Martin in 2011 and used to model attacks
It is important for us in order to have a better understanding of the stages of a cyber attack and determine which actions begin and end one.
We can use the CKC to analyze where the noticed attack occured.
It enables the organization to determine where and how severe the security flaws are

## Steps

They are sequential, not possible to execute one without the one before
1. Reconnaissance
	- Based on engaging with the target or not
		- Passive
			- eg. web archive websites, looking at employees profiles
		- Active
			- eg. request to the web server
2. Weaponization
3. Delivery
4. Exploitation
5. Installation
6. Command & Control (C2)
7. Actions on Objectives

##### Reconnaissance

Attackers can
- Based on engaging with the target or not
	- Passive
		- Obtaining information from open sources of information about the target has previously been released
		- Obtaining e-mail addresses of employees of the organization
		- Obtaining internal or personal information about employees of the organization using social networking platforms
		- Identification of vendors that the organization cooperates with
	- Active
		- Obtaining version information of servers and software belonging to the target
		- Detection of devices that are connected to the Internet
		- Detection of security vulnerabilities on servers open to access on the Internet
		- Identifying the IP address block belonging to the organization

Defenders can
- Detect areas of information disclosure with external pentest
- Obtain leak information about the organization from Threat Intelligence sources
- Not keep the documents providing organizational information available on the internet
- Monitor traffic by installing security solutions such as firewalls in areas of the company that are accessible over the internet
- Instantly update to avoid new security vulnerabilities from being exploited

#### Weaponization

Adversary actions
- Creating malware
- Developing exploits
- Creating malicious content for use in a phishing attempt (such as an email template and a malicious document).
- Identifying the best instrument for the cyber attack

Defender actions (not possible to directly prevent the attack)
- Checking the systems on a regular basis to see if any identified security vulnerabilities exist.
- Installing security updates for the systems of the institutions as soon as possible
- Analyzing the impact of known or newly produced cyber attack tools on systems by tracking the known or newly developed attack tools and therefore being able to detect when the tool is utilized


#### Delivery

First interaction with the victim happens

Adversary actions
- Delivering a malicious URL via email
- Delivering malware as a file attachment via email
- Delivering malware through the website
- Delivering the malicious URL via social media
- Delivering malware via social media
- Uploading the malware directly to the target server (if direct access to the server is possible) 
- Physically installing or enabling the installation of malware directly to the target system via a USB device

Defender actions (still can't prevent the attack from occurring but preventive measures can be taken and there are plenty)
- Adopting a skeptical attitude towards URLs in email content and viewing them in a sandbox environment
- Scanning the email's attachments using antivirus software
- Using email security solution products in organizations
- Ensuring that users/institutional employees receive training on information security
- Constant monitoring of server access and recording of logs
- Effective use and management of security solutions such as Firewall
- Conducting detailed analysis of suspicious activities when needed
- Detecting anomalies and determining the initial reason

##### Exploitation
The prepared and delivered tool is run / tested.

Adversary actions
- Executing the exploit that exploits the hardware vulnerability
- Executing the exploit that exploits the vulnerability of the software or operating system
- Running malware

Defender actions (*Defending against exploitation poses a significantly more intricate and labor-intensive task for Blueteams compared to other stages. This is primarily due to the potential encounter with previously unseen malware or exploits, which adds a layer of complexity to the defense process. To elucidate, the use of zeroday exploits can complicate the detection and prevention procedures during this phase.*)
- Training the employees of the organization on when it is/is not necessary to open a file uploaded on the systems and what issues should be considered
- Constantly monitoring system security operations on the assets belonging to the organization and detecting anomalies
- Tracking the security vulnerabilities published for the assets belonging to the organization, writing the appropriate monitoring rule, and detecting them when they are exploited
- Following the security updates of the assets belonging to the organization and installing them immediately
- Monitoring activities on endpoints using EDR products
- Providing secure coding training to software developers in order to prevent security vulnerabilities in locally developed applications 
- Conducting pentests on assets of the organization on a regular basis
- Regular automated vulnerability scanning and monitoring of reports
- Organizing the authorizations on the assets belonging to the institution and giving each account the authority needed


#### Installation
Attacker attempts to maintain persistance on the exploited system via
- Install malware on the victim's device.
- Placing a backdoor on the victim's system
- Install web shell on the web server (if it is a web server).
- Adding a service, firewall rule, or scheduled task to ensure the persistence of the victim device

Defender actions have to do with Threat Hunting, we assume the attacker has breached and cant be detected
- To carry out Network Security Monitoring operations on all assets of the organization
- Using EDR security solutions to be aware of configuration changes applied on each endpoint
- Restricting access to critical files on systems and monitoring access 
- Restricting access to critical paths on systems and monitoring access
- To allow the use of admin privileges only for mandatory situations by making authorization arrangements for users on the systems
- Detecting malicious process activities by monitoring the processes running on the systems
- Allowing only executable files with a valid signature to be run on the system
- Detect anomalies in all monitored system activities and find the root cause

#### C2
The attacker has completed several crucial tasks of the attack and has prepared the Command and Control (C2) server to deliver commands to the system. The attacker can send remote commands to the system and execute them at this step.

Attacker actions
- Configuring C2 Server to communicate with the victim
- Implementing the necessary actions on the victim's device to make its contact with C2 possible.

Defender actions (General security monitoring and detection techniques and practices within the context of C2 communication should be considered. Blueteams should take the appropriate steps to recognize and prevent potential C2 network traffic flow.)
- To determine whether the known C2 tools are available on systems
- Blocking C2 server IP addresses from Cyber Threat Intelligence sources through security products such as Firewall
- To detect network traffic that may be C2 communication with Network Security Monitoring on the system

#### Actions on Objectives
At this step, the attackers’ actions are determined by their purpose and motivation. If the attacker's primary goal is to cause system damage, they may delete critical information, as an example.

Attacker Actions
- To Encrypt files on the system with the help of ransomware
- To exfiltrate critical information/documents within the system
- Damaging the system by deleting critical information in the system
- To become able to apply more authorized operations with privilege escalation operations and to expand the scope of the cyber attack by providing access to other machines in the network
- Collecting user credentials to gain access to another device in the network
- Collecting information within the system
- Changing or manipulating the information in the system

First and foremost, the system must be regularly monitored. It may be possible to identify malicious activity on the system in this way. After the detection phase, the detected action should be followed by the appropriate action. One of the most fundamental measures that SOC teams may take is to prevent attackers from exfiltrating data from the organization to outside.  Because data leakage is one of the most common cyber attack outcomes today.

Defender Actions
- Detecting anomalies in network traffic
- Restricting network access to the outside and monitoring it continuously
- Restricting access to files/folders containing critical information and controlling access regularly
- Restricting the authorization of access to databases containing critical information and continuously monitoring access
- Using DLP products to prevent data leakage
- Detecting unauthorized access by users



