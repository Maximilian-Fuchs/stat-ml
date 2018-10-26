OSI Model
=========

| Layer | Function |
| ----- | -------- |
| 1: Physical | **Signal representation of bits: sending bit 1 is also received as bit 1** |
| 2: Data Link | **Reliable data transfer between adjacent stations with frames** |
| [3: Network](#Network Layer) | **Connection between end systems** |
| [4: Transport](#Transport Layer) | **Connection from source to destination** |
| 5: Session | **Support a "session over a longer period"** |
| 6: Presentation | **Data presentation independent from the end system** |
| 7: Application | **Application related services** |

---

Network Layer
=============

Functions
---------
- (subnets) with packets
- routing i.e. among others
  - fixed routes / dynamic routes / routes defined during connect
  - congestion control (eventhoug this is usually done by the [transport layer](#Transport Layer))
  - QoS dependent routing (e.g. traffic aware routing)
  - Routing is the process by which a route of a packet from source to destination is determined in a network where potentialy multiple possible routes exist.
- varying subnets, Internetworking
  - Networks can be organized hierarchically and the network layer is used to implement this hierarchy aswell as routing throughout various entities of this hierarchy 
- addressing
- packet sizing
- in broadcast networks this layer often does not exist
- examples: IP, X.25 (connection-oriented)

---

Transport Layer
===============
