# HTTP

Hyper text transfer protocol used to transfer data over the network. 

HTTP is vulnerable to hackers since the data is sent as clear “text”.

HTTPS is the same as HTTP but with a security feature that scrambles the data sent/received by using SSL or TLS Security
### Security 
- SSL - secure sockets layer; authenticates server and encrypts data
- TLS - Transport layer security; latest industry standard and based on SSL; authenticates server and client and encrypts data.

1. asks for copy of the ssl certificate (used to authenticate that the website is secure)
2. check if the certificate is valid
3. confirms to the server that we trust it
### HTTP Versions
- 1: built on top TCP requiring a tcp per request
- 1.1: introduction of keep-alive by not performing the TCP handshake for every request; introduction of pipelining meaning that several which meant that multiple request could be sent within the same connection with the caveat that the responses had to be sent in the same order; Packet loss and subsequent requests would be 
- 2: introduction of HTTP Streams which allow multiple requests could be sent in the same connection and don’t require order in of responses; bidirectional communication with the necessity of client poll
- 3: Uses QUIC as protocol based on UDP Connection; streams are independent; QUIC implements connection ID which allows the client to change network without losing their connection whereas TCP doesn’t

## Error codes
- 1xx Informational
- 2xx Success
- 3xx Redirection
- 4xx Client Error
- 5xx Server Error

## Request anatomy
- version
- url
- method or verb
- headers
- body (optional)

## Components of HTTP Based systems
- Client: the user-agent : (Usually a browser) the entity initiating the request
- Web server: serves the document and it may actually be a collection of servers sharing load, software, that totally or partially generates the document on demand
- Proxies:
    - caching (the cache can be public or private, like the browser cache)
    - filtering (like an antivirus scan or parental controls)
    - load balancing (to allow multiple servers to serve different requests)
    - authentication (to control access to different resources)
    - logging (allowing the storage of historical information)

Stateless but not sessionless 
- no link between consecutive requests of the same entity
- use of cookies to allowing different requests to share the same context or state


HTTP Flow
1. Open TCP connection
2. Send HTTP request
3. Read response
4. close or reuse connection


HoL: if a packet is lost the bytestream is lost
