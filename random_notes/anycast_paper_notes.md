Measurement Methods
-------------------

#### Performace of Internet-wide anycast

##### Metrics
- Geographic proximity
- Load Balance
- Access Latency

##### Dataset
1. Sampled traffic from the sites (replicas) of D-root DNS-Servers
- Includes 20% of traffic at each replica
- Includes every day in 2017
- 30.000 queries per second (summed across all sites) -> 140GB of trace data per day.
- Provides insights into:
    - Client population (§)
    - Client distribution (Geographic distribution?)
    - Load Distribution (§)
    - Load Variance (§)
    - Inter-site traffic variation (§)
- Mind:
    - Not clear if insights are also applicable to other root DNS-Servers
    - No data on client-side latency
    - No insights into alterneate AS paths or other selction policies (What does that mean?§)

2. RIPE Atlas measurements
- Augments the root DNS dataset with active measurements to account for latency and alternative paths.
- Includes periodical (CHAOS) queries and traceroutes from 10000 locations in 180 countries and 3587 ASs to all DNS root servers
    - CHAOS queries usually return a txt that identifies the replica.

3. "Own measurements"
- Augment the ripe atlas measurements to account for alternative paths and addresses ...


-------------------
# Facts (to be filed)

## Replicas of DNS root servers
- Each replica has the same IP address. ([Anycast](#Anycast))
- "Global replicas are advertised using inter-domain BGP, and can be accessed across the Internet"
	- Local replicas are only accessible from within the AS it's located in.
 
