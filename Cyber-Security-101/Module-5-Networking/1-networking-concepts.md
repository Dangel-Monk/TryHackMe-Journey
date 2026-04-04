
| Task 1 | = Introduction = |
| - | - |

> Have you ever wondered why you need an IP adress to access the Internet? Is it true that an IP address can uniquely identify the user? Are you curious to learn what the life of a packet looks like?

+ *(idk) To be honest, when they tried to explain it in 'Pre-security' it was just long walls of text… *

----
<br>



| Task 2 | = OSI Model = |
| - | - |

> Before we start, we should note that the OSI model might initially seem complicated... Don't worry... by the time you finish this module, this task will feel like a piece of cake.

+ *Am I really that stupid for not understanding this? I feel like I have to pray to God so I don't have to write it on the walls…*

> The OSI (Open Systems Interconnection) model is a conceptual model developed by the International Organization for Standardization (ISO) that describes how communications should occur in a computer network. In other words, the OSI model defines a framework for computer network communications.

+ *The main idea of ​​the model is not to memorize it, but to understand and internalize it in order to know how it works.*
<br>

\> Layer 1: Physical Layer (Electrical, optical, and wireless signals)

+ *To put it simply, it's anything you can touch... it's not limited to just a cables like Ethernet. Is it an antenna? Is it infrared port? Is it an object that transmits signals? Make sure to rub it gently with your fingers so as not to scare away the electromagnetic radiation.*

+ *Better yet, I will focus on using a hypothetical city, where the physical aspect is how everything connects: roads, vehicles, airports, antennas, drones, trains, a postal service, everything that entails.*


\> Layer 2: Data Link Layer (Ethernet (802.3), WiFi (802.11))

> This layer involves the recognition of the transmission media, where different systems reach an agreement on how to connect. I suppose the list the devices, their capabilities, brand and specifications, and which ones are available to both the deliver and receptor.

+ *In this layer, let's think of the media as a vehicle, which is driven by a driver. This layer not only recognizes all the different media by their types (MAC address as license plates + specs) but it ensures that the vehicle (data frame) does not collide with other packets and ensures that it arrives intact (or will it report otherwise?).*

+ *That's why you can do MAC Spoofing, you put the license plates of another vehicle on yours... but is that the only way to break this layer?*


\> Layer 3: Network Layer (IP, ICMP, IPSec)

> The main function of this layer is to send data, finding a path to transfer packets between different networks. Some examples, Internet Control Message Protocol (ICMP), Virtual Private Network (VPN). 

+ *In this situation, while the previous layer is responsible for a general recognition of the devices, in this one the driver has the IP address of the other city, Using this information, plan the best route by consulting routing tables (DNS?) through the various networks...*


\> Layer 4: Transport Layer (UDP, TCP)

> Once the route has been established, this layer is responsible for creating end-to-end communication with functions such as flow control, error correction, segmentation...

+ *From a general perspective, this is where the decision regarding shipping quality comes in. Is speed or reliability more important? Are we interested in verifying the integrity of the shipment, or do we just want to send it?*


\> Layer 5: Session Layer (NFS, RPC)

> Once communication is established, this layer is responsible for monitoring, synchronizing, and maintaining the connection, taking into account the session parameters. It ensures in-order transfers and recovery methods...

+ *Let's imagine we have a reception center, where once the data is received it verifies the information, establishes the exchange, discerns the type of information received and ends the sessions.*


\> Layer 6: Presentation Layer (Unicode, MIME, JPEG, PNG, MPEG)

> The presentation layer ensures the data is delivered in a form the application layer can understand, handles the data encoding, compression and encryption.

+ *Let's say the package is already in the city, but how can we deliver it? In this layer, we group by use, rewrite the lithograph to understand it, and encrypt it so that only the people involved can see its contents.*


\> Layer 7: Application Layer (HTTP, FTP, DNS, POP3, SMTP, IMAP)

> As the final layer, you are presented with an interface (applications) that takes all these packets and makes them available to the user. Different protocols require different applications.

+ *Well, have you used Chrome? Maybe YouTube? Even Gmail? (Glorious Monopoly x_x) All these interfaces make it easier to perform tasks quickly instead of reading all these raw packets, and they also make it easier to classify them.*

----
<br>



| Task 3 | = TCP/IP MODEL = |
| - | - |

> One of the strengths of this model is that it allows a network to continue to function as parts of it are out of service, for instance, due to a military attack. This capability is possible in part due to the design of the routing protocols to adapt as the network topology changes.

+ *As a point of interest, this type of connection offers us the strength of information integrity and the ability to be redundant in case of failure, thanks to its adaptability...? Due to its function, it is grouped differently.*


	\7. Aplication Layer
	> (Session, Presentation, Application)
	
	\4. Transport Layer
	> (Transportation)		# This Layer!

	\3. Internet Layer
	> (Network)

	\2. Link Layer
	> (Physical, Data Link)

----
<br>



| Task 4 | = IP ADDRESSES AND SUBNETS = |
| - | - |

> Every host on the network needs a unique identifier for other hosts to communicate with him. Without a unique identifier, the host cannot be found without ambiguity. When using the TCP/IP protocol suite, we need to assign an IP address for each device connected to the network.

