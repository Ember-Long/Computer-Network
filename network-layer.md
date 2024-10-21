# 📬 Network Layer

## The Network Layer

<figure><img src=".gitbook/assets/image (73).png" alt=""><figcaption><p>The Exchange of Data</p></figcaption></figure>

The **network layer**, or **OSI Layer 3**, provides services to allow **end devices to exchange data across the network**.

To accomplish this, the network layer uses four basic processes **(end-to-end)**:

* **Addressing end devices** - End devices must be configured with a <mark style="background-color:blue;">unique IP address</mark> for identification on the network.
* **Encapsulation** - The network layer encapsulates the protocol data unit (PDU) <mark style="background-color:blue;">from the transport layer into a packet</mark>. The encapsulation process <mark style="background-color:blue;">adds IP header information</mark>, such as the IP address of the source (sending) and destination (receiving) hosts.
* **Routing** - The network layer <mark style="background-color:blue;">provides services to direct packets to a destination host on another network</mark>. To travel to other networks, the <mark style="background-color:blue;">packet must be processed by a router</mark>. <mark style="background-color:orange;">The role of the route</mark>r is to <mark style="background-color:orange;">select the best path and direct packets toward the destination host in a process known as routing</mark>. A packet may cross many intermediary devices before reaching the destination host. <mark style="background-color:blue;">Each router a packet crosses to reach the destination host</mark> is called a **hop**.
* **De-encapsulation** - When the packet _arrives at the network layer of the destination host_, the host _checks the IP header of the packet_. If the <mark style="background-color:blue;">destination IP address within the header matches its own IP address</mark>, <mark style="background-color:blue;">the IP header is removed from the packet; and the resulting Layer 4 PDU is passed up to the appropriate service at the transport layer.</mark>

***

## A Router is a Computer/Router CPU and OS

Routers require:

* Central processing units (CPUs)
* Operating systems (OSs)

Memory consisting of:

* Random-access memory (RAM)
* Read-only memory (ROM)
* Nonvolatile random-access memory (NVRAM)
* Flash

***

## Two Key Network-Layer Functions

### Network-Layer Functions

* **Forwarding**: move packets from a router’s input link to appropriate router output link
* **Routing**: determine route taken by packets from source to destination routing algorithms

### Analogy: Taking a Trip

<figure><img src=".gitbook/assets/image (76).png" alt="" width="176"><figcaption><p>Forwarding</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (77).png" alt="" width="234"><figcaption><p>Routing</p></figcaption></figure>

* **Forwarding**: process of getting through single interchange
* **Routing**: process of planning trip from source to destination

***

## Encapsulating IP

<figure><img src=".gitbook/assets/image (78).png" alt=""><figcaption><p>Encapsulating IP</p></figcaption></figure>

IP encapsulates the transport layer segment by <mark style="background-color:blue;">adding an IP header</mark>. This header is used to <mark style="background-color:blue;">deliver the packet to the destination host</mark>. **The IP header remains the same from the time the packet leaves the source host until it arrives at the destination host**.

<mark style="background-color:blue;">The process of encapsulating data layer by layer enables the services at the different layers to develop and scale without affecting the other layers</mark>.

This means the transport layer segments can be readily packaged by IPv4 or IPv6 or by any new protocol that might be developed in the future.

## Charateristics of IP

<figure><img src=".gitbook/assets/image (79).png" alt=""><figcaption><p>Characteristics of IP</p></figcaption></figure>

IP provides only the functions that are necessary to deliver a packet from a source to a destination over an interconnected system of networks: this is important to be a protocol with a <mark style="background-color:blue;">low</mark> <mark style="background-color:blue;"></mark><mark style="background-color:blue;">**overhead**</mark>.

The protocol was not designed to track and manage the flow of packets: these functions, if required, are performed by other protocols at other layers, primarily TCP at Layer 4

***

## IP-Connectionless

<figure><img src=".gitbook/assets/image (80).png" alt=""><figcaption><p>IP-Connectionless</p></figcaption></figure>

IP is connectionless, meaning that <mark style="background-color:blue;">no dedicated end-to-end connection is created before data is sent</mark>.

<figure><img src=".gitbook/assets/image (81).png" alt=""><figcaption><p>Analogy of IP-Connectionless</p></figcaption></figure>

