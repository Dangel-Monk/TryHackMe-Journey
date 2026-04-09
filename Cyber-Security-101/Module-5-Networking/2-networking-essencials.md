
| Task 1 | = Introduction = |
| - | - |

> Have you ever wondered how your computer can dynamically configure its network settings when you turn it on or connect it to a new network? Have you ever wanted to know how many devices and countries your packets passed through before reaching their destination?

+ *Wait a minute, I've seen this before? Besides, yes, I don't know how the internet works, that's why I'm here.*

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

+ *While you could manually configure your devices' adapters/networks by hand (which has its advantages), doing so automatically in multi-device/varied environments would be complicated. I wonder if it can be modified manually after it's automated?*

> The solution lies in using Dynamic Host Configuration Protocol (DHCP). DHCP is an application-level protocol that relies on UDP; the server listens on UDP port `67`, and the client sends from UDP port `68`. Your smartphone and laptop are configured to use DHCP by default. DHCP follows four steps: Discover, Offer, Request, and Acknowledge...
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

      The first step would be to send a signal to find out if Is there a protocol for dynamically configuring hosts? It's a way of relating DHCP.

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

