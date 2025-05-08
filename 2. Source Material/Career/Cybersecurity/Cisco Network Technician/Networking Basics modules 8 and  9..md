#### Day 6/365
February 2nd

The IPv4 address is a logical network address that identifies a particular host, it must be unique within the LAN for local communication and also unique in the world, for remote communication
Note that the course does not go over how IP addressing works and IPv4 address exhaustion, address depletion and mitigation efforts to combat this.(mostly NAT).
IPv4s address are assigned to network interfaces usually through a Network Interface Controller (a network card).
Every packet sent across the internet has a source and destination IPv4 address.

The logical 32-bit IPv4 address is hierarchical and made up of two separate parts, network and host.
Depending on the subnet mask, the host and the network portion is divided.

---
Unicast refers to one device sending a message to other device in 1 to 1 communications.
A source IP address can only be a unicast address because it can only originate from a single source.
IPv4 unicast host addresses are in the address range of 1.1.1.1 to 223.255.255.255.

Broadcast transmission refers to a device sending a message to all the devices on a network in one-to-all communications. A broadcast packet has a destination IP address with all ones (1s) in the host portion, or 32 one (1) bits. A broadcast packet must be processed by all devices in the same broadcast domain. A broadcast may be directed or limited. A directed broadcast is sent to all hosts on a specific network. A limited broadcast is sent to 255.255.255.255. By default, routers do not forward broadcasts.

Multicast transmission reduces traffic by allowing a host to send a single packet to a selected set of hosts that subscribe to a multicast group. A multicast packet is a packet with a destination IP address that is a multicast address. IPv4 has reserved the 224.0.0.0 to 239.255.255.255 addresses as a multicast range. Each multicast group is represented by a single IPv4 multicast destination address. When an IPv4 host subscribes to a multicast group, the host processes packets addressed to this multicast address, and packets addressed to its uniquely allocated unicast address.

---
Public IPv4 addresses are addresses which are globally routed between ISP routers. However, not all available IPv4 addresses can be used on the internet. There are blocks of addresses called private addresses that are used by most organizations to assign IPv4 addresses to internal hosts.

Loopback addresses (127.0.0.0 /8 or 127.0.0.1 to 127.255.255.254) are more commonly identified as only 127.0.0.1, these are special addresses used by a host to direct traffic to itself.

Although deprecated, in 1982, IPV4 addresses were assigned using classful addressing as defined in RFC 790

- **Class A (0.0.0.0/8 to 127.0.0.0/8)** - Designed to support extremely large networks with more than 16 million host addresses.
- **Class B (128.0.0.0 /16 - 191.255.0.0 /16)** - Designed to support the needs of moderate to large size networks with up to approximately 65,000 host addresses.
- **Class C (192.0.0.0 /24 - 223.255.255.0 /24)** - Designed to support small networks with a maximum of 254 hosts.
---
In an Ethernet LAN, devices use broadcasts and ARP to locate other devices. ARP sends Layer 2 broadcasts to a known IPv4 address on the local network to discover the associated MAC address. Devices on Ethernet LANs also locate other devices using services. A host typically acquires its IPv4 address configuration using DHCP which sends broadcasts on the local network to locate a DHCP server. Switches propagate broadcasts out all interfaces except the interface on which it was received.

Subnetting comes into play when the LAN becomes too big, segmentation is useful for both organizing the addresses according to criteria and also for performance improvements, if the broadcast domain is too large, it can negatively affect the network and its devices.
The basis of subnetting is to use host bits to create additional subnets.

---