Connectionless communication is conceptually similar to _sending a letter to someone without notifying the recipient in advance_.

Connectionless data communications work on the same principle.  IP requires no initial exchange of control information to establish an end-to-end connection before packets are forwarded. <mark style="background-color:blue;">IP also does not require additional fields in the header to maintain an established connection</mark>. This process **greatly reduces the overhead of IP.**

However, with no pre-established end-to-end connection, <mark style="background-color:blue;">senders are unaware whether destination devices are present and functional when sending packets, nor are they aware if the destination receives the packet, or if they are able to access and read the packet</mark>.

## IP-Best Effort Delivery

<figure><img src=".gitbook/assets/image (82).png" alt=""><figcaption><p>IP-Best Effort Delivery</p></figcaption></figure>

**The IP protocol does not guarantee that all packets that are delivered are, in fact, received.**

**Unreliable** means that <mark style="background-color:blue;">IP does not have the capability to manage and recover from undelivered or corrupt packets</mark>. This is because while IP packets are sent with information about the location of delivery, <mark style="background-color:blue;">they contain no information that can be processed to inform the sender whether delivery was successful</mark>. Packets may arrive at the destination corrupted, out of sequence, or not at all. IP provides no capability for packet retransmissions if errors occur.

If out-of-order packets are delivered, or packets are missing, then <mark style="background-color:blue;">applications using the data, or upper layer services, must resolve these issues</mark>. This allows IP to function very efficiently. In the TCP/IP protocol suite, <mark style="background-color:orange;">**reliability**</mark>** is the role of the **<mark style="background-color:orange;">**transport layer**</mark>.

## Reflections on Best-Effort Service

* **Simplicity of mechanism** has allowed Internet to be widely <mark style="background-color:blue;">deployed adopted</mark>&#x20;
* **Sufficient provisioning of bandwidth** allows <mark style="background-color:blue;">performance of real-time applications</mark> (e.g., interactive voice, video) to be “good enough” for “most of the time”&#x20;
* **Replicated, application-layer distributed services** (datacenters, content distribution networks) connecting <mark style="background-color:blue;">close to clients</mark>’ networks, <mark style="background-color:blue;">allow services to be provided from multiple locations</mark>&#x20;
* Congestion control of “elastic” services helps

***

## IP-Media Independent

<figure><img src=".gitbook/assets/image (83).png" alt=""><figcaption><p>IP-Media Independent</p></figcaption></figure>

**IP operates independently of the media that carry the data at lower layers of the protocol stack.**

IP packets can be communicated as electronic signals over copper cable, as optical signals over fiber, or wirelessly as radio signals.

It is the responsibility of the OSI <mark style="background-color:blue;">data link layer</mark> to <mark style="background-color:blue;">take an IP packet and prepare it for transmission over the communications medium</mark>. This means that **sending IP packets is not limited to any particular medium**.

There is, however, one major characteristic of the media that the network layer considers: **the maximum size of the PDU that each medium can transport**. This characteristic is referred to as the **maximum transmission unit (MTU)**. The data link layer passes the MTU value up to the network layer. The network layer then determines how large packets can be.

In some cases, an intermediate device, usually a router, must <mark style="background-color:blue;">split up a packet</mark> when <mark style="background-color:blue;">forwarding it from one medium to another medium with a smaller MTU</mark>. This process is called **fragmenting the packet** or **fragmentation**.

***

## Network Layer: Data Plane, Control Plane

### Data Plane

* **Local**, per-router function&#x20;
* Determines how <mark style="background-color:blue;">datagram arriving on router input port is forwarded to router output port</mark>

<figure><img src=".gitbook/assets/image (91).png" alt=""><figcaption><p>Data Plane</p></figcaption></figure>

### Control Plane

* **Network-wide** logic&#x20;
* Determines how <mark style="background-color:blue;">datagram is routed among routers along end-end path from source host to destination host</mark>
*   Two control-plane approaches:&#x20;

    * **Traditional routing algorithms**: implemented in <mark style="background-color:blue;">routers</mark>&#x20;
    * **Software-defined networking (SDN)**: implemented in <mark style="background-color:blue;">(remote) servers</mark>



***

### Per-Router Control Plane

