## EDR - Endpoint Detection and Response

EDR is an integrated endpoint security solution that combines continuous real-time monitoring and collection of endpoint data with rules-based automated response and analysis capabilities
Endpoints are _physical devices that connect to a network system_ such as mobile devices, desktop computers, virtual machines, embedded devices, and servers.

Some EDR solutions commonly used in the workplace: CarbonBlack, SentinelOne, and FireEye HX.

## SOAR (Security Orchestration Automation and Response)

It enables security products and tools in an environment to work together, streamlining the tasks of SOC team members. For example, it will automatically search VirusTotal for the source IP of a SIEM alert, reducing the workload of the Analyst

Some SOAR products commonly used in the industry:

- Splunk Phantom
- IBM Resilient
- Logsign
- Demisto

![](../../../../../../7.%20Images/soar-capabilities.jpg)

SOAR solutions provide an all-in-one software integration
![](../../../../../../7.%20Images/soar-central.png)


### Threat Intelligence Feed
A Threat Intelligence Feed is data (such as malware hashes, C2 (Command&Control) domain/IP addresses etc.) provided by a third party company.

Free and popular sources to use:
- [VirusTotal](https://www.virustotal.com/)
- [Talos Intelligence](https://talosintelligence.com/)

Let's say you ran a hash of an .exe in VirusTotal and in the past you didn't find anything suspicious about it. In this case, you should not just assume that the file is clean, that would be a mistake. A SOC analyst should carefully perform the necessary file analysis (static/dynamic).

*IP ADDRESSES CAN CHANGE HANDS*

### Common Mistakes made by SOC Analysts

###### Over-reliance on VirusTotal Results
- There is a new malicious software developed using an AV bypass technique that may not be detected by VT.
- Accept it as a supporting tool but perform our analyses with this in mind
- Further reading: https://medium.com/maverislabs/virustotal-is-not-an-incident-responder-80a6bb687eb9

##### Hasty Analysis of Malware in a Sandbox
The duration of the analysis should be kept as long as possible and it should take place in a real environment, if possible, because malware:
- might be able to detect a sandbox environment an prevent itself from activating
- may not become active for 10 to 15 min after the operation is perormed


##### Inadequate Log Analysis

##### Overlooking VirusTotal Dates
Conduct a new search if the last updated one was too long ago eg. 3 months.

