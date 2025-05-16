- Designed to inspect a network's or digital device's incoming and outgoinf traffic
- You instruct the firewall by giving it rules to check against all the traffic.
- The firewall will allow or deny traffic based on its rules

It's important to note that different types of firewalls work on different OSI model layers.

## Firewall types
|Firewalls|Characteristics|
|---|---|
|Stateless firewalls|- Basic filtering  <br>- No track of previous connections  <br>- Efficient for high-speed networks|
|Stateful firewalls|- Recognize traffic by patterns  <br>- Complex rules can be applicable  <br>- Monitor the network connections|
|Proxy firewalls|- Inspect the data inside the packets as well  <br>- Provides content filtering options  <br>- Provides application control  <br>- Decrypts and inspects SSL/TLS data packets|
|Next-generation firewalls|- Provides advanced threat protection  <br>- Comes with an intrusion prevention system  <br>- Identify anomalies based on heuristic analysis  <br>- Decrypts and inspects SSL/TLS data packets|

### Rules
The basic components of a firewall’s rule are described below:

- **Source address:** The machine’s IP address that would originate the traffic.
- **Destination address:** The machine’s IP address that would receive the data.
- **Port:** The port number for the traffic.
- **Protocol:** The protocol that would be used during the communication.
- **Action:** This defines the action that would be taken upon identifying any traffic of this particular nature.
- **Direction:** This field defines the rule’s applicability to incoming or outgoing traffic.


##### Inbound Rules

Rules are categorized as inbound rules when they are meant to be applied to incoming traffic only. For example, you might allow incoming HTTP traffic (port 80) on your web server.

##### Outbound Rules

These rules are made for outgoing traffic only. For example, blocking all outgoing SMTP traffic (port 25) from all the devices except the mail server.

##### Forward Rules

Forwarding rules are created to forward specific traffic inside the network. For example, a forwarding rule can be created to forward the incoming HTTP (port 80) traffic to the web server located in your network.


## Types of Actions

| Action  | Source         | Destination    | Protocol | Port | Direction |
| ------- | -------------- | -------------- | -------- | ---- | --------- |
| Allow   | 192.168.1.0/24 | Any            | TCP      | 80   | Outbound  |
| Deny    | Any            | 192.168.1.0/24 | TCP      | 22   | Inbound   |
| Forward | Any            | 192.168.1.8    | TCP      | 80   | Inbound   |
- Allow
	- Permits traffic
- Deny
	- Blocks traffic
- Forward
	- Redirects traffic

---

## Linux Firewall

### Netfilter

Netfilter is the framework inside the Linux OS with core firewall functionalities, including packet filtering, NAT, and connection tracking. This framework serves as the foundation for various firewall utilities available in Linux to control network traffic. Some common firewall utilities that utilize this framework are listed below:

- **iptables:** This is the most widely used utility in many Linux distributions. It uses the Netfilter framework that provides various functionalities to control network traffic.
- **nftables:** It is a successor to the “iptables” utility, with enhanced packet filtering and NAT capabilities. It is also based on the Netfilter framework.
- **firewalld:** This utility also operates on the Netfilter framework and has predefined rule sets. It works differently from the others and comes with different pre-built network zone configurations.

### ufw 

ufw (Uncomplicated Firewall), as the name says, eliminates the complications of making rules in a complex syntax in “iptables”(or its successor) by giving you an easier interface. It is more beginner-friendly. Basically, whatever rules you need in “iptables”, you can define them with some easy commands via ufw, which would then be configuring your desired rules in “iptables”.

Commands
```shell-session
sudo ufw status 

//checks the status of the firewall
```

```shell-session
user@ubuntu:~$ sudo ufw enable 

//if it's disables, this enables it
```

```shell-session
sudo ufw default allow outgoing 

// allow all the outgoing connections, the default command means that we are defining this policy as a default policy, outgoing can be replaced by incoming
```

```shell-session
sudo ufw deny 22/tcp

// deny traffic at port 22
```

```shell-session
sudo ufw status numbered

// list all active rules in numbered order
```

```shell-session
sudo ufw delete 2

//delete a rule
```

