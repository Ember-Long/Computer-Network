# 🖥️ Transport & Application Layers

## Role of Transport Layer

<figure><img src=".gitbook/assets/image (16).png" alt="" width="554"><figcaption><p>Tansport Layer</p></figcaption></figure>

The transport layer is responsible for **establishing a communication session** <mark style="background-color:blue;">between two applications for delivering data between them</mark>.

A source computer communicates with a receiving computer to decide how to <mark style="background-color:blue;">break up data into segments</mark>, how to <mark style="background-color:blue;">make sure none of the segments get lost</mark>, and how to <mark style="background-color:blue;">verify all the segments arrived</mark>. All of these processes are  part of and described in the  OSI transport layer.

When thinking about the transport layer, think of a shipping department preparing (but not sending any thing at this stage) a single order of multiple packages for delivery (but not about the physical delivery / communication itself!)

The **transport layer** provides services, such as:&#x20;

* **Connection-oriented  support**&#x20;
* **Reliability**&#x20;
* **Flow control**&#x20;
* **Multiplexing**

***

## Transport Services and Protocols

<figure><img src=".gitbook/assets/image (17).png" alt=""><figcaption><p>Transport Services and Protocols</p></figcaption></figure>

* Provide **logical communication** between application processes running on different hosts
* Transport protocols actions in end systems:&#x20;
  * **Sender**: Breaks application messages into **segments**, passes to network layer&#x20;
  * **Receiver**: Reassembles segments into messages, passes to application layer
* Two transport protocols available to Internet applications:
  * TCP, UDP

By logical communication , we mean that from an **application’s perspective**, it is as if the <mark style="background-color:blue;">hosts running the processes were directly connected</mark>; in reality, the hosts may be on opposite sides of the planet, connected via numerous routers and a wide range of link types. Application processes use the logical communication provided by the transport layer to send messages to each other, free from the worry of the details of the physical infrastructure used to carry these messages.

***

## Transport Layer Responsibilities

<figure><img src=".gitbook/assets/image (145).png" alt=""><figcaption><p>Transport Layer Resonsibilities</p></figcaption></figure>

**Tracking Individual Conversations**

At the transport layer, <mark style="background-color:blue;">each set of data flowing between a source application and a destination application</mark> is known as a **conversation**. A host may have <mark style="background-color:blue;">multiple applications that are communicating across the network simultaneously</mark>. Each of these applications communicates with <mark style="background-color:blue;">one or more</mark> applications on one or more remote hosts. It is the responsibility of the transport layer to maintain and track these multiple conversations.

**Segmenting Data and Reassembling Segments**

Data must be prepared to be sent across the media in <mark style="background-color:blue;">manageable</mark> pieces. Most networks have a limitation on the amount of data that can be included in a single packet. Transport layer protocols have services that <mark style="background-color:blue;">segment the application data into blocks that are an appropriate size.</mark>

At the <mark style="background-color:blue;">destination</mark>, the transport layer must be able to <mark style="background-color:blue;">reconstruct the pieces of data into a complete data stream</mark> that is useful to the application layer.

**Identifying the Applications**

To pass data streams to the proper applications, the transport layer must identify the target application. To accomplish this, the transport layer assigns <mark style="background-color:blue;">each application</mark> an identifier called a **port number**. <mark style="background-color:blue;">Each software</mark> process that needs to access the network is assigned a port number <mark style="background-color:blue;">unique to that host</mark>.

<figure><img src=".gitbook/assets/image (146).png" alt="" width="348"><figcaption><p>Protocols Make for Transpot Reliability</p></figcaption></figure>

The transport layer is also responsible for managing reliability requirements of a conversation. **Different applications have different transport reliability requirements.**

Transport protocols specify <mark style="background-color:blue;">how to transfer messages between hosts</mark>. TCP/IP provides two transport layer protocols, **Transmission Control Protocol (TCP)** and **User Datagram Protocol (UDP)**. IP uses these transport protocols to enable hosts to communicate and transfer data.

<mark style="background-color:blue;">TCP</mark> is considered a reliable, full-featured transport layer protocol, which ensures that <mark style="background-color:blue;">all of the data arrives at the destination</mark>. However, this requires additional fields in the <mark style="background-color:blue;">TCP header</mark> which <mark style="background-color:blue;">increases the size of the packet and also increases delay</mark>.

In contrast, <mark style="background-color:blue;">UDP</mark> is a simpler transport layer protocol that <mark style="background-color:blue;">does not provide for reliability</mark>. It therefore has <mark style="background-color:blue;">fewer fields</mark> and is <mark style="background-color:blue;">faster</mark> than TCP.

### TCP vs UDP

