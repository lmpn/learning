# Internet

It is necessary to have grasp of what is internet and how it works since modern software relies upon it.

## Index
1. Introduction to the Internet
2. How the Internet works: An overview

## [Introduction to the Internet](introduction-to-the-internet)

Developed in 1960 by the USA as a means to have a descentralized communication network in case of a nuclear attack.

To understant the Internet it is necessary to understand what is a network within this context. A network is a group of computers connected to each other and simply put:

***The internet is a network of networks***

The network may be divided into three components: the last mile, data centers, and the backbone.

Note that the internet is descentralized and no one "runs" but rather there is an agreement between providers where they adhere or not to standards that allow intercommunication between networks.

The Internet nowadays is essential since it connects people to each other, allows bussineses to be conducted and more, thus, as developer it is necessary to understand it and the protocols associeted with it.

## [How the Internet works: An overview](how-the-internet-works-an-overview)

The Internet at its core is a global network of routers which are responsible for directing the data flow between devices and systems. When a device sends data through the Internet this data in broken down in several packets which are forwarded between routers until it reaches the final destination.

The send and receive of data needs to be correct its used the IP protocol, responsible for the routing the data to the correct recipient, and the TCP protocol, responsible for ensuring order and reliability of the data sent.

Other protocols:
- Domain Name System
- HTTP/HTTPS
- SSL/TLS

## [The role of protocols in Internet](the-role-of-protocols-in-internet)

A protocol is a set of rules and standards that define how information should be exchanged between devices and systems.

Examples:
- TCP and UDP: ensure that packets are delivered efficiently
- IP: ensure that the data reaches the correct destination
- DNS: translate Domain names into IP addresses

The key benifit of protocols is that they enable devices from different manufacturers and vendors to communicate with each other.

## [Understanding IP Addresses and Domain Names]

IP address: unique identifier assigned to each device on a network 
Domain name: human readable name give to websites of internet resources.

Domain names are translated into IP addresses using DNS which is a critical part of the internet infrastructure.

## [Introduction to HTTP and HTTPS]
The visit to a website normally implies that the web browser request for data usign Hypertext transfer protocol is used to transfer data between a client and server.

HTTPS is a more secure version of HTTP, that encrypts/decrypts the data using SSL/TLS.

## [Building Applications with TCP/IP]

Concepts:
- Ports
- Sockets
- Connections
- Data transfer

TCP/IP protocol provides reliable, ordered, and error checked delivery of data between communication different devices.
Applications built with TCP/IP need to ensure proper usage of sockets, ports and connections.

## [Securing Internet Communication with SSL/TLS]

Concepts:
- Certificates
- Handshake
- Encryption

Protocol used to encrypt and decrypt data transmitted over the internet.
Internet applications may handle sensitive information ie: login credentials, thus, it is *required* to ensuring integrity and confidentiality of the data.

## [What is the cloud?]
Approach to computing that consists in storing files and delivering software of the internet.

## [Concepts]
- **Packet**: small unit of data transmitted over the internet
- **Router**: device that directs packtes of data between different networks
- **IP Address**: A unique identifier attributed to each device on a network, used to route data to the correct destination
  - IPV4
  - IPV6
- **Domain name**: A human-readable name that is used to identify a website
- **DNS**: responsible for translating domain names into IP addresses
- **HTTP**: Hypertext transfer protocol is used to transfer data between a client and server
- **HTTPS**: An encrypted version of HTTP
- **SSL/TLS**: provide secure communication over the internet
- Ports
- Sockets
- Connections
- Data transfer
- Certificates
- Handshake
- Encryption
- Last Mile: part of the internet that connects homes and small bussinesses to the Internet.
- Data center: room of servers that store user data and host apps and content; they have fast internet connections allowing them to handle multiple users at once.
- Backbone: consists of long-distance networks normally over optic fiber 
- Browser: a web browser is a computer program that allows user to download and view websites