<figure><img src=".gitbook/assets/image (92).png" alt=""><figcaption><p>Per-Router Control Plane</p></figcaption></figure>

**Individual routing algorithm** components _in each and every router_ interact in the control plane

### Software-Defined Networking (SDN) Control Plane

<figure><img src=".gitbook/assets/image (93).png" alt=""><figcaption><p>SDN Control Plane</p></figcaption></figure>

**Remote controller** <mark style="background-color:blue;">computes, installs forwarding tables in routers</mark>

## IPv4 Packet Header

<figure><img src=".gitbook/assets/image (94).png" alt=""><figcaption><p>IPv4 Packet Header</p></figcaption></figure>

An IPv4 packet header consists of fields containing important information about the packet. These fields contain <mark style="background-color:blue;">binary numbers</mark> which are <mark style="background-color:blue;">examined by the Layer 3 process</mark>. The binary values of each field identify various settings of the IP packet.

The IP protocol header diagram in the figure identifies the fields of an IPv4 packet.

Significant fields in the IPv4 header include:

* **Version** - Contains a <mark style="background-color:blue;">4-bit</mark> binary value set to 0100 that identifies this as an IP version 4 packet.
* **Differentiated Services or DiffServ (DS)** - Formerly called the **Type of Service (ToS)** field, the DS field is an <mark style="background-color:blue;">8-bit</mark> field used to determine the <mark style="background-color:blue;">priority of each packet</mark>.
* **Time-to-Live (TTL)** - Contains an <mark style="background-color:blue;">8-bit</mark> binary value that is used to <mark style="background-color:blue;">limit the lifetime of a packet</mark>. _The packet sender sets the initial TTL value, and it is decreased by one each time the packet is processed by a router. If the TTL field decrements to zero, the router discards the packet and sends an Internet Control Message Protocol (ICMP) Time Exceeded message to the source IP address._
* **Protocol** - Field is used to <mark style="background-color:blue;">identify the next level protocol</mark>. Common values include TCP (6), and UDP (17).
* **Source IPv4 Address** - Contains a <mark style="background-color:blue;">32-bit</mark> binary value that represents the source IPv4 address of the packet. _The source IPv4 address is always a unicast address_.
* **Destination IPv4 Address** - Contains a <mark style="background-color:blue;">32-bit</mark> binary value that represents the destination IPv4 address of the packet. _The destination IPv4 address is a unicast, multicast, or broadcast address_.

The two most commonly referenced fields are the source and destination IP addresses. These fields identify where the packet is coming from and where it is going. Typically these addresses **do not change** while travelling from the source to the destination.

***

## Subnets

What’s a subnet ?

* Device interfaces that can physically reach each other without passing through an intervening router

**IP addresses contain 32 bits** and have a particular structure:&#x20;

* **Subnet portion/part**: devices in same subnet have common high order bits&#x20;
* **Host portion/part**: remaining low order bits

***

## IPv4 Addresses, Network and Host Portions /Parts

<figure><img src=".gitbook/assets/image (95).png" alt=""><figcaption><p>IPv4 Addresses, Network and Host Portions /Parts</p></figcaption></figure>

Within the 32-bit stream of an IPv4 address , a portion of the bits identify the network, and a portion of the bits identify the host.

The bits within the **network portion** of the address must be <mark style="background-color:blue;">identical for all devices that reside in the same network</mark>. The bits within the **host portion** of the address must be <mark style="background-color:blue;">unique to identify a specific host within a network</mark>.

If two hosts have the same bit-pattern in the specified network portion of the 32-bit stream, those two hosts will reside in the same network.

***

## The Subnet Mask

<figure><img src=".gitbook/assets/image (96).png" alt=""><figcaption><p>IP Address &#x26; Subnet Mask</p></figcaption></figure>

Comparing the IP Address and the Subnet Mask: The **1s** in the subnet mask identify the <mark style="background-color:blue;">network portion</mark> while the **0s** identify the <mark style="background-color:blue;">host portion</mark>.

<figure><img src=".gitbook/assets/image (97).png" alt=""><figcaption><p>Logical AND Result</p></figcaption></figure>

Use the Logical AND for the comparison of two bits: ANDing between the IP address and the subnet mask yields the network address.

How do <mark style="background-color:blue;">hosts know which portion of the 32-bits identifies the network and which identifies the host</mark>? That is **the job of the subnet mask**.

