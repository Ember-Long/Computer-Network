# 💪 Physical Layer & Data Link Layer

Further Key Topics and Concepts

### Host&#x20;

**Host**: sends packets of data **-** **Packetization**

Host sending function:

* Takes application-layer message
* Breaks into smaller chunks, known as **packets**, of length _L_ bits
* Transmits packet into access network at a particular **transmission rate**
* Link transmission rate, aka **link capacity**, aka **link bandwidth**

***

### **Packet-switching**

**Packet-switching**: hosts break application-layer messages into **packets**, forward packets from one router to the next across links on path from source to destination at link capacity

* Resources allocation not needed&#x20;
* Transmission path not predefined

### Alternative to Packet Switching: a Classical Circuit Switching

In circuit swithing: end-end resources allocated to, reserved for “call” between source and destination

<figure><img src=".gitbook/assets/image (2).png" alt="" width="375"><figcaption><p>Circuit Switching</p></figcaption></figure>

* In diagram, each link has four circuits.&#x20;
  * Call gets 2nd circuit in top link and 1st circuit in right link.&#x20;
*   Dedicated resources: no sharing&#x20;

    * Circuit-like guaranteed performance&#x20;

    _<mark style="color:purple;">**However, there are no dedicated resources in pack switching**</mark>_&#x20;
*   Circuit segment **idle** if not used by call (no sharing)&#x20;

    _<mark style="color:purple;">**However, in packet switching, different transmissions can share the same resources**</mark>_&#x20;

_Commonly used in traditional telephone networks_

### Packet-switching: Queueing Delay, Loss

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption><p>Queue Delay</p></figcaption></figure>

**Packet queuing and loss**: if arrival rate (in bitpersecond - bps) to link exceeds transmission rate (bps) of link for a period of time

* Packets will queue, waiting to be transmitted on output link&#x20;
* Packets can be dropped (lost) if memory (buffer) in router fills up

**Packets queue in router buffers:**

* Packets queue, wait for turn&#x20;
* Arrival rate to link (temporarily) exceeds output link capacity: packet loss

<figure><img src=".gitbook/assets/image (4).png" alt="" width="563"><figcaption><p>Packet Loss &#x26; Delay</p></figcaption></figure>

**Transmission Delay** _(sender side)_**; Propagation Delay** _(during the propagation process)_**; Processing Delay** _(receiver side)_

***

### Network Security

#### Field of Network Security:

* How bad guys can attack computer networks
* How we can defend networks against attacks
* How to design architectures that are immune to attacks

#### Internet not Originally Designed with (much) Security in Mind

* Original vision: “a group of mutually trusting users attached to a transparent network” J
* Internet protocol designers playing “catch-up”
* Security considerations in all layers!

***

### Malware

1. **Malware** can get in host from:

* **Virus**: self-replicating infection by receiving/executing object (e.g., e-mail attachment)
* **Worm**: self-replicating infection by passively receiving object that gets itself executed

2. **Spyware** malware can record keystrokes, web sites visited, upload info to collection site
3. Infected host can be enrolled in **botnet**, used for spam or **distributed denial of service (DDoS)** attacks

_**Denial of Service (DoS)**: attackers make resources (server, bandwidth) unavailable to legitimate traffic by overwhelming resource with bogus traffic_

### Packet Interception

#### Packet “Sniffing”:

* Broadcast media (shared Ethernet, wireless)
* Promiscuous network interface reads/records all packets (e.g., including passwords!) passing by

### Fake Identity

#### **IP spoofing**: send packet with false source address

***

## Media

### Types of Connetions

&#x20;A physical connection can be a wired connection using a cable or a wireless connection using radio waves.

The type of physical connection used is dependent upon the setup of the network.

To offer wireless capability, devices on a _wireless_ network must be connected to a _wireless **access point (AP)**_.

**Switch devices** and **wireless access points** are often two separate dedicated devices within a network implementation. However, there are also devices that offer both wired and wireless connectivity.

<figure><img src=".gitbook/assets/image (24).png" alt=""><figcaption><p>Home Router</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (25).png" alt=""><figcaption><p>Connecting to the Wired <a href="overview.md#main">LAN</a></p></figcaption></figure>

### Network Interface Card (NIC)

**Network Interface Cards (NICs) connect a device to the network.**

