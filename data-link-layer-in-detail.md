# 📡 Data Link Layer (In Detail)

Link Layer: Introduction

Terminology:

* Hosts and routers: **Nodes**
* Communication channels that connect adjacent nodes along communication path: **Links**
  * wired
  * wireless
  * LANs
* layer-2 packet: **frame**, encapsulates datagram
  * The word **datagram** is used to mean <mark style="background-color:blue;">a unit of data carrying sufficient information (in a header usually) for routing from the source to the destination nodes without reliance on earlier exchanges between the two parties</mark>.

{% hint style="info" %}
Link layer has responsibility of transferring datagram from one node to physically adjacent node over a link
{% endhint %}

***

## Link Layer: Services

### Framing, link access:

* Encapsulate datagram into frame, adding header, trailer
* Channel access if shared medium
* “MAC” addresses in frame headers identify source, destination (different from IP address!)

### Reliable delivery between adjacent nodes

#### Flow control:

* Pacing between adjacent sending and receiving nodes

#### Error detection:

* Errors caused by signal attenuation, noise.
* Receiver detects errors, signals retransmission, or drops frame

#### Error correction:

* Receiver identifies and corrects bit error(s) without retransmission

***

## Where Is the Link Layer Implemented?

<figure><img src=".gitbook/assets/image.png" alt="" width="296"><figcaption><p>Link Layer Implementation</p></figcaption></figure>

* In each-and-every <mark style="background-color:blue;">host</mark>
* Link layer implemented in <mark style="background-color:blue;">network interface card (NIC) or on a chip</mark>
  * Ethernet, WiFi card or chip
  * Implements link, physical layer
* Attaches into host’s system buses
* Combination of hardware, software, firmware

***

## Interfaces Communication

<figure><img src=".gitbook/assets/image (1).png" alt=""><figcaption><p>Interfaces Communication</p></figcaption></figure>

### Sending Side

* Encapsulates datagram in frame
* Adds error checking bits, reliable data transfer, flow control, etc.

### Receiving Side

* Looks for errors, reliable data transfer, flow control, etc.
* Extracts datagram, passes to upper layer at receiving side

***

## MAC Protocols: Taxonomy

### Two Types of "Links"

* **Point-to-point**: Example: point-to-point link between Ethernet switch, host
* **Broadcast** (shared wire or medium): Example: “old-fashioned” Ethernet, 802.11 wireless LAN, 4G/4G. Satellite. <mark style="background-color:blue;">Collisions can occur</mark>

### Three Broad Classes of Protocols to Deal with Collisions and Manage Access (MAC Protocols)

#### Channel Partitioning

* Divide channel into smaller “pieces” (time slots, frequency, code)
* Allocate piece to node for exclusive use

#### Random Access

* Channel not divided, allow collisions
* “Recover” from collisions

#### “Taking Turns”

* Nodes take turns, but nodes with more to send can take longer turns

***

## Random Access Protocols

### When node has packet to send

* Transmit at full channel data rate R.
* No a priori coordination among nodes

### Two or more transmitting nodes: “collision”

### _Random access MAC protocol_ specifies:

* How to detect collisions
* How to recover from collisions (e.g., via delayed retransmissions)

### Examples of random access MAC protocols:

* ALOHA, slotted ALOHA
* CSMA, CSMA/CD, CSMA/CA

***

## CSMA (Carrier Sense Multiple Access)

### Simple CSMA: Listen Before Transmit:

* If **channel sensed idle**: transmit entire frame
* If **channel sensed busy**: defer transmission

_Human analogy: don’t interrupt others!_

### CSMA/CD: CSMA with Collision Detection

* Collisions detected within short time
* Colliding transmissions aborted, reducing channel wastage
* Collision detection <mark style="background-color:blue;">easy in wired, difficult with wireless</mark>

_Human analogy: the polite conversationalist_

***

## Ethernet CSMA/CD Algorithm

1. NIC receives datagram from network layer, creates frame
2. If NIC senses channel:
   1. If **idle**: start frame transmission.
   2. If **busy**: wait until channel idle, then transmit
3. <mark style="background-color:blue;">If NIC transmits entire frame without collision, NIC is done with frame</mark> !
4. If NIC detects <mark style="background-color:blue;">another transmission while sending</mark>: <mark style="background-color:blue;">abort, send jam signal</mark>
5. After aborting, NIC enters **backoff**:
   1. NIC waits and then returns to Step 2
   2. More collisions: longer backoff interval

***

## Mac Address

<figure><img src=".gitbook/assets/image (3).png" alt=""><figcaption><p>MAC Address &#x26; IP Address</p></figcaption></figure>

<mark style="background-color:blue;">Each interface on LAN: has unique 48-bit MAC address (and also has a locally unique 32-bit IP address )</mark>

MAC (or LAN or physical or Ethernet) address:

* Function: used “locally” to get frame from one interface to another physically-connected interface (same subnet, in IP-addressing sense)
* 48-bit MAC address (for most LANs) burned in NIC ROM, also sometimes software settable

MAC address allocation administered by IEEE

Manufacturer buys portion of MAC address space (to assure uniqueness)

Analogy:

* MAC address: like Social Security Number
* IP address: like postal address

&#x20;**MAC flat address**: portability

* Can move interface from one LAN to another
* Recall IP address not portable: depends on IP subnet to which node is attached

***

## Ethernet Switch

Switch is a <mark style="background-color:blue;">link-layer device</mark>: takes an _active_ role

* Store, forward Ethernet frames
* Examine incoming frame’s MAC address, selectively forward  frame to one-or-more outgoing links when frame is to be forwarded on segment, uses CSMA/CD to access segment

**Transparent**: hosts unaware of presence of switches

***

## Ethernet Encapsulation

