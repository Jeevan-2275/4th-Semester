# CIA2 Exam Master MCQ Question Bank - Computer Networks (CN)

**Subject:** Computer Networks  
**Pattern:** Multiple Choice Questions (MCQs) with Detailed Explanations  
**Coverage:** 100% Exhaustive Topic Coverage across ALL Units (Units 1 to 5)  

---

## 🌐 Unit 1 & 2: Models, Topologies, Switching & Data Link Protocols

#### Q1. Which layer of the OSI model is responsible for end-to-end process-to-process communication, port addressing, flow control, and error recovery?
- (A) Network Layer
- (B) Data Link Layer
- (C) Transport Layer
- (D) Session Layer
**Answer:** (C) Transport Layer  
**Explanation:** The Transport layer manages process-to-process communication using port numbers (e.g., TCP/UDP ports) and guarantees reliable segment delivery.

#### Q2. In a Mesh topology with $N$ network devices, how many physical duplex links are required to connect all devices directly?
- (A) $N - 1$
- (B) $N(N - 1)$
- (C) $\frac{N(N - 1)}{2}$
- (D) $2^N$
**Answer:** (C) $\frac{N(N - 1)}{2}$  
**Explanation:** In a fully connected mesh, every node connects to every other node. Each link connects 2 nodes $\implies \frac{N(N-1)}{2}$ links.

#### Q3. Which switching technique breaks messages into fixed or variable packets and routes each packet independently through the network without reserving dedicated bandwidth?
- (A) Circuit Switching
- (B) Datagram Packet Switching
- (C) Virtual Circuit Packet Switching
- (D) Message Switching
**Answer:** (B) Datagram Packet Switching  
**Explanation:** Datagram packet switching treats each packet independently, routing them dynamically over different paths without prior resource reservation.

#### Q4. In Go-Back-N ARQ, if the sender's window size is $W = 7$ (using 3-bit sequence numbers $0 \dots 7$), what happens if frame 3 is lost during transmission?
- (A) The receiver buffers frames 4, 5, 6 and requests only frame 3.
- (B) The sender retransmits frames 3, 4, 5, 6, 7 upon timer expiration.
- (C) The sender retransmits only frame 3 (Selective Repeat behavior).
- (D) The connection resets automatically.
**Answer:** (B) The sender retransmits frames 3, 4, 5, 6, 7 upon timer expiration.  
**Explanation:** In Go-Back-N, the receiver discards all out-of-order frames after a lost frame. The sender must retransmit the lost frame and all subsequent unacknowledged frames in the window.

#### Q5. What is the maximum receiver window size $W_R$ allowed in Selective Repeat ARQ when using $m$-bit sequence numbers?
- (A) $2^m$
- (B) $2^m - 1$
- (C) $2^{m-1}$
- (D) $1$
**Answer:** (C) $2^{m-1}$  
**Explanation:** To prevent window overlap and ambiguity between new frames and retransmitted frames, the window size in Selective Repeat must satisfy $W_S = W_R \le 2^{m-1}$.

#### Q6. What is the physical address length of an Ethernet MAC address?
- (A) 32 bits (4 bytes)
- (B) 48 bits (6 bytes)
- (C) 64 bits (8 bytes)
- (D) 128 bits (16 bytes)
**Answer:** (B) 48 bits (6 bytes)  
**Explanation:** MAC addresses are 48-bit (6-byte) hexadecimal numbers uniquely assigned by IEEE and hardware vendors.

#### Q7. Which transmission mode allows communication in both directions simultaneously (e.g., telephone conversation)?
- (A) Simplex
- (B) Half-Duplex
- (C) Full-Duplex
- (D) Multiplex
**Answer:** (C) Full-Duplex  
**Explanation:** Full-duplex mode allows data transmission in both directions concurrently. Half-duplex allows both directions but one at a time (e.g., walkie-talkie); Simplex is one-way only.

