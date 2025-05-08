### Day 12/365

#### TCP
- acknowledgement of receipt of packets
- packets have sequence numbers
- keeps track of the number of segments that have been sent, if no ack, it resends them

#### UDP
- no acks, no sequence number of packets
- preferable with streaming and VOIP
- acks would slow down delivery and would be more disruptive than dropping packets


---
![2. Source Material/Career/Images/Pasted image 20250210191858.png](../../../../7.%20Images/Pasted%20image%2020250210191858%201.png)
*Port numbers*

### Server side
Port numbers below 1024 are usually called "well-known ports"
![2. Source Material/Career/Images/Pasted image 20250210192702.png](../../../../7.%20Images/Pasted%20image%2020250210192702%201.png)
automatically identified by the clients
ports "listen" = buffer setup that will accept requests

### Host side
above 1024, randomly assigned

---
- **Well-Known Ports -** Destination ports that are associated with common network applications are identified as well-known ports. These ports are in the range of 1 to 1023.
- **Registered Ports -** Ports 1024 through 49151 can be used as either source or destination ports. These can be used by organizations to register specific applications such as IM applications.
- **Private Ports -** Ports 49152 through 65535 are often used as source ports. These ports can be used by any application.

Unexplained TCP connections can pose a major security threat. They can indicate that something or someone is connected to the local host. Sometimes it is necessary to know which active TCP connections are open and running on a networked host. Netstat is an important network utility that can be used to verify those connections. The command netstat is used to list the protocols in use, the local address and port numbers, the foreign address and port numbers, and the connection state.