> So, what makes an IP address? An IP address comprises four octets, i.e., 32 bits. Being 8 bits, an octet allows us to represent a decimal number between 0 and 255.

		[ 192.		 168.	 10.	10 ]
		   ^		  ^		 ^		^
		Octet #1  -  #2  -  #3  -  #4

+ I've seen before more or less how they're structured, and if I'm not mistaken, each octet is 8 bits / 1 byte? So it doesn't go outside the range of 255; one more bit and it resets to zero.

> At the risk of oversimplifying things, the 0 and 255 are reserved for the network and broadcast addresses, respectively. In other words, 192.168.1.0 is the network address, while 192.168.1.255 is the broadcast address. Sending to the broadcast address targets all the hosts on the network.
<br>

\> Looking Up Network Configuration
```
ipconfig [arguments]		(Windows)

	/all			Shows complete network info for all adapters (MAC address, DHCP server, DNS server, etc.)

	/release		Releases the current IPv4 address from a DHCP server.
	/release6		Releases the current IPv6 address from a DHCP server.

	/renew			Requests a new IPv4 address from a DHCP server.
	/renew			Requests a new IPv6 address from a DHCP server.

	/displaydns		Shows the contents of the DNS resolver cache.
	/flushdns		Clears the DNS cache, helpful for fixing outdated DNS entries.
	/registerdns	Refreshes DHCP leases and re-registers DNS names.

	/showclassid	Displays or modifies the DHCP class ID for an adapter.
	/setclassid


ip [arguments]		(Linux)

	-a			Executes the command for all objects (e.g., shows all addresses for all interfaces.).
	-br			Provides a cleaner, more compact output for quick scanning.

	-s			Shows additional statistics (e.g., packet counts, error rates) for more detailed output.
	-d			Displays more detailed information for the specified object.

	-h			Formats statistics for easier readability (e.g., 1.5K instead of 1500.).
	-c			Add color to output for better readability.

	-4			Restricts the information/operation to IPv4.
	-6			Restricts the information/operation to IPv6.

	-f			Specifies the protocol family (inet, inet6, link, etc.).
```
+ *Yes, too much useful information suddenly appears, but we will focus on just a few. (They should look something like this.)*

	\a) inet 				(The host IP address)  
	\b) netmask 			(The subnet mask)  
	\c) broadcast / brd		(The broadcast address)  

> If you are wondering, a subnet mask of 255.255.255.0 can also be written as /24. The /24 means that the leftmost 24 bits within the IP address do not change across the network, i.e., the subnet.

		255.	255.	255.	0
		 ^		 ^		 ^		^
		 8	+	 8	+	 8	+	0	= 24 bits = /24

> In other words, the leftmost three octets are the same across the whole subnet; therefore, we can expect to find addresses that range from 192.168.66.1 to 192.168.66.254. Similar to what was mentioned earlier, 192.168.66.0 and 192.168.66.255 are the network and broadcast addresses, respectively.

		192.168.66.0		Network Address
		192.168.66.255		Broadcast Address
		
		192.168.66.xxx		(We have the last octet for IP addresses)	[.1 ~ .254]
<br>

\> Private Address

>  It is useful to mention that for most practical purposes, there are two types of IP addresses (Public IP / Private IP), and the RFC 1918 defines the following three ranges of private IP addresses:
> 
> 10.0.0.0 ~ 10.255.255.255 (10/8)  
> 172.16.0.0 ~ 172.31.255.255 (172.16/12)  
> 192.168.0.0 ~ 192.168.255.255 (192.168/16)  

+ *Before moving on, I want to explore what each of these CIDR (Classless Inter-Domain Routing) terms means. I think it might be more interesting.*

		10/8 = 0000 1010 | ____ ____ | ____ ____ | ____ ____  
				   ^
				   8		The first 8 bits are fixed.

  		So the remaining 24 bits can be anything [10.0.0.0 ~ 10.255.255.255]


  		172.16/12 = 1010 1100 | 0001 ____ | ____ ____ | ____ ____
  						^			^
						8			4		The first 12 bits are fixed.
  
		So the remaining 20 bits can be anything [172.16.0.0 ~ 172.31.255.255]


		192.168/16 = 1100 0000 | 1010 1000 | ____ ____ | ____ ____
  						 ^			 ^
  						 8			 8		The first 16 bits are fixed.

  		So the remaining 16 bits can be anything [192.168.0.0 ~ 192.168.255.255]
		
> We presented earlier an analogy stating that a public IP address is like your home postal address. A private IP address is different; the original idea is that it cannot reach or be reached from the outside world.

+ *It is like an isolated city or a compound, where all houses and apartments are numbered systematically and can easily exchange mail with each other, but not with the outside world.*

\> Routing

> In technical terms, a router forwards data packets to the proper network. Usually, a data packet passes through multiple routers before it reaches its final destination. The router functions at layer 3, inspecting the IP address and forwarding the packet to the best network (router) so the packet gets closer to its destination.

+ *A router is like your local post office; you hand them the mail parcel, and they would know how to deliver it. If we dig deeper, you might mail something to an address in another city or country. The post office will check the address and decide where to send it next.*


