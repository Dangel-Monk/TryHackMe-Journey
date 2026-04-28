
| Task 1 | = Introduction = |
| - | - |

> Have you ever wondered how your computer can dynamically configure its network settings when you turn it on or connect it to a new network? Have you ever wanted to know how many devices and countries your packets passed through before reaching their destination?

+ *Wait a minute, I've seen this before? Besides, yes, I don't know how the internet works, that's why I'm here.*
<br>

\> Learning Objectives
>
>  \a) Dynamic Host Configuration Protocol (DHCP) <br>
>  \b) Address Resolution Protocol (ARP) <br>
>  \c) Network Address Translation (NAT) <br>
>  \d) Internet Control Message Protocol (ICMP)

----
<br>



| Task 2 | = DHCP Give me my network settings = |
| - | - |

> Whenever we want to access a network, at the very least, we need to configure the following
>
> >  \a) IP address along with subnet mask <br>
> >  \b) Router (or gateway) <br>
> >  \c) DNS server
>
> Whenever we connect our device to a new network, the above configurations must be set according to the new network. Manually configuring these settings is a good option, especially for servers.
>
> Having an automated way to configure connected devices has many advantages. First, it would save us from manually configuring the network; this is extremely important, especially for mobile devices. Secondly, it saves us from address conflicts, i.e., when two devices are configured with the same IP address. An IP address conflict would prevent the involved hosts from using the network resources; this applies to local resources and the Internet.

+ *While you could manually configure your devices' adapters/networks by hand (which has its advantages), doing so automatically in multi-device/varied environments would be complicated. I wonder if it can be modified manually after it's automated...*

> The solution lies in using Dynamic Host Configuration Protocol (DHCP). DHCP is an application-level protocol that relies on UDP; the server listens on UDP port `67`, and the client sends from UDP port `68`. Your smartphone and laptop are configured to use DHCP by default. DHCP follows four steps: Discover, Offer, Request, and Acknowledge.
>
> >  \1) DHCP Discover <br>
> >  The client broadcasts a DHCPDISCOVER message seeking the local DHCP server if one exists.
> > 
> >  \2) DHCP Offer <br>
> >  The server responds with a DHCPOFFER message with an IP address available for the client to accept.
> > 
> >  \3) DHCP Request <br>
> >  The client responds with a DHCPREQUEST message to indicate that it has accepted the offered IP.
> > 
> >  \4) DHCP Acknowledge <br>
> >  The server responds with a DHCPACK message to confirm that the offered IP address is now assigned to this client.

+ *If I understand correctly, since it's automating IPs not only within the local network but also external networks, it operates at layer 4? Because it also involves ports... oooh nevermind, DHCP uses ports and assigns ip, but its an application that interacts from point to point, so its layer 7...*

      The first step would be to send a signal to find out if there's a protocol for dynamically configuring hosts? It's a way of relating DHCP.

      -- (Discover) ->    0.0.0.0 > 255.255.255.255 (The broadcast IP)
      "Hey, I'm a new device, who manages it?"

      <- (Offer) --    0.0.0.0 < 192.168.66.1
      "Oh, how are you? We have this space available." (192.168.66.133)

      -- (Request) ->    0.0.0.0 > 255.255.255.255
      "Sure, I'd like to use that space..."

      <- (Acknowledge) --    (192.168.66.133) < 192.168.66.1
      "No problem, others can see that you're using it."

> The client starts without any IP network configuration. It only has a MAC address. In the first and third packets, DHCP Discover and DHCP Request, the client searching for a DHCP server still has no IP network configuration and has not yet used the DHCP server’s offered IP address. Therefore, it sends packets from the IP address `0.0.0.0` to the broadcast IP address `255.255.255.255`. <br>

+ *I understand using the broadcast IP address in the Network Layer, but why would I also do it with the Data Link Layer using MAC addresses?*

----
<br>



| Task 3 | = ARP Bridging Layer 3 Addressing to Layer 2 Addressing = |
| - | - |

> Whenever one host needs to communicate with another host on the same Ethernet or WiFi, it must send the IP packet within a data link layer frame. Although it knows the IP address of the target host, it needs to look up the target’s MAC address so the proper data link header can be created.
>
> However, the devices on the same Ethernet network do not need to know each other’s MAC addresses all the time; they only need to know each other’s MAC addresses while communicating. Everything revolves around IP addresses.

+ *Consider this scenario:*

