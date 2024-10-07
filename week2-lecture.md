# 💪 Week2 Lecture

## Further Key Topics and Concepts

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