<table data-view="cards"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td><h3>TCP</h3></td><td><p>TCP transport is reliable because it supports <mark style="background-color:blue;">packet delivery confirmation</mark>. </p><p>There are three basic operations that enable reliability with TCP:</p><ul><li>Numbering and tracking data segments transmitted to a specific host from a specific application </li><li>Acknowledging received data </li><li>Retransmitting any unacknowledged data after a certain period of time</li></ul></td><td></td></tr><tr><td><h3>UDP</h3></td><td><ul><li>If reliability is not required, UDP is a better transport protocol.</li></ul><ul><li>Some applications do not require reliability. <mark style="background-color:blue;">Reliability incurs additional overhead and possible delays in transmission.</mark></li></ul><ul><li>UDP provides the basic functions for delivering data segments between the appropriate applications, with <mark style="background-color:blue;">very little overhead</mark> and data checking.</li></ul></td><td></td></tr></tbody></table>

While the <mark style="background-color:blue;">TCP</mark> reliability functions provide more <mark style="background-color:blue;">robust</mark> communication between applications, they also <mark style="background-color:blue;">incur additional overhead and possible delays</mark> in transmission.

Adding overhead to ensure reliability for some applications could reduce the usefulness of the application and can even be detrimental. In such cases, UDP is a better transport protocol.

UDP provides the basic functions for delivering data segments between the appropriate applications, with very little overhead and data checking. <mark style="background-color:blue;">UDP</mark> is known as a <mark style="background-color:blue;">best-effort delivery protocol</mark>. In the context of networking, best-effort delivery is referred to as <mark style="background-color:blue;">unreliable</mark> because there is <mark style="background-color:blue;">no acknowledgment that the data is received at the destination</mark>. With UDP, there are no transport layer processes that inform the sender of a successful delivery.

UDP is similar to placing a regular, non-registered, letter in the mail. The sender of the letter is not aware of the availability of the receiver to receive the letter. Nor is the post office responsible for tracking the letter or informing the sender if the letter does not arrive at the final destination.

***

## Conversation Multiplexing

<figure><img src=".gitbook/assets/image (147).png" alt=""><figcaption><p>Conversation Multiplexing</p></figcaption></figure>

Sending some types of data (for example, a streaming video) across a network, as one complete communication stream, can consume all of the available bandwidth. This will then prevent other communications from occurring at the same time. It would also make error recovery and retransmission of damaged data difficult.

To <mark style="background-color:blue;">identify each segment of data</mark>, the transport layer adds a header containing <mark style="background-color:blue;">binary data</mark> organized into several fields. It is the values in these fields that enable various transport layer protocols to <mark style="background-color:blue;">perform different functions in managing data communication</mark>.

***

## TCP Features

<figure><img src=".gitbook/assets/image (150).png" alt=""><figcaption><p>TCP Features</p></figcaption></figure>

**Establishing a Session**

TCP is a <mark style="background-color:blue;">connection-oriented protocol</mark>. A connection-oriented protocol is one that <mark style="background-color:blue;">negotiates and establishes a connection (or session) between source and destination devices</mark> prior to forwarding any traffic. Through session establishment, <mark style="background-color:blue;">the devices negotiate the amount of traffic that can be forwarded at a given time</mark>.

**Reliable Delivery**

In networking terms, reliability means ensuring that <mark style="background-color:blue;">each segment that the source sends arrives at the destination</mark>. For many reasons, <mark style="background-color:blue;">it is possible for a segment to become corrupted or lost completely</mark>, as it is transmitted over the network.

**Same-Order Delivery**

Because networks may provide multiple routes that can have different transmission rates, data can arrive in the wrong order. By <mark style="background-color:blue;">numbering and sequencing the segments</mark>, TCP can ensure that these segments are reassembled into the proper order.

**Flow Control**

Network hosts have limited resources, such as memory and processing power. TCP can request that the <mark style="background-color:blue;">sending application reduce the rate of data flow to match the hosts limited resources</mark>.  TCP can regulate the amount of data the source transmits. Flow control can prevent the need for retransmission of the data when the receiving host's recourses are overwhelmed.

## UDP Features

<figure><img src=".gitbook/assets/image (151).png" alt=""><figcaption></figcaption></figure>

User Datagram Protocol (UDP) is considered a best-effort transport protocol. UDP is a <mark style="background-color:blue;">lightweight transport protocol</mark>, but **without TCP reliability and flow control**. UDP is such a simple protocol that it is usually described in terms of what it does not do compared to TCP.

## Transport Layer Protocols: Which is More Suitable?

<figure><img src=".gitbook/assets/image (152).png" alt="" width="330"><figcaption><p>TCP</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (153).png" alt="" width="303"><figcaption><p>UDP</p></figcaption></figure>

TCP is a better choice for:&#x20;

* Applications whose segments must arrive in a <mark style="background-color:blue;">very specific sequence</mark> to be processed successfully.&#x20;
* Application in which all data must be <mark style="background-color:blue;">fully received</mark> before any is considered useful.&#x20;