Three dotted decimal IPv4 addresses must be configured when assigning an IPv4 configuration to host:

* **IPv4 address** – Unique IPv4 address of the host
* **Subnet mask**- Used to <mark style="background-color:blue;">identify the network/host portion of the IPv4 address</mark>
* **Default gateway** – Identifies the <mark style="background-color:blue;">local gateway</mark> (i.e. local router interface IPv4 address) to reach remote networks

When an IPv4 address is assigned to a device, the subnet mask is used to determine the **network address** where the device belongs. The network address represents all the devices on the same network. Note that the subnet mask does not actually contain the network or host portion of an IPv4 address, it just tells the computer where to look for these portions in a given IPv4 address.

The <mark style="background-color:blue;">actual process used to identify the network portion and host portion</mark> is called **ANDing**.

***

## The Prefix Length

<figure><img src=".gitbook/assets/image (98).png" alt=""><figcaption><p>Prefix Length</p></figcaption></figure>

* Shorthand method of identifying a subnet mask.&#x20;
* It is the number of bits set to 1 in the subnet mask.&#x20;
* Written in “slash notation”, a “/” followed by the number of bits set to 1.

***

## Network, Host, and Broadcast Addresses

<figure><img src=".gitbook/assets/image (99).png" alt=""><figcaption><p>An Example</p></figcaption></figure>

A host successfully connected to a network can communicate with other devices in one of three ways:

* **Unicast** - The process of sending a packet from one host to an individual host.
* **Broadcast** - The process of sending a packet from one host to all hosts in the network.
* **Multicast** - The process of sending a packet from one host to a selected group of hosts, possibly in different networks. In all three cases, the IPv4 address of the originating host is placed in the packet header as the source address.

***

## Legacy Classful Addressing vs Classless Addressing

<figure><img src=".gitbook/assets/image (84).png" alt=""><figcaption><p>Classful Addressing: Class A</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (85).png" alt=""><figcaption><p>Classful Addressing: Class B</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (86).png" alt=""><figcaption><p>Classful Addressing: Class C</p></figcaption></figure>

In 1981, Internet IPv4 addresses were assigned using **classful addressing**. Customers were allocated a network address based on one of three classes, A, B, or C:

* **Class A (0.0.0.0/8 to 127.0.0.0/8)** – Designed to support <mark style="background-color:blue;">extremely large networks with more than 16 million host addresses</mark>. It used a fixed /8 prefix with the first octet to indicate the network address and the remaining three octets for host addresses.
* **Class B (128.0.0.0 /16 – 191.255.0.0 /16)** – Designed to support the needs of <mark style="background-color:blue;">moderate to large size networks with up to approximately 65,000 host addresses</mark>. It used a fixed /16 prefix with the two high-order octets to indicate the network address and the remaining two octets for host addresses.
* **Class C (192.0.0.0 /24 – 223.255.255.0 /24)** – Designed to support <mark style="background-color:blue;">small networks with a maximum of 254 hosts</mark>. It used a fixed /24 prefix with the first three octets to indicate the network and the remaining octet for the host addresses.

{% hint style="info" %}
_Note: There is also a Class D multicast block consisting of 224.0.0.0 to 239.0.0.0 and a Class E experimental address block consisting of 240.0.0.0 – 255.0.0.0._
{% endhint %}

The classful system allocated 50% of the available IPv4 addresses to 128 Class A networks, 25% of the addresses to Class B and then Class C shared the remaining 25% with Class D and E. The problem is that this wasted a great deal of addresses and exhausted the availability of IPv4 addresses.

Not all organizations' requirements fit well into one of these three classes. For example, a company that had a network with 260 hosts would need to be given a class B address with more than 65,000 addresses wasting 64,740 addresses.

<mark style="background-color:blue;">The system in use today</mark> is referred to as **classless addressing**. The formal name is **Classless Inter-Domain Routing** (**CIDR**, pronounced “cider) which allows service providers to allocate IPv4 addresses on **any address bit boundary (prefix length)** instead of only by a class A, B, or C address.

