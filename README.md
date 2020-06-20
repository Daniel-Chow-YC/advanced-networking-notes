# Networking Concepts and Protocols

## Application Layer Protocols

### HTTP / HTTPS (Hypertext Transfer Protocol Secure)
- Transferring data (transmitting hypermedia documents)
- Was designed for communication between web browsers and web servers, but it can also be used for other purposes.

### FTP / SFTP / TFTP (File Transfer Protocol) and SMB (Server Message Block)
- Transferring computer files between a client and server on a computer network.

### POP3 / IMAP / SMTP
- Transferring / retrieving email

### LDAP / LDAPS (Lightweight Directory Access Protocol)
- Authentication (eg storing usernames and passwords)

### DHCP (Dynamic Host Configuration Protocol)
- A DHCP server dynamically assigns an IP address and other network configuration parameters to each device on a network so they can communicate with other IP networks.

### DNS (Domain Name System)
- A naming system for computers, services, or other resources connected to the Internet or a private network.

### NTP (Network Time Protocol)
- A networking protocol for clock synchronization between computer systems over data networks.

### Telnet and SSH (used for Network Management)
- SSH (Secure Shell) is a protocol for operating network services securely over an unsecured network.

### SNMP (Simple Network Management Protocol)
- An Internet Standard protocol for collecting and organizing information about managed devices on IP networks and for modifying that information to change device behaviour.

### RDP (Remote Desktop Protocol)
- Provides a user with a graphical interface to connect to another computer over a network connection.

### H.323 / SIP
- Audio/visual protocols

## Transport Layer Protocols

### TCP (Transmission Control Protocol)
- Establishes a session between a client and server.
- TCP is connection-oriented, a connection between client and server is established before data can be sent.

### TCP The 3-way Handshake
- Step 1 (SYN) : client wants to establish a connection with server, so it sends a SYN (Synchronize Sequence Number) message to the server
- Step 2 (SYN-ACK) : Server responds to the client request with SYN-ACK signal
- Step 3 (ACK) : The client sends ACK signal to acknowledges the response of the server and they both establish a reliable connection with which they will start the actual data transfer

Client -->---SYN-----> Server

Client <---SYN-ACK-<-- Server

Client -->---ACK-----> Server

### TCP The 4-way Disconnect

Client -->---FIN-----> Server

Client <-----ACK---<-- Server

Client <-----FIN---<-- Server

Client -->---ACK-----> Server

### TCP Reset
- A reset quickly closes the session, and prevents further communication from occurring (its like hanging up the phone).
- When an unexpected TCP packet arrives at a host, that host usually responds by sending a reset packet back on the same connection.
- Either the client, server or third party device (like a firewall) can send a RST.

### UDP (User Datagram Protocol)
- UDP uses a simple ``connectionless`` communication model.
- It speeds up communications by not requiring what’s known as a “handshake”, allowing data to be transferred before the receiving party agrees to the communication.
- This allows the protocol to operate very quickly, so is used for efficient data transfer, but this creates an opening for exploitation.

### Port Numbers (0 - 65,535)
- Port numbers typically identify an application layer protocol that is being used.

### Server Port Numbers (Well know / registered ports) -- Destination Port
- Well known: 0 - 1023
- Registered: 1024 - 49,151 (Custom Applications "Official and Unofficial")

````
HTTP        80
HTTPS       443
FTP         20, 21
SSH         22
Telnet      23
````

### Client Port Numbers (Ephemeral ports) -- Source Port
- An ephemeral port is a short-lived transport protocol port
- Ephemeral: 49,152 - 65,535

## IP Address

### IP address construction
- 4 numbers between 0 - 255 with decimals between each number.
- Each of the 4 numbers are converted into decimal from binary
- An IP address is a 32 bit value broken up into 4 octets (each octet being 8 bits long)
- eg 172.16.0.9

### Classless Addressing - Subnet Mask
- The subnet mask determines the network portion and the host portion of the address.
- Subnet masks are expressed in dot-decimal notation like an address.
- For example, 255.255.255.0 is the subnet mask for the prefix 198.51.100.0/24.