<mark style="background-color:blue;">Ethernet NICs are used for a wired connection</mark>, whereas <mark style="background-color:blue;">WLAN (Wireless Local Area Network) NICs are used for wireless</mark>.

An end-user device may include one or both types of NICs.

Not all physical connections are equal in terms of performance when connecting to a network. A wireless device will experience degradation in performance when farther from the wireless access point, while a wired connection will not.

***

### The Physical Layer

<figure><img src=".gitbook/assets/image (26).png" alt=""><figcaption><p>OSI Model</p></figcaption></figure>

The _physical layer_ encodes the frames and creates the _electrical, optical, or radio wave_ signals that represent the bits in each frame.

These signals are then sent on the media, one at a time.

The destination node physical layer retrieves these individual signals from the media, restores them to their bit representations, and passes the bits up to the data link layer as a complete frame.

***

### Physical Layer Media

There are three basic forms of network media. The physical layer produces the representation and groupings of bits for each type of media as:

<figure><img src=".gitbook/assets/image (28).png" alt="" width="563"><figcaption><p>Physical Layer Media</p></figcaption></figure>

* **Copper cable**: The signals are patterns of electrical pulses.
* **Fiber-optic cable**: The signals are patterns of light.
* **Wireless**: The signals are patterns of microwave transmissions.

***

### Links: Physical Media

<table><thead><tr><th width="125">Bit</th><th width="137">Physical Link</th><th width="137">Guided Media</th><th>Unguided Media</th></tr></thead><tbody><tr><td>propagates between transmitter/receiver pairs</td><td>what lies between transmitter &#x26; receiver</td><td>signals propagate in solid media: copper, fiber, coax</td><td>signals propagate freely, e.g., radio</td></tr></tbody></table>

<table><thead><tr><th align="center">Twisted Pair (TP)</th><th width="192" align="center">Coaxial Cable</th><th align="center">Fiber Optic Cable</th></tr></thead><tbody><tr><td align="center"></td><td align="center">Two concentric copper conductors</td><td align="center">Glass fiber carrying light pulses, each pulse a bit</td></tr><tr><td align="center"></td><td align="center">Bidirectional</td><td align="center"><p>Low error rate: </p><p>-repeaters spaced far apart </p><p>-immune to electromagnetic noise</p></td></tr><tr><td align="center"><p>Two insulated copper wires </p><p>-Category 5: 100 Mbps, 1 Gbps Ethernet </p><p>-Category 6: 10Gbps Ethernet</p></td><td align="center"><p>Broadband: </p><p>-multiple frequency channels on cable </p><p>-100’s Mbps per channel</p></td><td align="center">high-speed operation: high-speed point-to-point transmission (10’s-100’s Gbps)</td></tr><tr><td align="center"><img src=".gitbook/assets/image (33).png" alt="" data-size="original"><img src=".gitbook/assets/image (34).png" alt=""></td><td align="center"><img src=".gitbook/assets/image (31).png" alt="" data-size="original"></td><td align="center"><img src=".gitbook/assets/image (32).png" alt="" data-size="original"></td></tr></tbody></table>

#### Wireless Radio

1. Signal carried in electromagnetic spectrum
2. No physical “wire”
3. Broadcast and “half-duplex” (sender to receiver)
4. Propagation environment effects:
   1. reflection
   2. obstruction by objects
   3. interference

#### Radio Link Types

1.  Terrestrial  microwave

    Up to 45 Mbps channels
2.  Wireless LAN (WiFi)

    Up to 100’s Mbps


3.  Wide-area (e.g., cellular)

    4G cellular: \~ 10’s Mbps


4. Satellite
   1. Up to 45 Mbps per channel
   2. 270 msec end-end delay
   3. Geosynchronous versus low-earth-orbit

***

### Copper Media and Characteristics

<figure><img src=".gitbook/assets/image (35).png" alt=""><figcaption><p>Copper Media</p></figcaption></figure>

Networks use copper media because it is <mark style="background-color:blue;">inexpensive, easy to install, and has low resistance to electrical current</mark>. However, copper media is limited by _distance_ and _signal interference_.

Data is transmitted on copper cables as electrical pulses. A detector in the network interface of a destination device must receive a signal that can be successfully decoded to match the signal sent. However, **the longer the signal travels, the more it deteriorates**. This is referred to as **signal attenuation**.

