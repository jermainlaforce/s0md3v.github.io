---
layout: post
title: IP Addresses & Ports Explained for Dummies
description: "A fun explanation of what IP addreses and ports are"
modified: 25-10-2018
tags: [ports, ip address, networking]
image:
  path: /images/featured/ip-ports.png
  feature: /featured/ip-ports.png
---

Internet is basically a network of billions of devices just like humans.
So what do you do when you need connect to a remote human? You just call them right? or send them a letter?
But for doing that you need their phone number or address. Similarly, to connect to a remote device, you need it's address which is called IP address.
Each device which is a part of internet has an IP address which gives it a unique identiy.

An IP address looks like this:
```
202.87.58.20
```
You can see that it has 4 numbers, well each of these numbers can range from 0-255.
Which means there can't be an IP address such as 192.533.0.234
You must be thinking why 255? Why not 255 or 191283?
Well, when they were designing this whole internet thing,
they just had 32 bits to represent the IP address so they split the 32 bits into 4 equal parts i.e `8 + 8 + 8 + 8 = 32`.
So there are 8 bits available for each number and as we know, computers understand binary which boils down to 0s and 1s.
If you had to write, 69 in binary, it would be `1000101` which doesn't hit the 8 bit limit.
255 is `11111111` which is largest value you can have within that limit so that's the reason.

Well, you can create `4,294,967,296` unique combinations with this but apparently they aren't enough because the number of devices on the internet is growing rapidly that's why we designed IPv6 Addresses.
The IP address we just discussed is a IPv4 Address.
An IPv6 Address looks like this:
```
2404:6800:4002:807::200e
```
It has a 128 bits limit which makes it possible to create `340,282,366,920,938,463,463,374,607,431,768,211,456` unique IP Address.

You got it how IP Addreses help us to connect right?
Well it's not that simple. What if want to connect to someone over his teamviewer while he is browsing some website?
My computer will send his computer some data packet but how will his computer know for which service these packets are? TeamViewer or the browser?

Well this is where ports come into play.
Each service on your computer which needs to connect to the internet is given a number from 0-65536.
When a service is establishing a connection with a remote device, it can tell that device that
*Hey! I am running on port no. 69, please include this number when you send data packets for me so the computer can know it's for me.*

That's how ports work. They help in distinguishing between different services.

You can host any service on any port but some standard ports for various services are:

|Port|Service|
|---|---|
|1 |TCP Port Service Multiplexer (TCPMUX)|
|5 |Remote Job Entry (RJE)|
|7 |ECHO|
|18 |Message Send Protocol (MSP)|
|20 |FTP — Data|
|21 |FTP — Control|
|22 |SSH Remote Login Protocol|
|23 |Telnet|
|25 |Simple Mail Transfer Protocol (SMTP)|
|29 |MSG ICP|
|37 |Time|
|42 |Host Name Server (Nameserv)|
|43 |WhoIs|
|49 |Login Host Protocol (Login)|
|53 |Domain Name System (DNS)|
|69 |Trivial File Transfer Protocol (TFTP)|
|70 |Gopher Services|
|79 |Finger|
|80 |HTTP|
|103| X.400 Standard|
|108| SNA Gateway Access Server|
|109| POP2|
|110| POP3|
|115| Simple File Transfer Protocol (SFTP)|
|118| SQL Services|
|119| Newsgroup (NNTP )|
|137| NetBIOS Name Service|
|139| NetBIOS Datagram Service|
|143| Interim Mail Access Protocol (IMAP)|
|150| NetBIOS Session Service|
|156| SQL Server|
|161| SNMP|
|179| Border Gateway Protocol (BGP)|
|190| Gateway Access Control Protocol (GACP)|
|194| Internet Relay Chat (IRC)|
|197| Directory Location Service (DLS)|
|389| Lightweight Directory Access Protocol (LDAP)|
|396| Novell Netware over IP|
|443| HTTPS|
|444| Simple Network Paging Protocol (SNPP)|
|445| Microsoft-DS|
|458| Apple QuickTime|
|546| Client|
|547| DHCP Server|
|563| SNEWS|
|569| MSN|
|108|0 Socks|
