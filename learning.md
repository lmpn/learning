# Systems design
## Topics
- [Systems design](#systems-design)
  - [Topics](#topics)
  - [Vertical Scaling](#vertical-scaling)
  - [Horizontal Scaling](#horizontal-scaling)
  - [Load Balancers](#load-balancers)
    - [Advantages](#advantages)
  - [Content Delivery Networks](#content-delivery-networks)
  - [Caching](#caching)
  - [TCP / IP (Transmission Control Protocol \& Internet Protocol)](#tcp--ip-transmission-control-protocol--internet-protocol)
  - [IP Address](#ip-address)
  - [Domain Name System](#domain-name-system)
  - [HTTP/S](#https)
    - [Security](#security)
    - [HTTP Versions](#http-versions)
  - [CORS](#cors)
  - [WebAPI](#webapi)
    - [REST](#rest)
      - [HTTP Codes:](#http-codes)
      - [URI Best Pratices](#uri-best-pratices)
      - [Idempotent API](#idempotent-api)
      - [Response payload](#response-payload)
      - [Versioning](#versioning)
    - [GraphQL](#graphql)
    - [gRPC](#grpc)
    - [WebSockets](#websockets)
  - [Database](#database)
    - [SQL](#sql)
      - [ACID](#acid)
    - [NoSQL](#nosql)
      - [BASE](#base)
    - [Sharding](#sharding)
    - [Replication](#replication)
    - [CAP Theorem](#cap-theorem)
  - [Message Queues](#message-queues)
  - [OAuth2](#oauth2)
  - [Proxy *vs* Reverse proxy](#proxy-vs-reverse-proxy)
  - [SSO](#sso)
  - [API Gateway](#api-gateway)
  - [Distributed Systems](#distributed-systems)
  - [BOOKMARKS](#bookmarks)





## Vertical Scaling
Scale a system by adding hardware resources to a single machine.

Caveats:
- There is a theoretical maximum to what this method can do.
- The price doesn’t scale linearly with capacity. 
- The increase of capacity doesn’t imply that the performance won’t increase in the same ratio as capacity.
- Single point of failure.
## Horizontal Scaling
Scale a system by adding nodes, typically, a [load balancer](##load-balancers) is required to distribute load.

Caveats:
- Hard for databases (application is responsible for DI/O, )
## Load Balancers 
A load balancer is a component that sits between the user and the nodes that perform the processing. Only the LB needs to be public the other machines can have private IP’s (.7)
Functionality provided: 
- Request interception coming from users and forwards them to an available node
- Metrics collection from the nodes
- Customizable balancing strategy
  - Round robin
  - Load based - higher upfront cost
  - Random 

### Advantages 
- Scalability, due to balancing strategies
- Availability, if a machine fails the LB just uses the available machines
- Flexibility, ie: the LB can reroute requests from the old to new machines (software update)
## Content Delivery Networks
CDNs are server that bring content closer to the user, consequently, increases the performance perceived by it. 

A CDN server is often calledn Point of Presence (PoP) or edge server,  it works "like a cache" of an Origin server, and, oftenly, there several PoP across to exploit location to achieve better performance/latency.

The closest PoP's can be found via DNS or Anycast:
- DNS: each PoP has a unique IP
- Anycast: all PoP have the same IP

Key advantages
- Latency - HTTPS handshake latency is reduced since the request is forward to the closet PoP instead of the origin server.
- Security - protect DDoS by having a larger network than the attacker 
- Availability - hardware failure 
- More uptime and less load
## Caching
Store a limited amount of frequently requested items neat to whom is asking for them.

Different types of caches.
     
Different types of eviction:
- Least recently unused
- Random replacement
## TCP / IP (Transmission Control Protocol & Internet Protocol)
AllPeopleSeemToNeedDataProcessing
Application
Presentation
Session
Transport
Network
Data link
Physical
## IP Address
Represents where a machine "is" in the internet and it used to allow communication between machines. An IP is unique series of numbers composed of 4 numbers [0 - 255] separated by a dot.

- Network Address Translation or NAT(tipically router) represents a set of devices connected to a network
- Outside communication: default gateway
- x.x.x.0 and x.x.x.255 within a network are reserved 
## Domain Name System
DNS is system that resolves websites domain names like www.google.com into IP addresses.
- Root Nameservers store the Top Level domain Nameservers
- Top Level domain Nameservers store the Authoritative Nameservers
- Caching is everywhere (browser, OS, DNS resolver)

If the DNS resolver asks the RN, then the TLDN, then the AN, and finally forwards the answer to the requestor
## HTTP/S
Hyper text transfer protocol used to transfer data over the network. 

HTTP is vulnerable to hackers since the data is sent as clear “text”.

HTTPS is the same as HTTP but with a security feature that scrambles the data sent/received by using SSL or TLS Security
### Security 
- SSL - secure sockets layer; authenticates server and encrypts data
- TLS - Transport layer security; latest industry standard and based on SSL; authenticates server and client and encrypts data.

1. - asks for copy of the ssl certificate (used to authenticate that the website is secure)
2. - check if the certificate is valid
3. - confirms to the server that we trust it
### HTTP Versions
- 1: built on top TCP requiring a tcp per request
- 1.1: introduction of keep-alive by not performing the TCP handshake for every request; introduction of pipelining meaning that several which meant that multiple request could be sent within the same connection with the caveat that the responses had to be sent in the same order; Packet loss and subsequent requests would be 
- 2: introduction of HTTP Streams which allow multiple requests could be sent in the same connection and don’t require order in of responses; bidirectional communication with the necessity of client poll
- 3: Uses QUIC as protocol based on UDP Connection; streams are independent; QUIC implements connection ID which allows the client to change network without losing their connection whereas TCP doesn’t


## CORS
- Cross Origin Resource Sharing allows one url to request data from another url.
- Same Origin Policy is part of the security features of a browser.
- The server must include the proper header when responding.
- Non-standard verbs must be preflighted which is a sanity check that can be cached
- The OPTIONS verb response must allow CORS and must send the allowed headers 

## WebAPI
### REST
Representational State Transfer is the most common archicteture to allow communication between clients and servers.

The REST defines some loose rules to build web API.

Rules:
- Uniform interface
- Client-Server : Servers and clients may also be replaced and developed independently, as long as the interface between them is not altered.
- Stateless : No client context shall be stored on the server between requests. The client is responsible for managing the state of the application.
- Cacheable : Well-managed caching partially or completely eliminates some client-server interactions, further improving scalability and performance.
- Layered System : A client cannot ordinarily tell whether it is connected directly to the end server or an intermediary along the way.
- CoD (Optional)

Resources are defined by Uniform Resource Identifiers (URI).
A URI should define a resource by its name i.e: 
- /api/v1/products *correct*
- /api/v1/getAllProducts *incorrect*

A client interacts with a resource by performing an HTTP request which is composed by
- Headers
- Operation/Verb/Method - action to perform
- URI - resource to interact
- Parameters/Body - data to sent 

#### HTTP Codes:
- 200-level success
- 400-level client side error
- 500-level sever side error

#### URI Best Pratices
1. Forward slashes denote hierarchy
2. Plural nouns for branches (?)
3. Hypens for multiple words
4. Use lowercase
5. Refrain from using file extensions

#### Idempotent API 
Multiple requests with the same URI, verb, headers have the same result.

#### Response payload
Use pagination when the payload to return is high. 
The following URI demonstrates how pagination can be implemented: 

```/v1/products/count=10&offset=50```

Now imagine that the products is a collection of 100 items. 
The above example has two query parameters the *count* and *offset*. 
- *count* is the number of elements to be returned
- *offset* is the number of elements to ignore from the beggining

#### Versioning
The consumers of the API might not have the ability to keep their software up to date and/or they might not want to touch their side of the code.
With versioning the development is ensured and the consumers aren't forced to update because the newer version broke backwards compatibility.
### GraphQL
### gRPC
### WebSockets

## Database
### SQL
#### ACID
### NoSQL
#### [BASE](https://en.wikipedia.org/wiki/Eventual_consistency)
### Sharding
### Replication
### CAP Theorem
CAP Theorem of Brewer's theorem states that any distributed data store will only be able to comply with 2 of 3 of the following properties:
- Consistency: the lastest read corresponds to the latest write or an error
- Availability: Every request receives a (non-error) response, without the ensure that it will correspond to the latest write
- Partition: System continues to operate regardless of the number of messages dropped or delayed by the network

Consistency and Availability can be achieved if there is no network partition. Since the theorem applies to DDS then network partition must be ensured and one of two approaches must be taken when an NP error happens:
- cancel the operation favouring consistency
- continue the operation favouring availability

## Message Queues
## OAuth2
## Proxy *vs* Reverse proxy
## SSO
## API Gateway


## Distributed Systems

## BOOKMARKS
https://www.commandlinefu.com/commands/browse
https://cucumber.io/docs/gherkin/reference/
https://github.com/karan/Projects

c++
https://github.com/cpp-best-practices/cppbestpractices -> JTurner advices
https://cppinsights.io/ -> generated code
https://godbolt.org/ -> compiler explorer
https://perfbench.com/
https://quick-bench.com/
https://www.onlinegdb.com/
rust
https://docs.google.com/document/d/1kQidzAlbqapu-WZTuw4Djik0uTqMZYyiMXTM9F21Dz4/edit

tut
https://decovar.dev/blog/2021/03/08/cmake-cpp-library/#building-and-installing


