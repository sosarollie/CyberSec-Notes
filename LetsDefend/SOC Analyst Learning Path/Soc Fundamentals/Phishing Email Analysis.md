A phishing attack aims to steal the user's personal info by ticking them into clicking on a malicious link in emails or running malicious files on their computer.
They fall into the "Delivery" stage of the Cyber Kill Chain model


# Information Gathering
#### Spoofing
Even though a number of companies have an authentication mechanism to let you trust one of their emails, most emails won't pass though an authentication filter, so attackers can easily fake being someone else or a representative of a known company.
The protocols that exist to prevent spoofing techniques are
- Sender Policy Framework (SPF)
- DomainKeys Identified Mail (DKIM)
- DMARC (Domain-based Message Authentication, Reporting, and Conformance)

To manually determine if a mail is spoofed or not, the SMTP address of the mail should first be identified.
The domain's SPF, DKIM, DMARC and MX records (Mail eXchange) can be obtained by using Mxtoolbox

It is also worth noting that even when mails pass said validation methods, they can still be harmfull if the corporate/personal email address of the sender was compromised, this has happened in the past so considering this possibility is always a sensible thing to do.

#### E-mail traffic analysis
Many parameters are needed to analyze a phishing attack. The following parameters can give us an idea of the size of the attack and the target audience if we perform a search on the mail gateway.

- Sender Address
- SMTP IP Address(127.0.0.1)
- @letsdefend.io (domain base)
- letsdefend (In addition to the Gmail account, the attacker may have sent from the Hotmail account)
- Subject (sender address and SMTP address may be constantly changing)

## Email Headers
- Identifies the sender and recipient
- Makes it possible to detect spam emails
- Allows you to track an email's route

**Here are the key questions we need to answer when checking headings during a Phishing analysis:**

- Was the email sent from the correct SMTP server?
- Are the data "From" and "Return-Path / Reply-To" the same?

## Static Analysis
By querying VirusTotal for web addresses in emails, you can find out if the antivirus engines detect the web address as harmful. If someone else has already analyzed the same address/file in VirusTotal, VirusTotal will not analyze it from scratch, it will show you the old analysis result. This feature can be considered both an advantage and a disadvantage.
**If the attacker searches the domain address in VirusTotal when it does not contain malicious content, this address will appear to VirusTotal to be harmless. However, if you miss this tiny detail, you could be fooled into thinking that this address is harmless**

 [Cisco Talos Intelligence](https://talosintelligence.com/)  has search sections where we can learn the reputation of IP addresses. By looking up the SMTP address of the email we detected in Talos, we can see the reputation of the IP address and find out if it is on the blacklist. If the SMTP address is blacklisted, it can be assumed that the attack was carried out on a compromised server.
Similarly, the SMTP address can be searched on VirusTotal and AbuseIPDB to find out if the IP address has been involved in malicious activity in the past.

### Dynamic Analysis
Sandbox environments allow us to examine suspicious files and websites without the risk of infecting our  computer with malware. 
Some commonly used sandboxes:
- VMRay
- JoeSandbox
- AnyRun
- Hybrid Analysis(Falcon Sandbox)

### Additional Techniques

In addition to the phishing attack techniques mentioned in the previous lesson, attackers can also use normally legitimate websites. Some of these include:

- **Using services that offer cloud storage services such as Google and Microsoft**
    - Attackers attempt to trick users into clicking on Google / Microsoft Drive links that appear to be harmless to trick the user into downloading malicious files.
- **Using services that allow the creation of free subdomains, such as Microsoft, WordPress, Blogspot, Wix**
    - Attackers try to deceive security products and analysts by creating a free subdomain from these services. Since whois information cannot be searched as a subdomain, analysts can be tricked into believing that these addresses have been taken in the past and belong to institutions such as Microsoft, WordPress, and others.
- **Form applications**
    - Various services allow free-form creation, and attackers benefit from this rather than creating a phishing site themselves. As the domain is usually harmless, it can be forwarded to the user without triggering anti-virus software. Google Form is an example of such a service. As the Whois information shows that the domain is Google, the attacker can mislead analysts.