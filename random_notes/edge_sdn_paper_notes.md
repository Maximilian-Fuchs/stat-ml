Engineering Egress with Edge Fabric
===================================
## Steering Oceans of Content to the World

It's about Peering-/Edge- Routers that connect Facebook's Points of Presence to Peers/IXPs/Transit.
![](PoP.png)
The set opf these routers across all Points of Presence is generaly referred to as *the edge*.

The authors write about a §System allows them to centrally control these routers and, by that, have better control over the traffic flows that leave theire AS.

---

The challenges that large content providers face on theire edge include:

**Congested ports**
Ports on a router (which connect to a Peer/IXP/Transit) have limited capacity in bit/s. As BGP is not capacity aware, a router that solely relies on BGP to make forwarding decisions, may congest ports§. If a port congests, packets are being queued, which increases latency and decreases bandwidth for all transmissions that pass this port.

**Congested paths**
The authors also mention *congested paths*. Meaning that ports on some router (in a different AS) may congest and therefore throttle the transmission. The authors present a real-time meausurement method for path performance in theire paper.

---

The authors present a system with following key features:

**Near real-time performance**


**asd**

Points of Presence
=================
![](PoP.png)
Points of Presence (PoP) are globally distributed servers and network components (see pic). Their main purpose is to reduce latencies of internet applications.

The Paper goes into detail about how PoPs provide value to their (traffics performance§).

---
