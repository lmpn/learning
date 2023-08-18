# DNS

Domain name system is a hierarchical and structured nameing system for internet connected resources.
DNS has as main function the translation of domain names into ip addresses which eliminates the need of memorizing the IPv4 or IPv6 address of a device.

Domain names are a key part of the Internet infrastructure. They provide a human-readable address for any web server available on the Internet.

To perform a the tranlation it is necessary to perform a DNS lookup or DNS query.

DNS Servers involved in a DNS query:
- DNS recursor
- Root Nameservers store the Top Level domain Nameservers
- Top Level domain Nameservers stores nameservers
  - stores the nameservers that end in ".com" or ".org" or ".edu"
- Authoritative Nameservers store the IP addresses of the domain name queried

Steps of DNS query:
- Query DNS resolver
- Resolver queries root nameserver
- Return Top level domain nameservers
- Query top level domain nameserver
- Return ip addresses of nameservers
- Query nameservers
- Return IP address of domain name
- DNS resolver return IP address to browser
- HTTP Request from the browser to the ip address
- Server return web page which is rendered by the browser

Notes:
- Caching is everywhere (browser, OS, DNS resolver)
- foo.example.com or blog.cloudflare.com, an additional nameserver will be added to the sequence after the authoritative nameserver