
| Task 1 | = Introduction = |
| - | - |

> Have you ever wondered why you need an IP adress to access the Internet?

+ (idk) To be honest, when they tried to explain it in 'Pre-security' it was just long walls of text… 

----
<br>



| Task 2 | = OSI Model = |
| - | - |

> Before we start, we should note that the OSI model might initially seem complicated... Don't worry... by the time you finish this module, this task will feel like a piece of cake.

+ Am I really that stupid for not understanding this? I feel like I have to pray to God so I don't have to write it on the walls… 
<br>

\> Layer 1: Physical Layer

+ To put it simply, it's anything you can touch... it's not limited to just a cables like Ethernet. Is it an antenna? Is it infrared port? Is it an object that transmits signals? Make sure to rub it gently with your fingers so as not to scare away the electromagnetic radiation. 

+ Better yet, I will focus on using a hypothetical city, where the physical aspect is how everything connects: roads, vehicles, airports, antennas, drones, trains, a postal service, everything that entails.


\> Layer 2: Data Link Layer

> This layer involves the recognition of the transmission media, where different systems reach an agreement on how to connect. I suppose the list the devices, their capabilities, brand and specifications, and which ones are available to both the deliver and receptor.

+ In this layer, let's think of the media as a vehicle, which is driven by a driver. This layer not only recognizes all the different media by their types (MAC address as license plates + specs) but it ensures that the vehicle (data frame) does not collide with other packets and ensures that it arrives intact (or will it report otherwise?).

+ That's why you can do MAC Spoofing, you put the license plates of another vehicle on yours... but is that the only way to break this layer?.


\> Layer 3: Network Layer

> The main function of this layer is to send data, finding a path to transfer packets between different networks. Some examples, Internet Control Message Protocol (ICMP), Virtual Private Network (VPN). 

+ In this situation, while the previous layer is responsible for a general recognition of the devices, in this one the driver has the IP address of the other city, Using this information, plan the best route by consulting routing tables (DNS?) through the various networks...


\> Layer 4: Transport Layer

> Once the route has been established, this layer is responsible for creating end-to-end communication with functions such as flow control, error correction, segmentation...

+ From a general perspective, this is where the decision regarding shipping quality comes in. Is speed or reliability more important? Are we interested in verifying the integrity of the shipment, or do we just want to send it?


\> Layer 5: Session Layer

> Once communication is established, this layer is responsible for monitoring, synchronizing, and maintaining the connection, taking into account the session parameters. It ensures in-order transfers and recovery methods...

+ Let's imagine we have a reception center, where once the data is received it verifies the information, establishes the exchange, discerns the type of information received and ends the sessions.


\> Layer 6: Presentation Layer

> The presentation layer ensures the data is delivered in a form the application layer can understand, handles the data encoding, compression and encryption.

+ Let's say the package is already in the city, but how can we deliver it? In this layer, we group by use, rewrite the lithograph to understand it, and encrypt it so that only the people involved can see its contents.


\> Layer 7: Application Layer

> As the final layer, you are presented with an interface (applications) that takes all these packets and makes them available to the user. Different protocols require different applications.

+ Well, have you used Chrome? Maybe YouTube? Even Gmail? (Glorious Monopoly x_x) All these interfaces make it easier to perform tasks quickly instead of reading all these raw packets, and they also make it easier to classify them.

----
<br>



| Task 3 | = TCP/IP MODEL = |
| - | - |

> One of the strengths of this model is that it allows a network to continue to function as parts of it are out of service, for instance, due to a military attack. This capability is possible in part due to the design of the routing protocols to adapt as the network topology changes.

+ As a point of interest, this type of connection offers us the strength of information integrity and the ability to be redundant in case of failure, thanks to its adaptability...? Due to its function, it is grouped differently.


4. Aplication Layer
> (Session, Presentation, Application)
	
3. Transport Layer
> (Transportation)		# This Layer!

2. Internet Layer
> (Network)

1. Link Layer
> (Phisical, Data Link)

----
<br>



| Task 4 | = IP ADDRESSES AND SUBNETS = |
| - | - |