Applications requiring **TCP** include: **Databases, Web browsers, Email clients**.&#x20;

UDP is a better choice for applications that can <mark style="background-color:blue;">tolerate some data loss</mark> during transmission, but <mark style="background-color:blue;">delays in transmission are unacceptable</mark>.

There are three types of applications that are best suited for **UDP**:

* **Live video and multimedia applications** - Can tolerate some data loss, but require little or no delay. Examples include VoIP and live streaming video.
* **Simple request and reply applications** - Applications with simple transactions where a host sends a request and may or may not receive a reply. The size of the packets can be small. Examples include DNS and DHCP.
* **Applications that handle reliability themselves** – Unidirectional communications where flow control, error detection, acknowledgements, and error recovery is not required or can be handled by the application.  Examples include SNMP and TFTP.

For some applications, segments must arrive in a very specific sequence to be processed successfully. With other applications, all data must be fully received before any is considered useful. In both of these instances, TCP is used as the transport protocol. Application developers must choose which transport protocol type is appropriate based on the requirements of the applications.

For example, applications such as databases, web browsers, and email clients, require that all data that is sent arrives at the destination in its original condition. Any missing data could cause a corrupt communication that is either incomplete or unreadable. These applications are designed to use TCP.

In other cases, an application can tolerate some data loss during transmission over the network, but delays in transmission are unacceptable. UDP is the better choice for these applications because less network overhead is required. UDP is preferable for applications such as streaming live audio, live video, and Voice over IP (VoIP). Acknowledgments and retransmission would slow down delivery.

## TCP & UDP Headers

<table data-view="cards"><thead><tr><th></th><th></th><th></th></tr></thead><tbody><tr><td><h3>TCP Headers</h3></td><td><ul><li>TCP is a <mark style="background-color:blue;">stateful protocol</mark>. It <mark style="background-color:blue;">keeps track of the state</mark> of the communication session. </li><li>Each TCP segment has <strong>20 bytes</strong> of overhead in the header encapsulating the application layer data.</li></ul></td><td><img src=".gitbook/assets/image (154).png" alt="" data-size="original"></td></tr><tr><td><h3>UDP Headers</h3></td><td><ul><li>UDP is a <mark style="background-color:blue;">stateless protocol</mark>.</li></ul><ul><li>If needed: reliability must be handled by the application.</li></ul><ul><li>UDP has a low overhead<br>of <strong>8 bytes</strong>.</li></ul></td><td><img src=".gitbook/assets/image (155).png" alt="" data-size="original"></td></tr></tbody></table>

***

## Port Numbers

<figure><img src=".gitbook/assets/image (156).png" alt=""><figcaption><p>Port Numbers</p></figcaption></figure>

**Source Port**&#x20;

* The source port number is <mark style="background-color:blue;">dynamically chosen</mark> by the sending device to identify a conversation between two devices.&#x20;
* <mark style="background-color:blue;">An HTTP client usually sends multiple HTTP requests</mark> to a web server at the same time. <mark style="background-color:blue;">Each separate HTTP conversation is tracked</mark> based on the source ports.&#x20;

**Destination Port**&#x20;

* Used to identify an application or service running in the server. A server can offer more than one service at the same time, offering a web service on port 80 and File Transfer Protocol (FTP) on port 21 simultaneously.

The transport layer must separate and manage multiple communications with different transport requirements as different applications are sending and receiving data over the network simultaneously.

Unique header values allow TCP and UDP to manage these multiple and simultaneous conversations by identifying these **applications**. These unique identifiers are the **port numbers**.

The source port number is associated with the originating application on the local host. The destination port number is associated with the destination application on the remote host.

**Well-known Ports (Numbers 0 to 1023)** - These numbers are reserved for services and applications commonly used such as <mark style="background-color:blue;">web browsers, email clients, and remote access</mark>. By defining these well-known ports for server applications, client applications can be programmed to request a connection to that specific port and its associated service.

**Registered Ports (Numbers 1024 to 49151)** - These port numbers are assigned by <mark style="background-color:blue;">IANA</mark> (standardization body also responsible of <mark style="background-color:blue;">assigning IP addresses</mark>!) to a requesting entity to use with specific processes or applications. These processes are primarily individual applications that <mark style="background-color:blue;">a user has chosen to install</mark>, rather than common applications (a common applications usually receives a well-known port number).

**Dynamic or Private Ports (Numbers 49152 to 65535)** - Also known as <mark style="background-color:blue;">ephemeral ports</mark>, these are assigned dynamically by the client’s OS when a connection to a service is initiated. The dynamic port is then used to identify the client application during communication.

***

## Socket Pairs

<figure><img src=".gitbook/assets/image (157).png" alt=""><figcaption><p>Socket Pairs</p></figcaption></figure>