The timing and voltage values of the electrical pulses are also susceptible to interference from two sources:

* **Electromagnetic interference (EMI) or radio frequency interference (RFI)** - <mark style="background-color:blue;">EMI and RFI signals can distort and corrupt the data signals being carried by copper media</mark>. _Potential sources of EMI and RFI include radio waves and electromagnetic devices_, such as fluorescent lights or electric motors.
* **Crosstalk** - <mark style="background-color:blue;">Crosstalk is a disturbance caused by the electric or magnetic fields of a signal on one wire to the signal in an adjacent wire</mark>. In telephone circuits, crosstalk can result in hearing part of another voice conversation from an adjacent circuit. Specifically, when an electrical current flows through a wire, it creates a small, circular magnetic field around the wire, which can be picked up by an adjacent wire.

To counter the negative effects of crosstalk, some types of copper cables have _opposing circuit wire pairs twisted together_, which effectively cancels the crosstalk.

#### Unishielded Twisted-Pair Cable

<figure><img src=".gitbook/assets/image (36).png" alt=""><figcaption><p>UTP</p></figcaption></figure>

**Unshielded twisted-pair (UTP) cabling** is the most common networking media.

In LANs, UTP cable consists of <mark style="background-color:blue;">four pairs of color-coded wires</mark> that have been twisted together and then encased in a <mark style="background-color:blue;">flexible plastic sheath that protects from minor physical damage</mark>

UTP cable _does not use shielding to counter the effects of EMI and RFI_. Instead, cable designers have discovered that they can limit the negative effect of crosstalk by:

**Cancellation**: Designers now pair wires in a circuit. <mark style="background-color:blue;">When two wires in an electrical circuit are placed close together, their magnetic fields are the exact opposite of each other</mark>. Therefore, <mark style="background-color:blue;">the two magnetic fields cancel each other and also cancel out any outside EMI and RFI signals</mark>.

UTP cable relies solely on the cancellation effect produced by the twisted wire pairs to limit signal degradation and effectively provide self-shielding for wire pairs within the network media.

#### Shielded Twisted-Pair Cable

<figure><img src=".gitbook/assets/image (37).png" alt=""><figcaption><p>STP</p></figcaption></figure>