<figure><img src=".gitbook/assets/image (4).png" alt="" width="563"><figcaption><p>Ethernet Encapsulation</p></figcaption></figure>

### Ethernet

* Most widely used LAN technology&#x20;
* Operates in the <mark style="background-color:blue;">data link layer and the physical layer</mark>&#x20;
* Family of networking technologies that are defined in the IEEE 802.2 and 802.3 standards&#x20;
* Supports data bandwidths of 10, 100, 1000, 10,000, 40,000, and 100,000 Mbps (100 Gbps)

### Ethernet Standards

* Define Layer 2 protocols and Layer 1 technologies&#x20;
* Two separate sub layers of the data link layer to operate - Logical link control (LLC) and the MAC sublayers

<figure><img src=".gitbook/assets/image (5).png" alt=""><figcaption><p>The Illustration of Ehternet Encapsulation</p></figcaption></figure>

***

## MAC Sublayer

<figure><img src=".gitbook/assets/image (6).png" alt=""><figcaption><p>MAC Sublayer</p></figcaption></figure>

Primary responsibilities:

* Data encapsulation
* Media access control

***

## Ethernet Evolution

<figure><img src=".gitbook/assets/image (7).png" alt=""><figcaption><p>Ethernet II Frame Structure and Field Size</p></figcaption></figure>

***

## Frame Processing

<figure><img src=".gitbook/assets/image (8).png" alt=""><figcaption><p>Frame Forwarding</p></figcaption></figure>

* <mark style="background-color:blue;">The NIC views information to see if the destination MAC address in the frame matches the device’s physical MAC address stored in RAM.</mark>&#x20;
* If there is **no match**, the device **discards the frame**.
* If there is a **match**, the NIC **passes the frame up the OSI layers**, where the de-encapsulation process takes place.

***

## Unicast MAC Address

<figure><img src=".gitbook/assets/image (9).png" alt=""><figcaption><p>Unicast MAC Address</p></figcaption></figure>

## Broadcast MAC Address

<figure><img src=".gitbook/assets/image (10).png" alt=""><figcaption><p>Broadcast MAC Address</p></figcaption></figure>

## Multicast MAC Address

<figure><img src=".gitbook/assets/image (11).png" alt=""><figcaption><p>Multicast MAC Address</p></figcaption></figure>

***

## Learning MAC Address

<figure><img src=".gitbook/assets/image (12).png" alt=""><figcaption><p>Source MAC Address</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (13).png" alt=""><figcaption><p>Destination MAC Address</p></figcaption></figure>

## Filtering Frames

<figure><img src=".gitbook/assets/image (14).png" alt=""><figcaption><p>Add PC-D to the MAC Table</p></figcaption></figure>

PC-D sends a frame back to PC-A and the switch learns PC-D’s MAC address.&#x20;

<figure><img src=".gitbook/assets/image (16).png" alt=""><figcaption><p>Transmission from PC-D to PC-A</p></figcaption></figure>

Since the Switch MAC Address table contains PC-A’s MAC Address, it sends the frame out only port 1.

<figure><img src=".gitbook/assets/image (17).png" alt=""><figcaption><p>Transmission from PC-A to PC-D</p></figcaption></figure>

PC-A sends another frame to PC-D. The switch’s table now contains PC-D’s MAC address, so it sends the frame out only port 4.

***

## Frame Forwarding Methods on Cisco Switches

<figure><img src=".gitbook/assets/image (19).png" alt=""><figcaption><p>Frame Forwarding Methods on Cisco Switches</p></figcaption></figure>

***

## Destination on the Same Network

<figure><img src=".gitbook/assets/image (20).png" alt=""><figcaption><p>Communicating on a Local Network</p></figcaption></figure>

There are two primary addresses assigned to a device on an Ethernet LAN:

* **Physical address (the MAC address)** – Used for Ethernet NIC to Ethernet NIC communications on the same network.
* **Logical address (the IP address)** – Used to send the packet from the original source to the final destination.

## Destination on a Remote Network

<figure><img src=".gitbook/assets/image (23).png" alt=""><figcaption><p>Communicating to a Remote Network</p></figcaption></figure>

***

## Introduction to ARP

<figure><img src=".gitbook/assets/image (24).png" alt=""><figcaption><p>ARP</p></figcaption></figure>

### ARP Functions

ARP Table

* Used to <mark style="background-color:blue;">find the MAC address that is mapped to the destination IPv4 address</mark>.
* If the destination IPv4 address is on the **same network** as the source IPv4, the device will **search the ARP table for the destination IPv4 address**.
* If the destination IPv4 address is on a **different network**, the device will **search for the IPv4 address of the default gateway**.
* If the device **locates the IPv4 address**, its **corresponding MAC address is used as the destination MAC address in the frame**.
* If **no entry is found**, then an **ARP request is sent**.

### ARP Request

* Sent when <mark style="background-color:blue;">a device needs a MAC address associated with an IPv4 address, and it does not have an entry in its ARP table</mark>.&#x20;
* The ARP request message includes:&#x20;
  * **Target IPv4 address** – This is the IPv4 address that requires a corresponding MAC address.&#x20;
  * **Target MAC address** – This is the unknown MAC address and will be <mark style="background-color:blue;">empty</mark> in the ARP request message.&#x20;
* The ARP request is <mark style="background-color:blue;">encapsulated in an Ethernet frame</mark> using the following header information:&#x20;
  * **Destination MAC address** – This is a <mark style="background-color:blue;">broadcast address</mark> requiring all Ethernet NICs on the LAN to accept and process the ARP request.&#x20;
  * **Source MAC address** – This is the sender’s MAC address.&#x20;
  * **Type**  – ARP messages have a type field of 0x806.
