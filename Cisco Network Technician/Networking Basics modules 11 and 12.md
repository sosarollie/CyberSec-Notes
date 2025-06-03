Using static address assignment, the network administrator has to manually configure the network information for a host (IPv4 ad, mask and gateway). Although it can provide increased control of network resources, it is also time consuming and the need to maintain an accurate list arises.
IPv4 addresses can be assigned automatically using DHCP (Dynamic host connection protocol), and it is generally the preferred method, reduces the burden on network support staff and eliminates entry errors, hosts "borrow" an address instead of owning it.
With home networks, the DHCP server may be located at the ISP and a host on the home network receives its IPv4 config directly from the ISP, the wireless router is both a DHCP client and server
The DHCP server is configured with a range of IPv4 addresses that can be assigned to DHCP clients. A client that needs an IPv4 address will send a DHCP Discover message which is a broadcast with a destination IPv4 address of 255.255.255.255 (32 ones) and a destination MAC address of FF-FF-FF-FF-FF-FF (48 ones). All hosts on the network will receive this broadcast DHCP frame, but only a DHCP server will reply. The server will respond with a DHCP Offer, suggesting an IPv4 address for the client, the host then sends a DHCP request asking to use the suggested IPv4 address, and the server finally responds with a DHCP Ack.
For most home and small business networks, the IPv4 address of 192.168.0.1 and mask of 255.255.255.0 are defaults, and most have DHCP server enabled by default.

---
When a wireless router is connected to the ISP, it acts like a DHCP client to receive the correct external network IPv4 address for the internet interface. ISPs usually provide an internet-routable address, which enables hosts connected to the wireless router to have access to the internet. The wireless router serves as the boundary between the local internal network and the external internet.

The wireless router receives a public address from the ISP, which allows it to send and receive packets on the internet. It, in turn, provides private addresses to local network clients.

The process used to convert private addresses to internet-routable addresses is called NAT. With NAT, a private (local) source IPv4 address is translated to a public (global) address. The process is reversed for incoming packets. The wireless router is able to translate many internal IPv4 addresses to the same public address, by using NAT.

Only packets destined for other networks need to be translated. These packets must pass through the gateway, where the wireless router replaces the private IPv4 address of the source host with its own public IPv4 address.

---