**Shielded twisted-pair (STP)** provides <mark style="background-color:blue;">better noise protection than UTP cabling</mark>. However, compared to UTP cable, STP cable is _significantly more expensive and difficult to install_. STP cables[ <mark style="background-color:blue;">combine the techniques of shielding to counter EMI and RFI, and wire twisting to counter crosstalk</mark>](#user-content-fn-1)[^1].

#### Coaxial Cable

<figure><img src=".gitbook/assets/image (38).png" alt=""><figcaption><p>Coaxial Cable</p></figcaption></figure>

**Coaxial cable, or coax** for short, gets its name from the fact that there are _two conductors that share the same axis_. As shown in the figure, coaxial cable consists of:

* A **copper conductor** used to transmit the electronic signals.
* A layer of flexible **plastic insulation** surrounding a copper conductor.
* The insulating material is surrounded in a **woven copper braid**, or <mark style="background-color:green;">**metallic foil**</mark><mark style="background-color:green;">, that acts as</mark> _<mark style="background-color:green;">the second wire in the circuit</mark>_ <mark style="background-color:green;">and as</mark> <mark style="background-color:green;"></mark>_<mark style="background-color:green;">a shield for the inner conductor</mark>_. <mark style="background-color:blue;">This second layer, or shield, also reduces the amount of outside electromagnetic interference</mark>.

The entire cable is covered with a cable jacket to prevent minor physical damage.

Although _UTP cable has essentially replaced coaxial cable in modern Ethernet installations_, the coaxial cable design is used in:

* **Wireless installations**: Coaxial cables <mark style="background-color:blue;">attach antennas to wireless devices</mark>. The coaxial cable carries radio frequency (RF) energy between the antennas and the radio equipment.
* **Cable Internet installations**: Cable service providers provide Internet connectivity to their customers by replacing portions of the coaxial cable and supporting amplification elements with fiber-optic cable. However, the wiring inside the customer's premises is still coax cable.

_These cables are used to interconnect nodes on a LAN and infrastructure devices such as switches, routers, and wireless access points. Each type of connection and the accompanying devices has cabling requirements stipulated by physical layer standards._

***

### Fiber Versus Copper

<figure><img src=".gitbook/assets/image (39).png" alt=""><figcaption><p>Fiaber VS Copper</p></figcaption></figure>

**Optical fiber cable** <mark style="background-color:blue;">transmits data over longer distances and at higher bandwidths than any other networking media</mark>. Unlike copper wires, fiber-optic cable can <mark style="background-color:blue;">transmit signals with less attenuation and is completely immune to EMI and RFI</mark>. Optical fiber is <mark style="background-color:blue;">commonly used to interconnect network devices</mark>.

Optical fiber is a _flexible, but extremely thin, transparent strand of very pure glass, not much bigger than a human hair_. <mark style="background-color:blue;">Bits are encoded on the fiber as light impulses</mark>. The fiber-optic cable acts as a waveguide, or “light pipe,” to transmit light between the two ends with minimal loss of signal.

There are many advantages to using fiber-optic cable compared to copper cables: the media is immune to electromagnetic interference and will not conduct unwanted electrical currents due to grounding issues. Optical fibers are thin and have a relatively low signal loss and can be operated at much greater lengths than copper media. Some optical fiber physical layer specifications allow lengths that can reach multiple kilometers.

***

### Bandwidth

<figure><img src=".gitbook/assets/image (41).png" alt=""><figcaption><p>Bandwidth</p></figcaption></figure>

Different physical media support the transfer of bits at different rates. Data transfer is usually discussed in terms of **bandwidth** and **throughput**.

**Bandwidth is the capacity of a medium to carry data**. <mark style="background-color:blue;">Digital bandwidth measures the amount of data that can flow from one place to another in a given amount of time</mark>. Bandwidth is typically measured in kilobits per second (kb/s), megabits per second (Mb/s), or gigabits per second (Gb/s).

A combination of factors determines the practical bandwidth of a network:

* The properties of the physical media
* The technologies chosen for signaling and detecting network signals

**Throughput is the measure of the transfer of bits across the media over a given period of time.**

<mark style="background-color:red;">Throughput does not match the specified bandwidth in physical layer implementations</mark>. Many factors influence throughput, including:

* The amount of traffic
* The type of traffic
* The latency created by the number of network devices encountered between source and destination

<mark style="background-color:blue;">Throughput cannot be faster than the slowest link in the path from source to destination</mark>.

***

### The Data Link Layer

<figure><img src=".gitbook/assets/image (42).png" alt=""><figcaption><p>Data Link Layer</p></figcaption></figure>

The data link layer of the OSI model (Layer 2) is responsible for:

* Allowing the upper layers to access the media
* Accepting Layer 3 packets and packaging them into frames
* Preparing network data for the physical network
* Controlling how data is placed and received on the media
* Exchanging frames between nodes over a physical network media, such as UTP or fiber-optic
* Receiving and directing packets to an upper layer protocol
* Performing error detection

The Layer 2 notation for network devices connected to a common media is called a **node**. <mark style="background-color:blue;">Nodes build and forward frames.</mark>

The data link layer effectively separates the media transitions that occur as the packet is forwarded from the communication processes of the higher layers. <mark style="background-color:blue;">The data link layer receives packets from and directs packets to an upper layer protocol, in this case IPv4 or IPv6.</mark> This upper layer protocol does not need to be aware of which media the communication will use.

***

### Data Link Sublayers

<figure><img src=".gitbook/assets/image (43).png" alt=""><figcaption><p>Data Link Sublayers</p></figcaption></figure>

The data link layer is divided into two sublayers:

* **Logical Link Control (LLC)** - This upper sublayer <mark style="background-color:blue;">communicates with the network layer</mark>. It <mark style="background-color:blue;">places information in the frame that identifies which network layer protocol is being used for the frame</mark>. This information allows multiple Layer 3 protocols, such as IPv4 and IPv6, to utilize the same network interface and media.
* **Media Access Control (MAC)** - This lower sublayer <mark style="background-color:blue;">defines the media access processes performed by the hardware</mark>. It <mark style="background-color:blue;">provides data link layer addressing and access to various network technologies</mark>. For instance, the MAC sublayer communicates with Ethernet LAN technology to send and receive frames over copper or fiber-optic cable. The MAC sublayer also communicates with wireless technologies such as Wi-Fi and Bluetooth to send and receive frames wirelessly.

***

### Media Access Control

<figure><img src=".gitbook/assets/image (44).png" alt=""><figcaption><p>Meida Access Control</p></figcaption></figure>

Layer 2 protocols specify the encapsulation of a packet into a frame and the techniques for getting the encapsulated packet on and off each medium.

The technique used for getting the frame on and off the media is called the **media access control method**.

As packets travel from the source host to the destination host, they typically traverse over different physical networks. These physical networks can consist of different types of physical media such as copper wires, optical fibers, and wireless consisting of electromagnetic signals, radio and microwave frequencies, and satellite links.

Without the data link layer, network layer protocols such as IP, would have to make provisions for connecting to every type of media that could exist along a delivery path. Moreover, IP would have to adapt every time a new network technology or medium was developed. This process would hamper protocol and network media innovation and development. This is a key reason for using a layered approach to networking.

Different media access control methods may be required during a single communication. Each network environment that packets encounter as they travel from a local host to a remote host can have different characteristics. For example, an Ethernet LAN consists of many hosts contending to access the network medium. Serial links consist of a direct connection between only two devices.

Router interfaces encapsulate the packet into the appropriate frame, and a suitable media access control method is used to access each link. In any given exchange of network layer packets, there may be numerous data link layers and media transitions.

At each hop along the path, a **router**:

* Accepts a frame from a medium
* De-encapsulates the frame
* Re-encapsulates the packet into a new frame
* Forwards the new frame appropriate to the medium of that segment of the physical network

***

### The Frame

<figure><img src=".gitbook/assets/image (45).png" alt=""><figcaption><p>Frame</p></figcaption></figure>

<mark style="background-color:blue;">The data link layer prepares a packet for transport across the local media by encapsulating it with a header and a trailer to create a frame.</mark> The description of a frame is a key element of each data link layer protocol. Although there are many different data link layer protocols that describe data link layer frames, each frame type has three basic parts:

* Header
* Data
* Trailer

All data link layer protocols encapsulate the Layer 3 [PDU](overview.md#protocol-data-units) within the data field of the frame. However, <mark style="background-color:blue;">the structure of the frame and the fields contained in the header and trailer vary according to the protocol</mark>.

<mark style="background-color:blue;">Framing breaks the stream into decipherable groupings, with control information inserted in the header and trailer as values in different fields</mark>. <mark style="background-color:blue;">This format gives the physical signals a structure that can be received by nodes and decoded into packets at the destination.</mark>

Generic frame field types include:

* **Frame start and stop indicator flags** - Used to identify the beginning and end limits of the frame.
* **Addressing** - Indicates the source and destination nodes on the media.
* **Type** - Identifies the Layer 3 protocol in the data field.
* **Control** - Identifies special flow control services such as quality of service (QoS)
* **Data** - Contains the frame payload (i.e., packet header, segment header, and the data).
* **Error Detection** - These frame fields are used for error detection and are included after the data to form the trailer.

_Not all protocols include all of these fields. The standards for a specific data link protocol define the actual frame format._

<mark style="background-color:blue;">Data link layer protocols add a trailer to the end of each frame. The trailer is used to determine if the frame arrived without error</mark>. This process is called **error detection** and is accomplished by placing a logical or mathematical summary of the bits that comprise the frame in the trailer.

***

### Layer 2 Address

<figure><img src=".gitbook/assets/image (46).png" alt=""><figcaption><p>Layer 2 Address</p></figcaption></figure>

<mark style="background-color:blue;">The data link layer provides physical addressing that is used in transporting a frame across a shared local media.</mark>

<mark style="background-color:blue;">Data link layer addressing is contained within the frame header and specifies the frame destination node on the local network.</mark> _The frame header may also contain the source address of the frame._

Unlike Layer 3 logical addresses, which are hierarchical, physical addresses do not indicate on what network the device is located. Rather, <mark style="background-color:blue;">the physical address is unique to the specific device.</mark>

In the example: as the IP packet travels from host-to-router, router-to-router, and finally router-to-host, at each point along the way the IP packet is encapsulated in a new data link frame. Each data link frame contains the source data link address of the NIC card sending the frame, and the destination data link address of the NIC card receiving the frame.

[^1]: why UTP cannot counter the crosstalk through twisting?