_Public IPv4 addresses are addresses which are globally routed between ISP (Internet Service Provider) routers._ However, not all available IPv4 addresses can be used on the Internet. There are blocks of addresses called **private addresses** that are used by most organizations to <mark style="background-color:blue;">assign IPv4 addresses to internal hosts</mark>. **Private IPv4 addresses are not unique and can be used by an internal network; but they are not allowed on the Internet and must be filtered (discarded) by Internet routers.** For instance, most home routers assign IPv4 addresses to their wired and wireless hosts from the private address of 192.168.1.0 /24. The home router interface that connects to the Internet service provider (ISP) network is assigned a public IPv4 address to use on the Internet.

{% hint style="info" %}
The private address blocks are:

**10.0.0.0 /8** or **10.0.0.0 to 10.255.255.255**

**172.16.0.0 /12** or **172.16.0.0 to 172.31.255.255**

**192.168.0.0 /16** or **192.168.0.0 to 192.168.255.255**
{% endhint %}

***

## Broadcast Domains

<div align="center">

<figure><img src=".gitbook/assets/image (87).png" alt="" width="375"><figcaption><p>Broadcast Domain</p></figcaption></figure>

</div>

<figure><img src=".gitbook/assets/image (88).png" alt="" width="375"><figcaption><p>Subnets</p></figcaption></figure>

<mark style="background-color:blue;">Each router interface</mark> connects a **broadcast domain** and <mark style="background-color:blue;">broadcasts are only propagated within its specific broadcast domain.</mark>

A large broadcast domain is a network that connects many hosts. A problem with a <mark style="background-color:blue;">large broadcast domain</mark> is that these hosts can <mark style="background-color:blue;">generate excessive broadcasts</mark> and negatively affect the network resulting in:

* **Slow network operations** due to the significant amount of traffic it can cause
* **Slow device operations** because a device must accept and process each broadcast packet

The solution is to <mark style="background-color:blue;">reduce the size of the network to create smaller broadcast domains</mark> in a process called **subnetting**. These <mark style="background-color:blue;">smaller network spaces</mark> are called **subnets**.

{% hint style="info" %}
Note: The terms subnet and network are often used interchangeably. Most networks are a subnet of some larger address block.
{% endhint %}



***

## Classless Subnetting

<figure><img src=".gitbook/assets/image (72).png" alt=""><figcaption><p>A Case of Classless Subnetting</p></figcaption></figure>

<mark style="background-color:blue;">Subnets can borrow bits from any host bit position to create other masks.</mark>

For instance, a /24 network address is commonly subnetted using longer prefix lengths by borrowing bits from the fourth octet. This provides the administrator with additional flexibility when assigning network addresses to a smaller number of end devices:

**/25 row** - Borrowing 1 bit from the fourth octet creates **2 subnets** supporting 126 hosts each.

**/26 row** - Borrowing 2 bits creates **4 subnets** supporting 62 hosts each.

**/27 row** – Borrowing 3 bits creates **8 subnets** supporting 30 hosts each.

**/28 row** – Borrowing 4 bits creates **16 subnets** supporting 14 hosts each.

**/29 row** – Borrowing 5 bits creates **32 subnets** supporting 6 hosts each.

**/30 row** – Borrowing 6 bits creates **64 subnets** supporting 2 hosts each.

For each bit borrowed in the fourth octet, the number of subnetworks available is doubled while reducing the number of host addresses per subnet.

***

To understand how subnetting at a classless level can be useful, consider the following example.

<figure><img src=".gitbook/assets/image (100).png" alt="" width="410"><figcaption><p>192.168.1.0/25 Network</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (101).png" alt="" width="379"><figcaption><p>Dotted Decimal Address</p></figcaption></figure>

Consider the private network address _192.168.1.0/24 (Illustrated above)_ . The **first three octets are displayed in decimal**, while the **last octet is displayed in binary**. The reason for this is because we will be borrowing bits from the last octet to create subnets of the 192.168.1.0/24 network.

The subnet mask is 255.255.255.0 as indicated by the /24 prefix length. This identifies the first three octets as the network portion and the remaining 8 bits in the last octet as the host portion. Without subnetting, this network supports a single LAN interface providing 254 host IPv4 addresses. If an additional LAN is needed, the network would need to be subnetted.

Then: 1 bit is borrowed from the most significant bit (leftmost bit) in the host portion, thus extending the network portion to 25 bits or /25. This enables the creation of two subnets: <mark style="background-color:blue;">192.168.1.0/25 and 192.168.1.128/25</mark>.