* The combination of the **source IP address and source port number**, or the **destination IP address and destination port number**, is known as a **socket**.&#x20;
* The socket is used to <mark style="background-color:blue;">identify the server and service being requested by the client</mark>.&#x20;
* <mark style="background-color:blue;">Two sockets combine to form a socket pair</mark>: (192.168.1.5:1099, 192.168.1.7:80)&#x20;
* Sockets enable <mark style="background-color:blue;">multiple processes running on a client and multiple connections to a server process to be distinguished from each other</mark>. The source port number acts as a return address for the requesting application. It is the transport layer’s job to keeps track of active sockets. The transport layer keeps track of this port and the application that initiated the request so that when a response is returned, it can be forwarded to the correct application.

Putting it together:

The **source and destination ports** are placed within the **segment**; the segments are then encapsulated within an IP packet which contains the IP address of the source and destination.

A client socket might look like 192.168.1.5:1099 with 1099 representing the source port number.

The socket on a web server might be: 192.168.1.7:80

Together, these two sockets combine to form a socket pair: 192.168.1.5:1099, 192.168.1.7:80

***

## Stop-and-Wait Operation

<figure><img src=".gitbook/assets/image (158).png" alt=""><figcaption><p>Stop-and-Wait Operation</p></figcaption></figure>

**Round trip time RTT**

**L / R**: time to <mark style="background-color:blue;">generate packet bits and put them on the channel</mark> – depending on _channel capacity R_ and _packet length L_

<mark style="background-color:blue;">The sender will not send a new piece of data until it is sure that the receiver has correctly received the current packet.</mark>

Protocol limits performance of underlying infrastructure (channel) – efficiency loers when RTT is much more important than L/R

Improvement - **pipelining**: sender allows multiple, yet-to-be-acknowledged packets

* Sequence numbers to be added to packets
* Buffering at sender and/or receiver

***

## Go-Back-N

<figure><img src=".gitbook/assets/image (159).png" alt=""><figcaption><p>Go-Back-N</p></figcaption></figure>

**Sender**: uses a “window” of up to N, consecutive transmitted but  nacknowledged packets

**Cumulative ACK**: ACK(n): ACKs all packets up to, including n&#x20;

* On receiving ACK(n): move window forward to begin at n+1&#x20;

Timer for oldest in-flight packet&#x20;

Timeout(n): retransmit <mark style="background-color:blue;">packet n and all higher seq num. packets in window</mark>

**Receiver**: ACK-only: always send ACK for <mark style="background-color:blue;">correctly-received packet so far</mark>, with <mark style="background-color:blue;">highest in-order sequence num</mark>. May generate duplicate ACKs&#x20;

On receipt of out-of-order packet: re-ACK pkt with <mark style="background-color:blue;">highest in-order sequence num</mark>.

**In Go-Back-N, the sender controls the flow of packets**

There exist two pointers to keep track of send base and the next packet to send

The receiver implementation of the Go-Back-N is as simple as possible

The receiver only keeps track of the expected sequence number to receive next:

There is no receiver buffer: <mark style="background-color:blue;">out of order packets are simply discarded</mark>. Similarly, <mark style="background-color:blue;">corrupted packets are also silently discarded</mark>

The Go-Back-N protocol adopts the use of cumulative acknowledgments. That is, <mark style="background-color:blue;">receiving acknowledgment for frame n  means the frames n-1, n-2, and so on are acknowledged as well</mark>.

***

## Selective Repeat

* Receiver **individually** acknowledges all correctly received packets
  * Buffers packets, as needed, for eventual in-order delivery to upper layer
* Sender times-out/retransmits **individually** for unACKed packets
  * Sender maintains timer for each unACKed packet
* Sender window
  * N consecutive sequence numbers

An important mechanism of GBN (Go-Back-N) was the use of the cumulative acknowledgements, and cumulative ACKs are used in TCP

An alternate ACK mechanism would be for the receiver to individually acknowledge specific packets as they are received.  This mechanism is at the heart of the Selective repeat protocol.

***

## TCP Connection Establishment

<figure><img src=".gitbook/assets/image (160).png" alt=""><figcaption><p>TCP Connection Establishment</p></figcaption></figure>

In some cultures, when two persons meet, they often greet each other by shaking hands. The act of shaking hands is understood by both parties as a signal for a friendly greeting. Connections on the network are similar.

In TCP connections, the host client establishes the connection with the server.

A TCP connection is established in three steps:

1. The initiating client requests a client-to-server communication session with the server.
2. The server acknowledges the client-to-server communication session and requests a server-to-client communication session.
3. The initiating client acknowledges the server-to-client communication\
   session.

This may be referred to as TCP three-way handshake!

## TCP Three-Way Handshake Analysis

<figure><img src=".gitbook/assets/image (161).png" alt=""><figcaption></figcaption></figure>

The three-way handshake:

* Establishes that the destination device is present on the network.
* Verifies that the destination device has an active service and is accepting requests on the destination port number that the initiating client intends to use
* Informs the destination device that the source client intends to establish a communication session on that port number.

