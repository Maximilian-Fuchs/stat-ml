Engineering Egress with Edge Fabric
===================================
## Steering Oceans of Content to the World

It's about Peering-/Edge- Routers that connect Facebook's Points of Presence to Peers/IXPs/Transit.
![](PoP.png)
The set opf these routers across all Points of Presence is generaly referred to as *the edge*.

The authors write about a §system that allows them to centrally control these routers and, by that, have better control over traffic flows that leave theire AS (egress traffic). 

---

The challenges that large content providers face on theire edge include:

**Congested ports**  
Ports on a router (which connect to a Peer/IXP/Transit) have limited capacity in bit/s. As BGP is not capacity aware, a router that solely relies on BGP to make forwarding decisions, may congest ports§. If a port congests, packets are being queued, which increases latency and decreases bandwidth for all transmissions that pass this port.

**Congested paths**  
The authors also mention *congested paths*. Meaning that ports on some router (in a different AS) may congest and therefore throttle the transmission. The authors present a real-time meausurement method for path performance in theire paper.

---
The authors present a system with following key functions:

**Can overwrite BGP's best path selection**

---

The authors present a system with following key features:

**Performance- and capacity-awareness**


**Near real-time performance**

---

The authors also show in their paper the network connectivity and trafiic characteristics that 'make it challenging to manage egress trafiic'. Those are the following:

**as**

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




---

Edge Router
===========
![](EdgeRouter.png)

