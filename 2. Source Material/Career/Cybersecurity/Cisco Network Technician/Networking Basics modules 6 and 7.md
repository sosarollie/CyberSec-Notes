#### Day 5/365
26th of January

Modern networks primarily use three types of media to interconnect devices are:

- **Metal wires within cables** - Data is encoded into electrical impulses.
- **Glass or plastic fibers within cables (fiber-optic cable)** - Data is encoded into pulses of light.
- **Wireless transmission** - Data is encoded via modulation of specific frequencies of electromagnetic waves.

The four main criteria for choosing media are the following:

- What is the maximum distance that the media can successfully carry a signal?
- What is the environment in which the media will be installed?
- What is the amount if data and at what speed must is be transmitted?
- What is the cost of the media installation?

---
Placing one message format inside another message format is called encapsulation. De-encapsulation occurs when the process is reversed by the recipient.
The Ethernet protocol standards define aspects of network communication including frame format, size, timing and encoding. The format for Ethernet frames specifies the location of the destination and source MAC addresses, and additional information including preamble for sequencing and timing, start of frame delimiter, length and type of frame, and frame check sequence to detect transmission errors.
![2. Source Material/Career/Images/Pasted image 20250126231959.png](../../../../7.%20Images/Pasted%20image%2020250126231959%201.png)
*Ethernet frame protocol*

The access layer is the part of the network in which people gain access to other hosts and to shared files.
An Ethernet switch is a device that is used at Layer 2. When a host sends a message to another host connected to the same switched network, the switch accepts and decodes the frames to read the MAC address portion of the message. The switch uses a table to store the known MAC addresses on the network. If a packet is sent and the destination MAC address is not on the table, it will format the packet to every device in the network and said devices will check on their own if the destination MAC address matches its own, if it does it will receive the package and the switch builds a temporary connection called a circuit, if it doesn't, the end device ignores the rest of the package.
The switch builds the actual MAC address table using the SOURCE MAC address and not the destination, when a new host sends a message or responds to a flooded message, the switch learns its MAC address and the port to which the device is connected.
![2. Source Material/Career/Images/Pasted image 20250126232624.png](../../../../7.%20Images/Pasted%20image%2020250126232624%201.png)
*Example of a MAC Address Table inside a switch*

---


