Engineering Egress with Edge Fabric
===================================
## Steering Oceans of Content to the World

It's about Peering-/Edge- Routers that connect Facebook's Points of Presence to Peers/IXPs/Transit.
![](PoP.png)
The set opf these routers across all Points of Presence is generaly referred to as *the edge*.

The authors write about a §system that allows them to centrally control these routers and, by that, have better control over traffic flows that leave theire AS (egress traffic).

The system aims to enable capacity aware egress decisions on top of BGP. This is to avoid different types of congestion.

Thereby Facebook uses interdomain connectivity to improve their performanc. That's also something we want to achieve with the programmable route server.

---

The challenges that large content providers face on theire edge include:

**Congested ports**  
Ports on a router (which connect to a Peer/IXP/Transit) have limited capacity in bit/s. As BGP is not capacity aware, a router that solely relies on BGP to make forwarding decisions, may congest ports§. If a port congests, packets are being queued, which increases latency and decreases bandwidth for all transmissions that pass this port.

**Congested paths**  
The authors also mention *congested paths*. Meaning that ports on some router (in a different AS) may congest and therefore throttle the transmission. This phenomenon is also known as *downstream congestion*. The authors present a real-time meausurement method for path performance in theire paper.

Congestion also leads to packet loss, which causes an increase of server load due to retransmission.

**The authors recorded a dataset with following attributes to understand the scale of the link congestion problem**  

| Time | Egress in bit/s | PoP ID | Prefix | (Prefix-) Link capacity |
| ---- | --------------- | ------ | ------ | ----------------------- |

**They visualised the data and could draw following conclusions**
- Most pops have at least one prefix congested
- A small fraction of PoPs is congested for most prefixes.
- Most interfaces (links) are only slightly overloaded
- About 10% of interfaces experience a period where BGP assigns twice as much traffic as the capacity.

**'AS path length serves as an imperfect heuristic for proximity and performance'**  
To understand the severity of this problem, the authors conducted performance measurements on alternative paths.  
They came to following conclusions:
- 5% of <PoP, Prefix> pairs could see an improvement of 20+ms by choosing the second preference.
- 3% could see an improvement if switched to BGP's third preference.
- The second preference is within 20ms for 74%. Therefore the second preference still imposes a good choice and could be selected for load balancing purposes.

---


---

The authors present a system with following key functions:

**Can overwrite BGP's best path selection**  

---

The authors present a system with following key features:

**Performance- and capacity-awareness**  

**Near real-time performance**  

---

The authors also show in their paper the network connectivity and traffic characteristics that 'make it challenging to manage egress trafiic'. Problems originate especially from the required BGP compatibility. Those are the following:

**Rapid growth in number of PoPs**  

**Rapid growth in traffic volume**  
An edge routers link capacity may not be suffice to deliver all traffic that Facebook would like to send over it.
Just increasing port capacity would be inefficient as traffic is highly volatile (peaks occour) and upgrading ports can take months. Therefore there is also the risk of *poor utilization*.

---

Points of Presence
=================
![](PoP.png)
Points of Presence (PoP) are globally distributed servers and network components (see pic). Their main purpose is to reduce latencies of internet applications.

**PoPs reduce traffic in two ways:**  

1. 'They cache content to serve user requests directly.' By serving user requests, from a PoP, the latency is reduced as the request passes less hops.

2. 'When a user needs to communicate with a data center, the users TCP Connection terminates at the PoP'. This reduces latency in two ways: First, the TLS (Transport Layer Security) negotiation, which involves several round trips, is performed between geographically near endpoints. And second because Facebook can impose specialised mechanisms§ (like handling packet loss) on the long distance transmission if these happen on theire private network.

**Request-routing**  

The PoPs described in the Edge Fabric paper(§) use [DNS Request-routing](#CDN Request-routing). A load balacer decides based on user-sided connectivity measurements which PoP to route the request to. Usually a user network will contain to a single PoP during one day.


---

CDN Request-routing
===================

Three types are listed by Wichtluhuber(§):

1. DNS Request-routing

2. HTTP Request-routing

3. Anycast Request-routing

---

Interdomain Connectivity
========================

[Peering-/Edge-routers](#Edge Router) connect to other ASes via different types of connections:

**Private Peering**  
Router connects to peer via a dedicated [PNI](#Private Network Interconnect)

**Public Peering**  
Router exchanges BGP announcements and connects via the shared fabric of an [IXP](#IXP)

**Transit**  
'Transit providers provide routes to all prefixes via a [PNI](#Private Network Interconnect) with dedicated capacity just for traffic between the customer AS (Facebook) and the provider'

**Route Server Peering**  
Router receives BGP announcements indirectly via a [route server](#Route Server) and exchanges traffic across the IXP fabric.

**Traffic share over interconnection types for Facebook PoPs**  
From the table in the edge fabric paper we can see that most traffic is usually exchanged via private peering. Most connections to peers are of the public peering type though. From this difference I ponder, that there must be something about the private peers that makes them more suitable to route egress traffic to them. Probably the eyeball networks all have a private peering and there are just more requests from private peering networks. I wonder why public peering does not directly imply a route server connection.

**A PoP may maintain multiple BGP peering sessions with the same AS**  
For example private + public peering.
Facebooks PoPs also connect to 2+ transit providers and each transit provider is connected to 2+ edge routers for capacity and failure resilience.

The authors write that their preference by connection type in paths for the same AS is as follows: private peers > public peers > route
server.
Facebooks preference of peer over transit comes from the fact that peers expect facebook traffic via peering link and it was found that peer routes generally perform better and have lower risk of *downstream congestion*.
Preference of private over public peering comes from respecting that the peer dedicated resources to receive traffic from facebook. Also to avoid *cross congestion* (§What do they mean by this?).

If there are multiple shortest paths, facebook edge routers distribute traffic across all of them.

---

Edge Router
===========
![](EdgeRouter.png)
