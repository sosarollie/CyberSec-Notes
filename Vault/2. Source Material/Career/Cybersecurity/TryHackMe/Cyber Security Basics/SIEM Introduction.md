The one big advantage of having a SIEM solution is condensing every log source in one place and correlating between events, search through them, and investigate incidents without having to search for scattered and uncategorized logs in the system.

Windows stores its logs in the Event Viewer. Even though Event Viewer has its own filtering, these logs are forwarded to the SIEM solution for monitoring and better visibility.

Linux stores all the related logs in various locations, such as:
- /var/log/httpd : Contains HTTP Request  / Response and error logs.
- /var/log/cron   : Events related to cron jobs are stored in this location.
- /var/log/auth.log and /var/log/secure : Stores authentication related logs.  
- /var/log/kern : This file stores kernel related events.

When it comes to Web Servers in Linux, common locations are /var/log/apache or /var/log/httpd

#### Log Ingestion

Each solution has a way to ingest the logs, the most common methods are usually:
1) Agent / Forwarder: These SIEM solutions provide a lightweight tool called an agent (forwarder by Splunk) that gets installed in the Endpoint. It is configured to capture all the important logs and send them to the SIEM server.  

2) Syslog: Syslog is a widely used protocol to collect data from various systems like web servers, databases, etc., are sent real-time data to the centralized destination.

3) Manual Upload: Some SIEM solutions, like Splunk, ELK, etc., allow users to ingest offline data for quick analysis. Once the data is ingested, it is normalized and made available for analysis.

4) Port-Forwarding: SIEM solutions can also be configured to listen on a certain port, and then the endpoints forward the data to the SIEM instance on the listening port.


---
SIEM solutions are also used to link data together in order to detect threats. Once a threat is detected, an alert is raised. It helps detect and protect against threats in a timely manner, and provides visiblity of what's happening inside the network structure.

As presented previously, SIEM is one of if not the most important componen of a SOC ecosystem

To summarise its capabilities:

- Correlation between events from different log sources.
- Provide visibility on both Host-centric and Network-centric activities.
- Allow analysts to investigate the latest threats and timely responses.
- Hunt for threats that are not detected by the rules in place.

They make the SOC Analyst job easier, by helping in key tasks like identifying false positives, reporting, monitoring, investigating, etc.

---

## The Dashboard

Definitely the most important part of any solution, it presents the data for analysis after being ingested in a not-so-verbose or more human manner.
The information commonly found in dashboards is:
- Alert Highlights
- System Notification
- Health Alert
- List of Failed Login Attempts
- Events Ingested Count
- Rules triggered
- Top Domains Visited

## Correlation Rules
The are logical expressions set to be triggered, for example:
- If login is successful after multiple failed login attempts - Raise an alert for `Successful Login After multiple Login Attempts`
- A rule is set to alert every time a user plugs in a USB (Useful if USB is restricted as per the company policy)
- If outbound traffic is > 25 MB - Raise an alert to potential Data exfiltration Attempt (Usually, it depends on the company policy)

Example of Eventlog use cases:

**Use-Case 1:**

Since Adversaries tend to remove the logs during the post-exploitation phase to remove their tracks, unique Event ID **104** is logged every time a user tries to remove or clear event logs with the following condition:

**Rule:** If the Log source is WinEventLog **AND** EventID is **104** - Trigger an alert `Event Log Cleared`

**Use-Case 2:** Adversaries use commands like **whoami** after the exploitation/privilege escalation phase. The following Fields will be helpful to include in the rule.

- Log source: Identify the log source capturing the event logs  

- Event ID: which Event ID is associated with Process Execution activity? In this case, event id 4688 will be helpful. 

- NewProcessName: which process name will be helpful to include in the rule?  

**Rule:** If Log Source is WinEventLog **AND** EventCode is **4688,** and NewProcessName contains **whoami,** then Trigger an ALERT `WHOAMI command Execution DETECTED`

### Alert Investigation

Once an alert is triggered, the events/flows associated with the alert are examined, and the rule is checked to see which conditions are met. Based on the investigation, the analyst determines if it's a True or False positive. Some of the actions that are performed after the analysis are:

- Alert is False Alarm:
	- It may require tuning the rule to avoid similar False positives from occurring again.  
- Alert is True Positive
	- Perform further investigation.  
- Contact the asset owner to inquire about the activity.
- Suspicious activity is confirmed
	- Isolate the infected host.
- Block the suspicious IP.