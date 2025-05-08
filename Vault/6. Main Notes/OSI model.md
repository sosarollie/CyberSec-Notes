2024-07-29 00:08

Status:

Tags: [compTIA](../3.%20Tags/compTIA.md) [cybersecurity](../3.%20Tags/cybersecurity.md) [network](../3.%20Tags/network.md) 
# OSI model

- Open Systems Interconnection Reference Model

Way to describe how data moves across the network

*Model*

**NOT** OSI protocol suite

- 7 Layers
	-  7 Application
	- 6 Presentation
	- 5 Session
	- 4 Transport
	- 3 Network
	- 2 Data Link
	- 1 Physical

==A== ll
==P== eople
==S== eem
==T== o
==N== eed
==D== ata
==P== rocessing
or
Please
Do 
Not 
Throw
Sausage
Pizza
Away

#### Layer 1 - Physical Layer

- The physics of the network
	Signalling, cabling, connectors, data cables, cat6
	This layer isn't about protocols
- Physical layer problem
	Fix your cabling, punch-downs
	Run loopback tests, replace cables or test them, swap adapter cards

#### Layer 2 - Data Link Layer

- The basic network "language"
	- The foundation of communication at the data link layer
- Data Link Control (DLC) Protocols 
	- Mac (MEDIA ACCESS CONTROL) address on Ethernet (LAYER 2 ADDRESSES)
- The "switching" layer

#### Layer 3 - Network Layer (The IP layer)

- The "routing" layer
- Internet Protocol (IP)
- Fragments frames to traverse different networks

#### Layer 4 - Transport Layer

- The "post office" layer
	- Parcels and letters
- TCP UDP
Used when accessing a webpage but since the webpage is large you can't send it through 1 frame, you have to split it and be put back together

#### Layer 5 - Session Layer

- Communication management between devices
	- Start, stop, restart
- Control protocols, tunnelling protocols

#### Layer 6 - Presentation layer

- Character encoding
- WMV, JPEG, MOV (media)
- Application encryption
- Often combined with the Application Layer

#### Layer 7 - Application Layer

- The layer we see
- HTTP, FTP, DNS, POP3, SMTP

(when troubleshooting, go from layer 1 to 7)
## Example: Google Mail

	7 -Application: HTTPS://mail.google.com
	6 -Presentation: SSL Encryption
	5 -Session: Link the presentation to the transport
	4 -Transport: TCP encapsulation
	3 -Network: IP encapsulation
	2 -Data Link: Ethernet
	1 -Physical: Electrical signals
# Reference

https://www.youtube.com/watch?v=owDh6FNJUog&list=PLG49S3nxzAnlCJiCrOYuRYb6cne864a7G&index=2