Intrusion Detection System, for when malicious activity has bypass the Firewall, a solution inside the network. It only notifies and does not act on detections

## Types of IDS

They vary depending on deployment and detectons modes


#### Deployment modes:
- Host Intrusion Detection System
	- Host-based, installed on the host directly
	- Resource intensive, hard to manage
- Network Intrusion Detection System
	- Network-based
	- Centralized view of all detections inside the network


#### Detection Modes
- **Signature-Based IDS:** 
	- Attack patters = signature
	- Signatures are preserved by the IDS in their databases, if the same attack happens, it gets detected and reported
	- The stronger the database the more efficiently it would detect known threats
	- Unable to detect zero-day attacks
- **Anomaly-Based IDS**:
	- It first learns the normal behaviour (baseline) of the network
	- Performs detections if there is any deviation from behaviour
	- Can detect zero-day
	- Generates lot of false positives
	- Can be reduced by fine tuning
- **Hybrid IDS**:
	- Combines both approaches