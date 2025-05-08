2024-07-29 00:33

Status:

Tags: [compTIA](../3.%20Tags/compTIA.md) [cybersecurity](../3.%20Tags/cybersecurity.md) [network](../3.%20Tags/network.md) 
# Data Communication

Getting data moved from one part of the network to the other relies on a PDU (protocol data unit)
- Transmission units
Ethernet operates on a frame of data
	It doesn't care what's inside
IP operates on a packet of data
	Inside is TCP or UDP, but IP doesn't really care
TCP or UDP
	TCP segment
	UDP datagram

![2. Source Material/Career/Images/Pasted image 20240729003857.png](../7.%20Images/Pasted%20image%2020240729003857%201.png)

![2. Source Material/Career/Images/Pasted image 20240729004002.png](../7.%20Images/Pasted%20image%2020240729004002%201.png)
Another way of viewing it

![2. Source Material/Career/Images/Pasted image 20240729004102.png](../7.%20Images/Pasted%20image%2020240729004102%201.png)

TCP Flags are a set of bits included in the TCP header
The TCP flags control the payload, there are multiple flags, such as acknowledgment, push, fin, syn, urgent, etc.

IP header also has flags

MTU (Maximum Transmission Unit)
	determines the maximum size of the packet that we are going to send without having to fragment
Fragmentation slows things down
MTU has automated methods but is often done manually

Fragments are always in multiples of 8

MTU sizes are usually configured once, based on the network infrastructure and don't change often
# Reference