#### Q8. In Frequency Division Multiplexing (FDM), what is inserted between adjacent sub-carrier signal channels to prevent cross-talk interference?
- (A) Guard Bands
- (B) Time Slots
- (C) Checksums
- (D) Preamble bits
**Answer:** (A) Guard Bands  
**Explanation:** Guard bands are unused frequency strips separating allocated channels in FDM to prevent signal overlap and cross-talk.

---

## 📡 Unit 3 & 4: Transmission Media, IP Addressing, Routing & Error Control

#### Q9. What is the network address and broadcast address for the IP address `192.168.10.45/27`?
- (A) Network: `192.168.10.0`, Broadcast: `192.168.10.31`
- (B) Network: `192.168.10.32`, Broadcast: `192.168.10.63`
- (C) Network: `192.168.10.32`, Broadcast: `192.168.10.255`
- (D) Network: `192.168.10.40`, Broadcast: `192.168.10.64`
**Answer:** (B) Network: `192.168.10.32`, Broadcast: `192.168.10.63`  
**Explanation:** `/27` has a block size of $256 - 224 = 32$. Subnet boundaries are `0..31`, `32..63`, etc. For IP `.45`, the network address is `.32` and the broadcast address is `.63`.

#### Q10. Which routing protocol uses the Bellman-Ford Distance Vector algorithm and limits paths to a maximum of 15 hops?
- (A) OSPF
- (B) BGP
- (C) RIP (Routing Information Protocol)
- (D) IS-IS
**Answer:** (C) RIP (Routing Information Protocol)  
**Explanation:** RIP is a Distance Vector routing protocol with a hop limit of 15; 16 hops represents infinity (unreachable).

#### Q11. Which interior gateway routing protocol uses Dijkstra's Shortest Path First (SPF) algorithm and Link-State Advertisements (LSAs)?
- (A) RIP
- (B) OSPF
- (C) BGP
- (D) EGP
**Answer:** (B) OSPF  
**Explanation:** OSPF (Open Shortest Path First) is a link-state routing protocol that builds a complete topology map of the area and executes Dijkstra's algorithm to compute shortest paths.

#### Q12. To detect and correct a single-bit error using Hamming Code on a $d$-bit dataword with $p$ parity bits, what inequality must be satisfied?
- (A) $2^p \ge d + p + 1$
- (B) $2^p \le d + p$
- (C) $p^2 \ge d + 1$
- (D) $2^d \ge p + 1$
**Answer:** (A) $2^p \ge d + p + 1$  
**Explanation:** $2^p$ states must be sufficient to indicate all $d + p$ bit error positions plus the no-error state ($+1$).

#### Q13. In Cyclic Redundancy Check (CRC), if the generator polynomial $G(x) = x^3 + x + 1$ (binary `1011`), how many 0 bits must be appended to the dataword before division?
- (A) 4 bits
- (B) 3 bits
- (C) 2 bits
- (D) 1 bit
**Answer:** (B) 3 bits  
**Explanation:** If the generator polynomial has degree $k = 3$ (length 4 bits), exactly $k = 3$ zeros are appended to the dataword before modulo-2 division.

#### Q14. Which fiber optic connector features a push-pull latching mechanism and is widely used in Fast Ethernet / Gigabit datacenter links?
- (A) BNC Connector
- (B) RJ-45 Connector
- (C) SC (Subscriber Connector) / LC (Lucent Connector)
- (D) F-Type Connector
**Answer:** (C) SC (Subscriber Connector) / LC (Lucent Connector)  
**Explanation:** SC and LC are square push-pull optical fiber connectors. BNC is coaxial; RJ-45 is copper UTP.

#### Q15. Which field in the IPv4 header prevents packets from circulating endlessly in routing loops by being decremented by 1 at each router hop?
- (A) Version
- (B) Type of Service (ToS)
- (C) Time To Live (TTL)
- (D) Header Checksum
**Answer:** (C) Time To Live (TTL)  
**Explanation:** Every router that forwards an IPv4 datagram decrements its TTL field by 1. When TTL reaches 0, the router drops the packet and sends an ICMP Time Exceeded message back.

