#### Day 4/365
25th of January

Protocols are required for computers to properly communicate across the network. These include message format, message size, timing encoding, encapsulation, and message patters.

---
The only thing a device sees in a network is its own addressing information, by using network protocols it reaches out to other devices in said network.
Most network communications are broken up into smaller data units, or packets.

Networking and internet standards ensure that all devices connecting to the network implement the same set of rules or protocols in the same manner.

These different standards are developed, published, and maintained by a variety of organizations.
RFCs for internet standards are published and managed by the IETF.

---
The interaction between the different protocols on a device can be illustrated as a protocol stack
- layered hierarchy
- each higher-level protocol depending on lower levels.

The suite of TCP/IP protocols that are used for internet communications follows the structure of this model:

- **Application** - Represents data to the user, plus encoding and dialog control
- **Transport** -Supports communication between various devices across diverse networks
- **Internet** - Determines the best path through the network
- **Network Access** - The hardware devices and media that make up the network.

*note that this model does not specify exactly how a function should be accomplished*
The primary purpose of a reference model is to aid in understanding of the functions neccessary for network communications

---
#### OSI MODEL

==A== ll 
==P== eople
==S== eem
==T== o
==N== eed
==D== ata
==P== rocessing

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
Used when accessing a webpage but since the webpage is large you can't send it through 1 frame, you have to split it and be put back together.

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