[![Screenshot-21.png](https://i.postimg.cc/HnKwwVm3/Screenshot-21.png)](https://postimg.cc/m1Y1RZtF)

[![Screenshot-20.png](https://i.postimg.cc/65gcR15w/Screenshot-20.png)](https://postimg.cc/Whm0c8kf)

### IP Address Types
- ``Network Address``
  - Identifier for a group of devices
  - Sometimes called "Network Prefix" or just "Prefix"
- ``Host Address``
  - Identifies a unique device on a network
- ``Broadcast Address``
  - Identifier for all devices on a network
  - Broadcast address allows information to be sent to all devices on a given subnet rather than to a specific machine.

#### Network Address
A network address has all 0's in the host portion of the address
[![Screenshot-22.png](https://i.postimg.cc/DyG6Qkj6/Screenshot-22.png)](https://postimg.cc/0b87x3qK)

#### Broadcast Address
A broadcast address has all 1's in the host portion of the address
[![Screenshot-23.png](https://i.postimg.cc/BZLBsf03/Screenshot-23.png)](https://postimg.cc/RqmHQ8hp)

#### Host Address
A host address has anything EXCEPT all binary 0's and 1's
[![Screenshot-24.png](https://i.postimg.cc/q7F6Zgg3/Screenshot-24.png)](https://postimg.cc/jWzjDxHx)

#### Examples
````
IP Address:     192.168.10.0      192.168.10.25     192.168.10.255
Subnet Mask:    255.255.255.0     255.255.255.0     255.255.255.0
Address Type:      Network            Host            Broadcast
````
[![addressing-example-1-1024x576.jpg](https://i.postimg.cc/L5ptNh0V/addressing-example-1-1024x576.jpg)](https://postimg.cc/Q9fKMNDB)

![alt text](https://i.pinimg.com/originals/d1/7e/47/d17e47d5c7561f32b7a5d6c0788ca5ca.jpg)

### CIDR Notation
- The CIDR notation number represents the number of bits (1's) in the binary subnet mask. (This represents the network portion.)
[![Screenshot-25.png](https://i.postimg.cc/q7Z0s3q9/Screenshot-25.png)](https://postimg.cc/XZFT3Xw8)

### Private IP Address
- These 3 ranges of addresses have been set aside so they cannot be used on the public internet
- They can only be used for internal private use
````
Private IP Address Range:
10.0.0.0/8
172.16.0.0/12
192.168.0.0/16
````
- There is one other range the APIPA (Automatic Private IP Addressing) address: 169.254.0.0/16
  - APIPA addresses often don't work so AVOID using it.
- The ``Loopback Address`` -- 172.0.0.1
  - A local address used for testing on your local system

### IPV6

#### Sizes
- ``Bit``
  - 1 or 0
- ``Nibble - 4 bits``
  - 1010
  - Hex - 0xA
- ``Byte - 8 bits``
  - 11001001
  - Hex - 0xC9
- ``Hextet - 16 bits``
  - 10101010 01000110
  - Hex - 0xAA46

#### IPV4 Address Size
- 32 bits long = 4 octets

#### IPV6 Address Size
- 128 bits long = 32 nibbles = 8 hextets
- eg 2001:0DB8:0002:008D:0000:0000:00A5:52F5

- Typically the first 64 bits are the network portion
- And the last 64 bits are the Interface Identifier (the host portion)

- To shorten writing the IPV6 address
  - ``Eliminate leading 0s``
  - ``Then eliminate successive 0's with :: (double colon)``
    - But can only use one double colon per address
    - Typically double colon is used between network portion and host portion at 64 bits

[![Screenshot-27.png](https://i.postimg.cc/cHq61nFY/Screenshot-27.png)](https://postimg.cc/06f9cbR2)

### Ethernet
- A system for connecting a number of devices to form a local area network, with protocols to control the passing of information
- Can be wireless or wired

#### CSMA/CD (Carrier Sense Multiple Access / Collision Detection)
- a set of rules determining how network devices respond when two devices attempt to use a data channel simultaneously (called a collision).
- ``Collision Domain`` : a group of networked devices that will simultaneously detect a voltage spike. (Voltage spike caused by multiple devices sending data at the same time)

#### Duplex
- ``Half duplex``
  - One device communicates at a time
  - Cannot send data simultaneously
  - On old devices / old wiring
- ``Full duplex``
  - Two devices can communicate at same time
  - Collisions not possible for ethernet networks using full duplex
  - Most modern networks are full duplex

#### Network Topology: Star Network
- Star is a topology for a Local Area Network (LAN) in which all nodes are individually connected to a central connection point, like a hub or a switch.

#### Layer 2 Switch: Ethernet Switch
- Ethernet switches link Ethernet devices together
- An ethernet switch prevents collisions
- Does this by breaking up collision domains

#### Spanning Tree Protocol
- Shuts down redundancy
- Prevents loops from occurring

#### VLAN (Virtual Local area network)
-  A VLAN is a subnetwork which can group together collections of devices on separate physical local area networks (LANs).
- The switch can be used to support more than one broadcast domain.

[![Screenshot-28.png](https://i.postimg.cc/FsCLj87r/Screenshot-28.png)](https://postimg.cc/kB8GCjQz)
- Therefore can isolate traffic within the network
- Use VLANs to segment data centres into specific networks for specific purposes
- Can have up to almost 4,000 VLANs on a single switch

#### Port Mirroring
- Is a method of monitoring network traffic.
- The switch sends a copy of all network packets seen on one port (or an entire VLAN) to another port, where the packet can be analysed.

#### Power Over Ethernet (POE)
- Power over Ethernet (POE) is a technology that lets network cables carry electrical power.

### IP Routing

#### Routers
- A gateway is another term for router.
- Routers are special because they have two IP addresses.
- An IP address is assigned to each of the router’s two “interfaces”.
  - The first router interface is called the WAN (Wide Area Network) interface.
    - This is the side of the router that faces the Internet and has a public IP address.
  - The second router interface is called the LAN (Local Area Network) interface.
    - This is the side of the router that faces the home network’s computers and has a private IP address.

#### Default Gateway
- Default gateway can get traffic to other networks
- The default gateway is the place where our PC sends traffic to when it does not know how to reach the destination network.
- Typically on a LAN, this means the IP address we are trying to reach is on a different IP subnet than our PC exists on.
- So PC sends message to default gateway. Then Default gateway sends message to PC on different subnet.
- PC (subnet_1) ---> Default Gateway ---> PC (subnet_2)

#### Routing Table
- This is a data table stored in a router / gateway
- It lists the routes to particular network destinations (and in some cases, metrics associated with those routes).

### Network Services

#### The need for NAT
- Private IP address ranges were created so that any organisation or user could create their own internal network and have IP addresses used for communication
- But these IPs cannot be used on the public internet
- On the public internet a public IP address is needed

#### NAT (Network Address Translation)
- NAT allows a device on an internal private IP address to communicate with the public internet by using the public IP address.
- The specific type of NAT we use is called Port Address Translation (PAT)
  - PAT uses IP addresses along with port numbers
  - PAT is a type of NAT where the multiple private IP addresses are mapped into a single public IP (many-to-one) by using ports.
- PAT allows a single public IP address to be used by many hosts on the private network, which is usually a LAN.

#### Port Forwarding (port mapping)
- Port Forwarding is another component of NAT
  - Note : A socket is an IP address with a port number
- It allows a device residing on an internal network to be available to devices on the opposite side of the gateway (external network), by redirecting the destination socket of the communication request from one socket (the router) to another socket (the intended internal device).
- A port forward is basically a setting that tells your router to take data that shows up on certain ports from specific IPs and send it to a specific device.
- In order for a device on the internet to be able to send a message directly to a device on the inside of your network we have to explicitly configure our router that is connected to the internet to watch for traffic with the specific address properties
- When a packet with these properties come into the router then do the special translation

- Eg when receiving a message from the public internet
  - From the sender on an external network: The destination socket of the message is set to the public IP of the receiver's router (with the appropriate port number)
  - When the message is received by the router the destination socket is swapped out to the private IP of the intended device (and with the appropriate port number)

#### ACLs (Access Control Lists)
- An ACL is a set of rules that is usually used to filter network traffic.
- ACLs can be configured on network devices with packet filtering capabilities, such as routers and firewalls.
- ACLs can be used for traffic shaping

#### Traffic Shaping
- Traffic shaping gives priority on a network to some traffic and does not give priority to other traffic.

#### DHCP (Dynamic Host Configuration Protocol)
- Allows for automatic configuration of IP addresses on your network
- DHCP server can be built into your router or can be separate
- When the DHCP server / router offers and assigns address details to a device, the router / DHCP server then creates a DHCP Binding
- A ``DHCP Binding`` is a record in a database that, for a MAC address, records the assigned:
  - IP Address
  - Default Gateway
  - DNS
- Note : A MAC address is a hardware identification number that uniquely identifies each device on a network.
- The DHCP Binding prevents another device from getting the same IP address

#### DNS URL (Uniform Resource Locator)
- The URL gives DNS a hierarchy so we can find an IP address for a specific url
- TLD (Top Level Domain) eg:
  - .com , .edu , .org , .gov , .uk , .net
- Second Level Domain (usually name of company or resource) eg:
  - ``google``.com, ``amazon``.com, ``wikipedia``.org, ``pluralsight``.com
- Third Level Domain, usually the hostname of a specific device eg:
  - www. (worldwide web server)
  - However, it is not always a hostname eg:
    - www.engineering.university.edu
    - In this example engineering is the subdomain under university but is the third level domain name
    - www. is the fourth level domain name

#### Forward DNS Lookup
- Forward DNS lookup is using an Internet domain name to find an IP address.
  - eg a device asks a DNS server

#### Reverse DNS Lookup
- Reverse DNS lookup is using an Internet IP address to find a domain name.