\a) You connect your device to a network, and if the network has a DHCP server, your device is automatically configured to use a specific gateway (router) and DNS server. <br>
\b) Consequently, your device knows the IP address of the DNS server to resolve any domain name; moreover, it knows the IP address of the router when it needs to send packets over the Internet.

+ *In all this scenario, no MAC addresses are revealed. However, two devices on the same Ethernet cannot communicate without knowing each other’s MAC addresses.*

> Address Resolution Protocol (ARP) makes it possible to find the MAC address of another device on the Ethernet.
>
> > \1. A host with the IP address `192.168.66.89` wants to communicate with another system with the IP address `192.168.66.1`. It sends an ARP Request asking the host with the IP address `192.168.66.1` to respond.
>
> > \2. The ARP Request is sent from the MAC address of the requester to the broadcast MAC address, `ff:ff:ff:ff:ff:ff` as shown in the first packet.
>
> > \3. The ARP Reply arrived shortly afterwards, and the host with the IP address `192.168.66.1` responded with its MAC address. From this point, the two hosts can exchange data link layer frames.

      -- (ARP Request) ->      cc:5e:f8:02:21:a7 > ff:ff:ff:ff:ff:ff (The broadcast MAC)
      "Hey, is anyone using the IP address 192.168.66.1?
            Let me know at my IP address 192.168.66.89... "

      <- (ARP Reply) --      cc:5e:f8:02:21:a7 < 44:df:65:d8:fe:6c
      "Oh, I'm using it, let me introduce myself... "

> An ARP Request or ARP Reply is not encapsulated within a UDP or even IP packet; it is encapsulated directly within an Ethernet frame. The following ARP Reply shows this.

+ *ARP is considered layer 2 because it deals with MAC addresses. Others would argue that it is part of layer 3 because it supports IP operations. What is essential to know is that ARP allows the translation from layer 3 addressing to layer 2 addressing.*
  
----
<br>



| Task 4 | = ICMP Troubleshooting Networks = |
| - | - |

> Internet Control Message Protocol (ICMP) is mainly used for network diagnostics and error reporting. Two popular commands rely on ICMP, and they are instrumental in network troubleshooting and network security.
>
> > `ping` <br>
> > This command uses ICMP to test connectivity to a target system and measures the round-trip time (RTT). In other words, it can be used to learn that the target is alive and that its reply can reach our system.
> >
> > `traceroute` <br>
> > This command is called `traceroute` on Linux and UNIX-like systems and `tracert` on MS Windows systems. It uses ICMP to discover the route from your host to the target.
<br>

\> Ping

> The ping command sends an ICMP Echo Request (ICMP Type 8).
```
ping [arguments]		   (Linux)

      -I [interface]           Specify source interface/IP. Crucial when a machine has multiple network interfaces.

      -n                       Numeric output only. Prevents reverse DNS lookups, speeds up output.
      -4 / -6                  Force IPv4 or IPv6. Useful for testing a specific IP version.
      -q                       Quiet output. Only shows the final summary statistics.

      -c [count]               Limit the number of pings. Stops after sending the specified number of packets.
      -t [ttl]                 Set Time to Live (TTL). Limits the packet's maximum number of hops.
      -w [deadline]            Set a total deadline. Exits after the specified number of seconds, regardless of packets sent/received.
      -W [timeout]             Set per-packet timeout. Time to wait for a response for each individual packet.

      -i [interval]            Change the ping interval. Waits the specified number of seconds between pings (default is 1 second).
      -s [packet size]         Change packet size. Specifies the number of data bytes to send (default is 56).

      -f                       Flood ping. Sends packets as fast as possible. Use with caution as it can overwhelm the network.
```
<br>

\> Traceroute

> The Internet protocol has a field called Time-to-Live (TTL) that indicates the maximum number of routers a packet can travel through before it is dropped. The router decrements the packet’s TTL by one before it sends it across. When the TTL reaches zero, the router drops the packet and sends an ICMP Time Exceeded message (ICMP Type 11). (In this context, “time” is measured in the number of routers, not seconds.)
```
traceroute [arguments]      (Linux)

      -s [src_addr]             Specify source address. Forces the probe to originate from a particular interface's IP.

      -I                        Use ICMP Echo Requests. Often gets through firewalls better than the default UDP.
      -T                        Use TCP SYN packets. Great for testing specific services or bypassing ICMP/UDP filtering.
      -U                        Use UDP...?
      -p [port]                 Specify destination port. Required for TCP (-T) or UDP (-U) to target a service.

      -4 / -6                   Force IPv4 or IPv6. Explicitly traces the route using a specific IP version.
      -n                        Skip DNS resolution. Displays only IP addresses, making the trace much faster.

      -f [first_ttl]            Set initial TTL. Skips the first few hops to start tracing further along the path.
      -m [max_ttl]              Set max number of hops. Stops tracing after the specified number of hops (default is 30).
      -q [n-queries]            Number of probes per hop. Sets how many packets are sent to each hop (default is 3).
      -w [timeout]              Set per-hop timeout. How long to wait for a response from each hop.

      -A                        Perform AS path lookups. Looks up the Autonomous System (AS) number for each hop.
      -F                        Set "Don't Fragment" bit. Useful for discovering issues with packet sizes.
```
> Routers that belong to our ISP might respond, revealing their private IP address. Moreover, some routers respond and show their public IP address, and this would let us look up their domain name and discover their geographic location. Finally, there is always a possibility that an ICMP Time Exceeded message gets blocked and never reaches us.

