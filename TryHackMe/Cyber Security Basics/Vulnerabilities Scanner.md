Fixing vulns is known as Patching

### Authenticated vs Unauthenticated scans

|Authenticated Scans|Unauthenticated Scans|
|---|---|
|The credentials of the subject host must be provided to the vulnerability scanner.|The vulnerability scanner does not require the host’s credentials; it only needs the IP address.|
|Identifies the vulnerabilities that can be exploited by the attackers having access to the host.|Identifies the vulnerabilities that can be exploited by an external attacker having no access to the subject host.|
|It provides a deeper visibility into the target system by scanning its configuration and installed applications.|It is less resource-intensive and straightforward to set up.|
|For example, scanning an internal database by providing its credentials to the vulnerability scanner.|For example, scanning a public-facing website for vulnerabilities that any user can exploit.|

|Internal Scans|External Scans|
|---|---|
|Conducted from inside the network.|Conducted from outside the network.|
|It focuses on the vulnerabilities that can be exploited inside the network.|It focuses on the vulnerabilities that can be exploited from outside the network.|
|Identifies vulnerabilities that would be exposed to the attackers once they get inside the network.|Identifies the vulnerabilities exposed to the attacker from outside the network.|

#### Most used vuln scanners
### Nessus

[Nessus](https://www.tenable.com/products/nessus) was developed as an open-source project in 1998. It was later acquired by Tenable in 2005 and became proprietary software. It has extensive vulnerability scanning options and is widely used by large enterprises. It is available in both free and paid versions. The free version offers a limited number of scan features. In contrast, its commercial version offers advanced scanning features, unlimited scans, and professional support. Nessus needs to be deployed and managed on-premises.


![Nessus logo.](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1726737640788.png)  

### Qualys

[Qualys](https://qualys.com/) was developed in 1999 as a subscription-based vulnerability management solution. Along with continuous vulnerability scanning, it provides compliance checks and asset management. It automatically alerts on the vulnerabilities found during continuous monitoring. The best thing about Qualys is that it is a cloud-based platform, which means there is no extra cost or effort to keep it up and running on our physical hardware and manage it.

![Qualys logo.](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1726737640778.png)  

### Nexpose

[Nexpose](https://www.rapid7.com/products/nexpose/) was developed by Rapid7 in 2005 as a subscription-based vulnerability management solution. It continuously discovers new assets in the network and performs vulnerability scans on them. It gives vulnerability risk scores depending on the asset value and the vulnerability’s impact. It also provides compliance checks against various standards. Nexpose offers both on-premises and hybrid (cloud and on-premises) deployment modes.

![Nexpose logo.](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1726737640774.png)  

### OpenVAS (Open Vulnerability Assessment System)

[OpenVAS](https://www.openvas.org/) is an open-source vulnerability assessment solution developed by Greenbone Security. It offers basic features with known vulnerabilities scanned through its database. It is less extensive than commercial tools; however, it gives you the flavor of a complete vulnerability scanner. It is beneficial for small organizations and individual systems. The next section will explore this tool in more detail by performing vulnerability scanning.

![OpenVAS logo.](https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1726737640798.png)
### CVE

Common Vulnerabilities and Exposured
- A CVE number is a unique number given to vulnerabilities
- developed by MITRE Corporation
- They are made of
	- CVE prefiex
	- Year discovered
	- Arbitrary Digits
	- Example: CVE - 2024 - 9374 --> Terms description plugin for WordPress

### CVSS
Common Vulnerability Scoring System
- Scoring denotes severity
	- 0.0 -3.9: LOW
	- 4.0-6.9: MEDIUM
	- 7.0-8.9: HIGH
	- 9.0-10: CRITICAL