***

## TCP Session Termination

<figure><img src=".gitbook/assets/image (74).png" alt=""><figcaption><p>TCP Session Termination</p></figcaption></figure>

To close a connection, the Finish **(FIN) control flag** must be set in the <mark style="background-color:blue;">segment header</mark>. To end each one-way TCP session, a two-way handshake, consisting of a FIN segment and an Acknowledgment (ACK) segment, is used.

Therefore, to terminate a single conversation supported by TCP, four exchanges are needed to end both sessions.

{% hint style="info" %}
Note: In this explanation, the terms client and server are used as a reference for simplicity, but the termination process can be initiated by any two hosts that have an open session
{% endhint %}

The FIN TCP flag is used to terminate a TCP connection.

1. When the client has no more data to send in the stream, it sends a segment with the FIN flag set.
2. The server sends an ACK to acknowledge the receipt of the FIN to terminate the session from client to server.
3. The server sends a FIN to the client to terminate the server-to-client session.
4. The client responds with an ACK to acknowledge the FIN from the  erver.
5. When all segments have been acknowledged, the session is closed.

***

## TCP Reliability – Ordered Delivery

<figure><img src=".gitbook/assets/image (75).png" alt=""><figcaption><p>TCP Reliability - Ordered Delivery</p></figcaption></figure>

* TCP segments use <mark style="background-color:blue;">sequence numbers</mark> to uniquely identify and acknowledge each segment, <mark style="background-color:blue;">keep track</mark> of segment order, and indicate how to <mark style="background-color:blue;">reassemble</mark> and <mark style="background-color:blue;">reorder</mark> received segments.&#x20;
* An **initial sequence number (ISN)** is <mark style="background-color:blue;">randomly chosen</mark> during the TCP session setup.&#x20;
* The ISN is then incremented by the number of transmitted bytes. The <mark style="background-color:blue;">receiving TCP process buffers the segment data until all data is received and reassembled</mark>.&#x20;
* Segments received out of order are held for later processing.&#x20;
* <mark style="background-color:blue;">The data is delivered to the application layer only when it has been completely received and reassembled.</mark>

## TCP Reliability - Sequence Numbers and Acknowledgements

* TCP is designed to confirm that **each segment reached its destination**.&#x20;
* TCP session setup ensures the destination is not only reachable, but ready to receive data.&#x20;
* The TCP process on the destination host acknowledges the data it has received from the source application.&#x20;
* <mark style="background-color:blue;">TCP allows for the retransmission of missed segments.</mark>&#x20;
* TCP ensures all segments are properly re-ordered upon receipt.&#x20;
* TCP session termination allows for parties to gracefully end a TCP session when no data is to be transferred (FIN flag).&#x20;
* A TCP endpoint can abruptly terminate a session if necessary (RST flag).

## Application Layer

<figure><img src=".gitbook/assets/image (77).png" alt=""><figcaption><p>Application Layer</p></figcaption></figure>

* The application layer is closest to the end user.&#x20;
* Network applications enable users to send and receive data with ease.&#x20;
* The application layer acts as interface between the applications and the underlying network.&#x20;
* Application layer protocols help exchange data between programs running on the source and destination hosts.&#x20;
* The TCP/IP application layer performs the functions of the upper three layers of the OSI model (application, presentation, and session).&#x20;
* Common application layer protocols include: Hypertext Transfer Protocol (HTTP), File Transfer Protocol (FTP), Trivial File Transfer Protocol (TFTP), Internet Message Access Protocol (IMAP), and Domain Name System (DNS) protocol.

## Presentation and Session Layer

<figure><img src=".gitbook/assets/image (78).png" alt=""><figcaption><p>Presentation Layer</p></figcaption></figure>

### The Presentation Layer

The presentation layer has three primary functions:

* **Formatting**, or **presenting**, data at the <mark style="background-color:blue;">source device</mark> into a <mark style="background-color:blue;">compatible form</mark> for receipt by the destination device
* **Compressing data** in a way that <mark style="background-color:blue;">can be decompressed by the destination device</mark>
* **Encrypting data** for transmission and decrypting data upon receipt

As shown in the figure, the presentation layer formats data for the application layer, and it sets standards for file formats. Some well-known standards for video include QuickTime and Motion Picture Experts Group (MPEG). Some well-known graphic image formats that are used on networks are Graphics Interchange Format (GIF), Joint Photographic Experts Group (JPEG), and Portable Network Graphics (PNG) format.

### The Session Layer

As the name implies, functions at the session layer create and maintain dialogs between source and destination applications. The session layer handles the exchange of information to initiate dialogs, keep them active, and to restart sessions that are disrupted or idle for a long period of time.

***

## TCP/IP Application Layer Protocols

