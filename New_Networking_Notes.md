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

### CIDR Notation
- The CIDR notation number represents the number of bits (1's) in the binary subnet mask. (This represents the network portion.)
[![Screenshot-25.png](https://i.postimg.cc/q7Z0s3q9/Screenshot-25.png)](https://postimg.cc/XZFT3Xw8)
