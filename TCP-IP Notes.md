# TCP/IPv4 Basics
## TCP/IP Model

Some things to consider is how TCP/IP is set up by looking at the Individual Layers:

| Layer | TCP/IP Model | Protocols/Functions |
| ---- | ---- | ---- |
| Application | Application | HTTP, FTP, SMTP, DNS, Telnet, SSH, SNMP, etc. |
| Transport Layer | Transport | TCP, UDP |
| Internet | Internet | IP, ICMP, ARP, DHCP. NAT.OSPF. BGP, IPv6 |
| Link | Network Access | Ethernet, Wi-Fi, PPP, DSL, MPLS, etc. |
**Application Layer** - Represent the user's interface (UI)/web browser or other network based application
**Transport Layer** - Manages data transport issues.
**Internet Layer** - Identifies sender/receiver 
**Interface Layer** - Physical cards and hardware like NIC's

## Network Communication 

Application programs on direct computers can't communicate directly, they have to rely on layered communication to make packets indirect. 

Encapsulation of packets helps to embed a message received from another layer of the [[#TCP/IP Model]]. Here's how it does it:

| Layer                     | Packet Contents                                                                    |
| ------------------------- | ---------------------------------------------------------------------------------- |
| Application (Web Browser) | \| HTTP request \|                                                                 |
| Transport Layer (TCP)     | \| HTTP request \| TCP -Header \|                                                  |
| Internet Layer (IPv4)     | \| HTTP request \| TCP -Header \| IP-Header \|                                     |
| Data Link (Wi-Fi)         | \| Data-Link Head \| HTTP request \| TCP -Header \| IP-Header \|  Data-Link Tail\| |
### Frames and Packets

To transmit a single packet, you have to use frames as you pass through switches and routers. If you had two hosts transmitting a packet along 6 different networks, you would have 6 frames because you jump through 6 different routers.

## Structure of an IP Packet
| Version | Header Length | Diff-Serv | Total Length (in Octets) |
| ---- | ---- | ---- | ---- |
|  |  |  |  |