The two subnets are derived from changing the value of the bit borrowed to either 0 or 1. Because the bit borrowed is the 128 bit, the decimal value of the fourth octet for the 2nd subnet is 128.

Because one bit has been borrowed, the subnet mask for each subnet is 255.255.255.128 or /25.

<figure><img src=".gitbook/assets/image (102).png" alt="" width="287"><figcaption><p>/25 Subnetting Topology</p></figcaption></figure>

To see how a /25 subnet is applied in a network; consider the shown topology: R1 has two LAN segments attached to its GigabitEthernet interfaces. Each LAN is assigned one of the subnets.

<figure><img src=".gitbook/assets/image (103).png" alt="" width="469"><figcaption><p>192.168.1.0/25 Subnet</p></figcaption></figure>

For the first subnet, _192.168.1.0/25_:

**IPv4 Network address** is 192.168.1.0 and contains all 0 bits in the host portion of the address.

**First IPv4 host address** is 192.168.1.1 and contains all 0 bits plus a right-most 1 bit in the host portion of the address.

**Last IPv4 host address** is 192.168.1.126 and contains all 1 bits plus a right-most 0 bit in the host portion of the address.

**IPv4 Broadcast address** is 192.168.1.127 and contains all 1 bits in the host portion of the address.

<figure><img src=".gitbook/assets/image (104).png" alt="" width="410"><figcaption><p>192.168.1.128/25</p></figcaption></figure>

For the second subnet, 192.168.1.128/25: compare the Network address with that of subnet 192.168.1.0/25, what do you make of that?

Notice that the default gateway IPv4 address is the address configured on the G0/1 interface of R1!

***

## Subnetting Formulas

<figure><img src=".gitbook/assets/image (105).png" alt="" width="383"><figcaption><p>Calculate the Number of Subnets</p></figcaption></figure>

To calculate the number of subnets use the formula **2^n** where n refers to **bits borrowed**.

<figure><img src=".gitbook/assets/image (106).png" alt="" width="458"><figcaption><p>Calculate the Number of Hosts</p></figcaption></figure>

To calculate the number of hosts use the formula **2^h-2** where h refers to the number of **remaining bits** in the host portion.

Good to take into account: <mark style="background-color:blue;">The last two bits cannot be borrowed from the last octet because there would be no host addresses available</mark>.

***

## Creating 4 Subnets

<figure><img src=".gitbook/assets/image (107).png" alt="" width="392"><figcaption><p>Borrowing 2 Bits</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (108).png" alt="" width="429"><figcaption><p>192.168.1.0/26</p></figcaption></figure>

Let us suppose an enterprise is using the private network address 192.168.1.0/24 range and requires three subnets. Borrowing a single bit only provided 2 subnets; therefore, another host bit must be borrowed  (as according to the **2^n** formula for two borrowed bits results in **2^2 = 4** subnets).

To calculate the number of hosts, examine the last octet: after borrowing 2 bits for the subnet, there are 6 host bits remaining. Apply the host calculation formula **2^h - 2** to reveal that each subnet can support **62** host addresses.

<figure><img src=".gitbook/assets/image (109).png" alt="" width="563"><figcaption><p>Address Ranges Nets 0-2</p></figcaption></figure>

***

## Creating Subnets with a /16 Prefix

<figure><img src=".gitbook/assets/image (110).png" alt=""><figcaption></figcaption></figure>

In a situation requiring a larger number of subnets, an IPv4 network is required that has more hosts bits to borrow from. For example, the network address 172.16.0.0 has a default mask of <mark style="background-color:blue;">255.255.0.0, or /16</mark>. This address has 16 bits in the network portion and 16 bits in the host portion. The <mark style="background-color:blue;">16 bits in the host portion are available to borrow for creating subnets</mark>.

Although a complete memorization of the table is not required, it is suggested that you gain a good understanding of how each value in the table is generated. Do not let the size of the table intimidate you. The reason it is big is because it has 8 additional bits that can be borrowed, and, therefore, the number of subnets and hosts are simply larger.

***

## Creating 100 Subnets with a /16 Network

<figure><img src=".gitbook/assets/image (111).png" alt="" width="563"><figcaption><p>/26 Network</p></figcaption></figure>