#### Q16. Which network device operates at OSI Layer 2 (Data Link Layer) and uses a MAC address table to forward frames selectively to specific destination ports?
- (A) Hub
- (B) Repeater
- (C) Switch
- (D) Router
**Answer:** (C) Switch  
**Explanation:** Switches operate at Layer 2, maintaining a MAC address table to forward frames only to the port where the destination MAC resides. Hubs (Layer 1) broadcast to all ports.

---

## 🔒 Unit 5: Application Protocols, Security & CLI Diagnostic Tools

#### Q17. What is the primary difference between TCP and UDP headers?
- (A) TCP header is fixed at 8 bytes; UDP header is variable (20-60 bytes).
- (B) TCP header is 20–60 bytes with Sequence/Ack numbers; UDP header is fixed at 8 bytes without connection tracking.
- (C) UDP contains port numbers while TCP does not.
- (D) TCP uses IP addresses in its header; UDP does not.
**Answer:** (B) TCP header is 20–60 bytes with Sequence/Ack numbers; UDP header is fixed at 8 bytes without connection tracking.  
**Explanation:** TCP provides reliable, connection-oriented service with a 20–60 byte header. UDP provides lightweight, connectionless service with a minimal 8-byte header.

#### Q18. Which CLI command uses ICMP Echo Requests and Time-To-Live (TTL) expiration messages to map out the hop path to a destination host?
- (A) `ping`
- (B) `netstat`
- (C) `traceroute` / `tracert`
- (D) `nslookup`
**Answer:** (C) `traceroute` / `tracert`  
**Explanation:** `traceroute` sends packets with incrementing TTL values ($1, 2, 3 \dots$). Intermediate routers discard the packet when TTL hits 0 and send ICMP Time Exceeded messages back, revealing each hop.

#### Q19. Which Application Layer protocol operates over TCP ports 20 and 21, using port 21 for control commands and port 20 for data transfer?
- (A) HTTP
- (B) SMTP
- (C) FTP (File Transfer Protocol)
- (D) TFTP
**Answer:** (C) FTP (File Transfer Protocol)  
**Explanation:** FTP uses dual TCP connections: Port 21 for out-of-band control commands and Port 20 for active data transfer.

#### Q20. What type of firewall inspects stateful connection tables, tracking TCP 3-way handshakes, sequence numbers, and packet flags across sessions?
- (A) Packet Filtering Firewall
- (B) Stateful Inspection Firewall
- (C) Circuit-Level Gateway
- (D) Application Proxy Firewall
**Answer:** (B) Stateful Inspection Firewall  
**Explanation:** Stateful inspection firewalls maintain a dynamic connection state table to ensure incoming traffic matches legitimate, established outgoing sessions.

#### Q21. In the Domain Name System (DNS), which Resource Record (RR) type maps a domain name directly to an IPv6 128-bit address?
- (A) A Record
- (B) CNAME Record
- (C) AAAA Record
- (D) MX Record
**Answer:** (C) AAAA Record  
**Explanation:** `A` records map hostname to IPv4 (32-bit); `AAAA` records map hostname to IPv6 (128-bit). `MX` is Mail Exchange; `CNAME` is Canonical Name alias.

#### Q22. Which protocol is used by email clients to retrieve messages from a mail server while synchronizing folder states across multiple devices?
- (A) SMTP (Port 25)
- (B) POP3 (Port 110)
- (C) IMAP (Port 143)
- (D) SNMP (Port 161)
**Answer:** (C) IMAP (Port 143)  
**Explanation:** IMAP leaves messages on the server and synchronizes folder state across devices. POP3 downloads messages to a single local device. SMTP transfers mail between servers.

#### Q23. What is the TCP 3-way handshake sequence executed when establishing a reliable connection between a client and server?
- (A) SYN $\to$ SYN-ACK $\to$ ACK
- (B) FIN $\to$ ACK $\to$ FIN-ACK
- (C) RST $\to$ SYN $\to$ ACK
- (D) ACK $\to$ SYN $\to$ SYN-ACK
**Answer:** (A) SYN $\to$ SYN-ACK $\to$ ACK  
**Explanation:** Client sends SYN to request connection; Server responds with SYN-ACK; Client sends ACK to establish full-duplex TCP session.

---