<figure><img src=".gitbook/assets/image (80).png" alt=""><figcaption><p>TCP/IP Application Layer Protocols</p></figcaption></figure>

* TCP/IP application protocols specify the <mark style="background-color:blue;">format and control information</mark> necessary for common Internet functions.&#x20;
* Application layer protocols must be implemented in both the source and destination devices.&#x20;
* Application layer protocols implemented on the source and destination host must be compatible to allow communication.

***

## Client-Sever Model

<figure><img src=".gitbook/assets/image (81).png" alt=""><figcaption><p>Client-Sever Model</p></figcaption></figure>

* The device requesting the information is called a client.&#x20;
* The device responding to the request is called a server.&#x20;
* <mark style="background-color:blue;">Client and server processes are considered to be in the application layer.</mark>&#x20;
* The client initiates the exchange by requesting data from the server.&#x20;
* The server responds by sending one or more streams of data to the client.&#x20;
* Application layer protocols describe the <mark style="background-color:blue;">format of the requests and responses</mark> between clients and servers.&#x20;
* The contents of the data exchange will depend of the application in use.&#x20;
* Email is an example of a Client-Server interaction.

***

## Peer-to-Peer Networks

<figure><img src=".gitbook/assets/image (82).png" alt=""><figcaption><p>P2P Networks</p></figcaption></figure>

In the **peer-to-peer (P2P) networking** model, <mark style="background-color:blue;">the data is accessed from a peer device without the use of a dedicated server</mark>.

The P2P network model involves two parts: <mark style="background-color:blue;">P2P networks and P2P applications</mark>. Both parts have similar features, but in practice work quite differently.

In a P2P network, two or more computers are connected via a network and can share resources (such as printers and files) without having a dedicated server. Every **connected end device** (known as a **peer**) can <mark style="background-color:blue;">function as both a server and a client</mark>. One computer might assume the role of server for one transaction while simultaneously serving as a client for another. The roles of client and server are set on a per request basis.

In addition to sharing files, a network such as this one would allow users to enable networked games, or share an Internet connection.

## Peer-to-Peer Aplications

<figure><img src=".gitbook/assets/image (83).png" alt=""><figcaption><p>Peer-to-Peer Applications</p></figcaption></figure>

* Some P2P applications use a hybrid system.&#x20;
* In hybrid P2P, resource sharing is decentralized.&#x20;
* Indexes that point to resource locations are stored in a centralized directory.&#x20;
* In a hybrid system, each peer accesses an index server to get the location of a resource stored on another peer.

## Common P2P Applications

<figure><img src=".gitbook/assets/image (84).png" alt=""><figcaption><p>Common P2P Application</p></figcaption></figure>

* Common P2P networks include: eDonkey, G2, BitTorrent, Bitcoin.&#x20;
* Many P2P applications allow users to share pieces of many files with each other at the same time.&#x20;
* A small torrent file contains information about the location of other users and tracker computers.&#x20;
* <mark style="background-color:blue;">Trackers are computers keeping track of the files hosted by users.</mark>&#x20;
* This technology is called **BitTorrent**.&#x20;
* There are many BitTorrent clients, including BitTorrent, uTorrent, Frostwire, and qBittorrent.

***

## Hypertext Transfer Protocol and Hypertext Markup Language

When a web address or **uniform resource locator (URL)** is typed into a web browser, the web browser establishes a connection to the web service running on the server using the HTTP protocol. URLs and **Uniform Resource Identifier (URIs)** are the names most people associate with web addresses.

To better understand how the web browser and web server interact, we can examine how a web page is opened in a browser. For this example, use the http://www.cisco.com/index.html URL.

First, the browser interprets the three parts of the URL:

1. &#x20;http (the protocol or scheme)
2. www.cisco.com (the server name)
3. &#x20;index.html (the specific filename requested)

The browser then checks with a name server to <mark style="background-color:blue;">convert www.cisco.com into a numeric IP address</mark>, which it uses to connect to the server.&#x20;

<figure><img src=".gitbook/assets/image (87).png" alt=""><figcaption><p>HTTP Protocols Step 1</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (88).png" alt=""><figcaption><p>HTTP Protocol Step 2</p></figcaption></figure>

<figure><img src=".gitbook/assets/image (89).png" alt=""><figcaption><p>HTTP Protocol Step 3</p></figcaption></figure>

Using HTTP requirements:

1. The browser sends a <mark style="background-color:blue;">GET request</mark> to the server and <mark style="background-color:blue;">asks for the index.html file</mark>.&#x20;
2. The server <mark style="background-color:blue;">sends the HTML code</mark> for this web page to the browser.&#x20;
3. Finally, the browser <mark style="background-color:blue;">deciphers the HTML code and formats the page</mark> for the browser window.

HTTP is a <mark style="background-color:blue;">request/response protocol</mark>. When a client, typically a web browser, sends a request to a web server, HTTP specifies the message types used for that communication. The three common message types are GET, POST, and PUT:

**GET** - A <mark style="background-color:blue;">client request for data</mark>. A client (web browser) sends the GET message to the web server to request HTML pages.

**POST** - Uploads data files to the web server such as form data.

**PUT** - Uploads resources or content to the web server such as an image.

Although HTTP is remarkably flexible, it is <mark style="background-color:blue;">not a secure protocol</mark>. <mark style="background-color:blue;">The request messages send information to the server in plain text that can be intercepted and read.</mark> <mark style="background-color:blue;">The server responses, typically HTML pages, are also unencrypted.</mark>

For secure communication across the Internet, the **HTTP Secure (HTTPS)** protocol is used.

***

## Email Protocols

<figure><img src=".gitbook/assets/image (90).png" alt=""><figcaption><p>Email Protocols</p></figcaption></figure>

* Email is a <mark style="background-color:blue;">store-and-forward method</mark> of sending, storing, and retrieving electronic messages.&#x20;
* <mark style="background-color:blue;">Email clients do not communicate directly when sending email</mark>: Email relies on three separate protocols for operation: **SMTP (sending),POP (retrieving), IMAP (retrieving)**.&#x20;
* Email messages are stored in databases on mail servers.&#x20;
* <mark style="background-color:blue;">Email clients communicate with mail servers to send and receive email.</mark>&#x20;
* <mark style="background-color:blue;">Mail servers communicate with other mail servers to transport messages from one domain to another.</mark>

Email supports three separate protocols for operation: **Simple Mail Transfer Protocol (SMTP), Post Office Protocol (POP), and Internet Message Access Protocol (IMAP)**. The application layer process that sends mail uses SMTP. A client retrieves email, however, using one of the two application layer protocols: POP or IMAP.

## SMTP Operation

<figure><img src=".gitbook/assets/image (91).png" alt=""><figcaption><p>SMTP Operation</p></figcaption></figure>

* An SMTP client sends an email by connecting to a SMTP server on port 25.&#x20;
* The server receives the message and stores it message in a local mailbox or relays the message to another mail server.&#x20;
* Users use email clients to retrieve messages stored on the server.&#x20;
* IMAP and POP are two protocols commonly used by email clients to retrieve messages.

SMTP message formats require a <mark style="background-color:blue;">message header and a message body</mark>. While the message body can contain any amount of text, the message header must have a properly formatted recipient email address and a sender address.

## POP Operation

<figure><img src=".gitbook/assets/image (92).png" alt=""><figcaption><p>POP Operation</p></figcaption></figure>

* <mark style="background-color:blue;">Messages are downloaded from the server to the client.</mark>&#x20;
* The server listens on port 110 TCP for client requests.&#x20;
* Email clients direct their POP requests to mail servers on port TCP 110.&#x20;
* The POP client and server exchange commands and responses until the connection is closed or aborted.&#x20;
* POP allows for email messages to be downloaded to the client’s device (computer or phone) and removed from the server.&#x20;
* There is no centralized location where email messages are kept.&#x20;
* <mark style="background-color:blue;">A downloaded message resides on the device that triggered the download.</mark>

## IMAP Operation

<figure><img src=".gitbook/assets/image (94).png" alt=""><figcaption><p>IMAP Operation</p></figcaption></figure>

* IMAP is another protocol used to retrieve email messages.&#x20;
* Allows for messages to be <mark style="background-color:blue;">displayed to the user rather than downloaded</mark>.&#x20;
* <mark style="background-color:blue;">The original messages reside on the server until manually deleted by the user.</mark>&#x20;
* Users view copies of the messages in their email client software.&#x20;
* Users can create a folder hierarchy on the server to organize and store mail.&#x20;
* That file structure is displayed on the email client.&#x20;
* When a user decides to delete a message, the server synchronizes that action and deletes the message from the server.

***

## Domian Name Service

<figure><img src=".gitbook/assets/image (95).png" alt=""><figcaption><p>Domain Name Service</p></figcaption></figure>

* While IP addresses are crucial for network communication, they are not easy to memorize.&#x20;
* Domain names are created to make server addresses more user-friendly.&#x20;
* However, computers still need the actual numeric address before they can communicate.&#x20;
* The <mark style="background-color:blue;">DNS protocol allows for the dynamic translation of a domain name into the correct IP address</mark>.&#x20;
* The DNS protocol communications using a single format called a **message**.

The DNS protocol defines an automated service that matches resource names with the required numeric network address. It includes the format for queries, responses, and data.

## DNS Message Format

<figure><img src=".gitbook/assets/image (96).png" alt=""><figcaption><p>DNS Message Format</p></figcaption></figure>

The DNS server stores different types of resource records used to resolve names. These records contain the **name, address, and type of record**. Some of these record types are:

* **A** - An end device IPv4 address
* **NS** - An authoritative name server
* **AAAA** - An end device IPv6 address (pronounced quad-A)
* **MX** - A mail exchange record

When a client makes a query, the server’s DNS process <mark style="background-color:blue;">first looks at its own records to resolve the name</mark>. <mark style="background-color:blue;">If it is unable</mark> to resolve the name using its stored records, it <mark style="background-color:blue;">contacts other servers to resolve the name</mark>. After a match is found and returned to the original requesting server, the server temporarily stores the numbered address in the event that the same name is requested again.

The DNS Client service on Windows PCs also stores previously resolved names in memory. The <mark style="background-color:blue;">ipconfig /displaydns command displays all of the cached DNS entries</mark>.

***

## Dynamic Host Configuration Protocol

<figure><img src=".gitbook/assets/image (97).png" alt=""><figcaption><p>Dynamic Host Configuration Protocol</p></figcaption></figure>

* Computers need network addresses to communicate over a network.&#x20;
* Additional crucial information includes gateway address, subnet mask, and DNS server.&#x20;
* Manually configuring end devices is not scalable. <mark style="background-color:blue;">DHCP allows for automated distribution of network information.</mark>&#x20;
* DHCP-distributed addresses are leased for a set period of time.&#x20;
* Addresses are returned to the pool of addresses for reuse when no longer in use.&#x20;
* DHCP supports IPv4 and DHCPv6 supports IPv6.

## DHCP Operation

<figure><img src=".gitbook/assets/image (98).png" alt=""><figcaption><p>DHCP Operation</p></figcaption></figure>

The **Dynamic Host Configuration Protocol (DHCP)** for IPv4 service automates the assignment of <mark style="background-color:blue;">IPv4 addresses, subnet masks, gateways, and other IPv4 networking parameters</mark>. This is referred to as **dynamic addressing**. The alternative to dynamic addressing is **static addressing**. When using static addressing, the network administrator <mark style="background-color:blue;">manually enters IP address information on hosts</mark>.

A DHCP client goes through the following basic steps to request an IP:&#x20;

1. The client broadcasts a **DHCPDISCOVER**.&#x20;
2. A DHCP server replies with a **DHCPOFFER** message&#x20;
3. The client sends a **DHCPREQUEST** message to the server it wants to use (in case of multiple offers).

{% hint style="info" %}
When an IPv4, DHCP-configured device boots up or connects to the network, the <mark style="background-color:blue;">client broadcasts a</mark> <mark style="background-color:blue;"></mark><mark style="background-color:blue;">**DHCP discover (DHCPDISCOVER)**</mark> <mark style="background-color:blue;"></mark><mark style="background-color:blue;">message to identify any available DHCP servers on the network</mark>. A DHCP server replies with a **DHCP offer (DHCPOFFER)** message, which offers a lease to the client. The offer message contains the IPv4 address and subnet mask to be assigned, the IPv4 address of the DNS server, and the IPv4 address of the default gateway. The lease offer also includes the duration of the lease.

The client may receive multiple DHCPOFFER messages if there is more than one DHCP server on the local network. Therefore, it must choose between them, and sends a **DHCP request (DHCPREQUEST)** message that identifies the explicit server and lease offer that the client is accepting. A client may also choose to request an address that it had previously been allocated by the server.
{% endhint %}

Assuming that the IPv4 address requested by the client, or offered by the server, is still available, the server returns a **DHCP acknowledgment (DHCPACK)** message that acknowledges to the client that <mark style="background-color:blue;">the lease has been finalized</mark>. If <mark style="background-color:blue;">the offer is no longer valid</mark>, then the selected server responds with a **DHCP negative acknowledgment (DHCPNAK)** message. <mark style="background-color:blue;">If a DHCPNAK message is returned, then the selection process must begin again with a new DHCPDISCOVER message being transmitted</mark>. After the client has the lease, it must be renewed prior to the lease expiration through another DHCPREQUEST message.

The DHCP server ensures that <mark style="background-color:blue;">all IP addresses are unique</mark> (the same IP address cannot be assigned to two different network devices simultaneously). Most Internet providers use DHCP to allocate addresses to their customers.

***

## File Transfer Protocol

<figure><img src=".gitbook/assets/image (99).png" alt=""><figcaption><p>File Transfer Protocol</p></figcaption></figure>

* FTP was developed to allow the transfer of files over the network.&#x20;
* An FTP client is an application that runs on a client computer used to push and pull data from an FTP server.&#x20;
* FTP requires two connections between the client and the server: one connection for <mark style="background-color:blue;">commands and replies</mark> and another connection for the <mark style="background-color:blue;">actual file transfer</mark>.&#x20;
* The client initiates and establishes the first connection to the server for control traffic on TCP port 21.&#x20;
* The client then establishes the second connection to the server for the actual data transfer on TCP port 20.&#x20;
* The client can download (pull) data from the server or upload (push) data to the server.