When borrowing bits from a /16 address, start borrowing bits in the third octet, going from left to right. Borrow a single bit at a time until the number of bits necessary to create <mark style="background-color:blue;">100 subnets</mark> is reached.

To satisfy the requirements of the enterprise, 7 bits (i.e., 2^7 = 128 subnets) would need to be borrowed.

Recall that the subnet mask must change to reflect the borrowed bits. In this example, when 7 bits are borrowed, the mask is extended 7 bits into the third octet. In decimal, the mask is represented as <mark style="background-color:blue;">255.255.254.0, or a /23 prefix</mark>, because the third octet is 11111110 in binary and the fourth octet is 00000000 in binary.

<figure><img src=".gitbook/assets/image (112).png" alt="" width="379"><figcaption><p>/23 Subnets</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (113).png" alt="" width="393"><figcaption><p>Address Range for 172.16.0.0/23 Subnet</p></figcaption></figure>

To calculate the number of hosts each subnet can support, examine the third and fourth octet. After borrowing 7 bits for the subnet, there is one host bit remaining in the third octet and 8 host bits remaining in the fourth octet for a total of 9 bits that were not borrowed.

Apply the host calculation: there are only <mark style="background-color:blue;">510 host addresses</mark> that are available for each /23 subnet. The first host address for the first subnet is 172.16.0.1, and the last host address is 172.16.1.254.

***

## Default Gateway

<figure><img src=".gitbook/assets/image (114).png" alt=""><figcaption><p>Host Default Gateway</p></figcaption></figure>

<mark style="background-color:blue;">Another role of the network layer is to direct packets between hosts.</mark> A **host** can send a packet to:

**Itself** - IPv4 address of 127.0.0.1, which is referred to as the <mark style="background-color:blue;">loopback interface</mark>. Pinging the loopback interface tests the TCP/IP protocol stack on the host.

**Local host** - This is <mark style="background-color:blue;">a host on the same local network as the sending host</mark>. The hosts <mark style="background-color:blue;">share the same network address</mark>.

**Remote host** - This is <mark style="background-color:blue;">a host on a remote network</mark>. The hosts do not share the same network address.

Whether a packet is destined for a local host or a remote host is determined by the IPv4 address and subnet mask combination of the source (or sending) device compared to the IPv4 address and subnet mask of the destination device.

If a host is sending a packet to a device that is configured with the **same IP network** as the host device, the packet is simply <mark style="background-color:blue;">forwarded out of the host interface, through the intermediate device, and to the destination device directly</mark>.

Devices that are beyond the local network segment are known as **remote hosts**. When a source device sends a packet to a remote destination device, then the help of <mark style="background-color:blue;">routers and routing is needed</mark>. **Routing** is the <mark style="background-color:blue;">process of identifying the best path to a destination</mark>. <mark style="background-color:blue;">The router connected to the local network segment</mark> is referred to as the **default gateway**.

The default gateway is the network device that can <mark style="background-color:blue;">route traffic to other networks</mark>. It is the router that can route traffic out of the local network.

* Routes traffic to other networks
* Has a local IP address in the same address range as other hosts on the network
* Can take data in and forward data out

***

## Router Packet Forwarding Decision

<figure><img src=".gitbook/assets/image (115).png" alt=""><figcaption><p>Directly Connected and Remote Network Routes</p></figcaption></figure>

When a host sends a packet to another host, it will use its **routing table** to determine where to send the packet. <mark style="background-color:blue;">If the destination host is on a remote network, the packet is forwarded to the default gateway.</mark>

What happens when a packet arrives at the default gateway, which is usually a router? <mark style="background-color:blue;">The router looks at its routing table to determine where to forward packets.</mark>

The **routing table** of a router can store information about:

* **Directly-connected routes** - These routes come from the <mark style="background-color:orange;">active router interfaces</mark>. <mark style="background-color:blue;">Routers add a directly connected route when an interface is configured with an IP address and is activated.</mark> <mark style="background-color:blue;">Each of the router's interfaces is connected to a different network segment</mark>.
* **Remote routes** - These routes come from <mark style="background-color:orange;">remote networks connected to other routers</mark>. Routes to these networks can be <mark style="background-color:blue;">manually configured on the local router by the network administrator</mark> or <mark style="background-color:blue;">dynamically configured by enabling the local router to exchange routing information with other routers using a dynamic routing protocol</mark>.
* **Default route** – Like a host, routers also use a default route as a <mark style="background-color:blue;">last resort if there is no other route to the desired network in the routing table</mark>.