----
<br>



| Task 5 | = Routing = |
| - | - |

> The Internet is made up of millions of routers and billions of devices. The mobile user can reach the web server; however, for this to happen, each router across the path needs to send the packets via the appropriate link. Obviously, there is more than one path, i.e., route, connecting the mobile user and the web server. We need a routing algorithm for the router to figure out which link to use.

> Just to name a few, there are variations in how to find the best route:
>
> > \a) OSPF (Open Shortest Path First) <br>
> > OSPF is a routing protocol that allows routers to share information about the network topology and calculate the most efficient paths for data transmission. It does this by having routers exchange updates about the state of their connected links and networks. This way, each router has a complete map of the network and can determine the best routes to reach any destination.
> >
> > \b) EIGRP (Enhanced Interior Gateway Routing Protocol) <br>
> > EIGRP is a Cisco proprietary routing protocol that combines aspects of different routing algorithms. It allows routers to share information about the networks they can reach and the cost (like bandwidth or delay) associated with those routes. Routers then use this information to choose the most efficient paths for data transmission.
> >
> > \c) BGP (Border Gateway Protocol) <br>
> > BGP is the primary routing protocol used on the Internet. It allows different networks (like those of Internet Service Providers) to exchange routing information and establish paths for data to travel between these networks. BGP helps ensure data can be routed efficiently across the Internet, even when traversing multiple networks.
> >
> > \d) RIP (Routing Information Protocol) <br>
> > RIP is a simple routing protocol often used in small networks. Routers running RIP share information about the networks they can reach and the number of hops (routers) required to get there. As a result, each router builds a routing table based on this information, choosing the routes with the fewest hops to reach each destination.

+ *As you can see, it may seem like the most complicated thing in the world, with 'impossible algorithms' but stop for a moment and think... what do they have in common?.*
+ *In most cases, routers provide information about the network and its connections. From this, you can determine the number of routers involved and the distance between them. Finally, you choose the most efficient option...*

----
<br>



| Task 6 | = NAT = |
| - | - |

> With the increase in the number of devices connected to the Internet, from computers and smartphones to security cameras and washing machines, it was clear that the IPv4 address space would be depleted quickly. One solution to address depletion is Network Address Translation (NAT).
>
> The idea behind NAT lies in using one public IP address to provide Internet access to many private IP addresses. In other words, if you are connecting a company with twenty computers, you can provide Internet access to all twenty computers by using a single public IP address instead of twenty public IP addresses.

+ *There's a really cool story behind NAT as a 'solution' to a big fuck up of IP distribution, But as a result, I'm scared by the idea that if someone can find out your public IP address, they could access your specific network where all your devices are connected. Even worse, could they track you?*

> Unlike routing, which is the natural way to route packets to the destination host, routers that support NAT must find a way to track ongoing connections. Consequently, NAT-supporting routers maintain a table translating network addresses between internal and external networks. Generally, the internal network would use a private IP address range, while the external network would use a public IP address.

      > Internal Network (192.168.0/24)          |      > External Network (212.3.4.5)

      Cameras (xxx.xxx.xxx.129)      :15401      <      (xxx.xxx.xxx.xxx)      :23123
      Computer (xxx.xxx.xxx.125)     :27912      <      (xxx.xxx.xxx.xxx)      :34532  
      Laptop (xxx.xxx.xxx.112)       :38192      <      (xxx.xxx.xxx.xxx)      :87321
      Mobile (xxx.xxx.xxx.137)       :45691      <      (xxx.xxx.xxx.xxx)      :98632

+ *So when you connect a device to the internet (let's say a website), it communicates with your device through a public port, but upon entering your network, it redirects to the port that your device uses?*

----
<br>