***

## IPv4 Router Routing Table

<figure><img src=".gitbook/assets/image (116).png" alt="" width="563"><figcaption><p>R1 IPv4 Routing Table</p></figcaption></figure>

The **show ip route** command can be used to <mark style="background-color:blue;">display the router’s IPv4 routing table</mark>. In addition to providing routing information for directly-connected networks and remote networks, the routing table also has information on _how the route was learned, the trustworthiness and rating of the route, when the route was last updated, and which interface to use to reach the requested destination_.

When a packet arrives at the router interface, the router examines the packet header to determine the destination network. If the destination network matches a route in the routing table, the router forwards the packet using the information specified in the routing table. <mark style="background-color:blue;">If there are two or more possible routes to the same destination, the metric is used to decide which route appears in the routing table.</mark>

***

## Verify Interface Configuration

<figure><img src=".gitbook/assets/image (89).png" alt=""><figcaption><p>Verify Interface Configuraiton</p></figcaption></figure>

* **Show ip route** - Displays the contents of the IPv4 routing table stored in RAM.
* **Show interfaces** -Displays statistics for all interfaces on the device.
* **Show ip interface** -Displays the IPv4 statistics for all interfaces on a router.

***

## Limitations of IPv4

There are several network layer protocols in existence; however, there are only two network layer protocols that are commonly implemented:

Internet Protocol version 4 (IPv4)

Internet Protocol version 6 (IPv6)

**IPv4** has three major issues:

* **IP address depletion** - IPv4 has a limited number of unique public IPv4 addresses available. Although there are approximately 4 billion IPv4 addresses, the increasing number of new IP-enabled devices, always-on connections, and the potential growth of less-developed regions have increased the need for more addresses.
* **Internet routing table expansion** - A routing table is used by routers to make best path determinations. As the number of servers connected to the Internet increases, so too does the number of network routes. These IPv4 routes consume a great deal of memory and processor resources on Internet routers.
* **Lack of end-to-end connectivity** - <mark style="background-color:blue;">Network Address Translation (NAT)</mark> is a technology commonly implemented within IPv4 networks. NAT provides a way for <mark style="background-color:blue;">multiple devices to share a single public IPv4 address</mark>. However, because the public IPv4 address is shared, <mark style="background-color:blue;">the IPv4 address of an internal network host is hidden</mark>. This can be problematic for technologies that require end-to-end connectivity.

***

## Introducing IPv6

The _Internet Engineering Task Force (IETF)_ concerned about the issues with IPv4, began to look for a replacement. This leads to the development of IP version 6 (IPv6). IPv6 overcomes the limitations of IPv4 and is a powerful enhancement with features that better suit current and foreseeable network demands.

Motivations of developing IPv6 addressing:

* **Initial motivation**: 32-bit IPv4 address space would be completely allocated\

* **Additional motivation**:&#x20;
  * **Speed processing/forwarding**: 40-byte fixed length header&#x20;
  * Enable different network-layer treatment of “flows”

Improvements that **IPv6** provides include:

* **Increased address space** - IPv6 addresses are based on <mark style="background-color:blue;">128-bit</mark> hierarchical addressing as opposed to IPv4 with 32 bits.
* **Improved packet handling** - The IPv6 header has been simplified with fewer fields.
* **Eliminates the need for NAT** - With such a large number of public IPv6 addresses, NAT between a private IPv4 address and a public IPv4 is not needed.

***

## Transmition from IPv4 to IPv6

<figure><img src=".gitbook/assets/image (90).png" alt=""><figcaption><p>IPv4 VS IPv6</p></figcaption></figure>

* Not all routers can be upgraded simultaneously&#x20;
  * No “flag days”&#x20;
  * How will network operate with mixed IPv4 and IPv6 routers?
* **Tunneling**: IPv6 datagram carried as payload in IPv4 datagram among IPv4 routers (“packet within a packet”)&#x20;
  * Tunneling used extensively in other contexts (4G/5G)
