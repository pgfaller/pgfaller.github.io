---
layout: page
---

# Networking

Contents:

- [OSPF](ospf/)
- [EIGRP](eigrp/)
- [BGP](bgp/)
- [Useful Links](links/)

## Administrative Distance

| Protocol       | Administrative Distance | Metric            |
| :------------- | ----------------------: | :---------------- |
| Connected      |                       0 | --                |
| Static         |                       1 | --                |
| eBGP           |                      20 | Path Vector       |
| EIGRP          |                      90 | Bandwidth + Delay |
| IGRP           |                     100 | (Obsolete)        |
| OSPF           |                     110 | Bandwidth         |
| IS-IS          |                     115 | Varies            |
| RIP            |                     120 | Hop Count         |
| EIGRP external |                     170 | (Static route)    |
| iBGP           |                     200 | Path Vector       |

Routers add the route with the lowest AD to the routing table.
If more than one route to the same destination, add route with the lowest metric.
Add all routes with equal cost (and load-balance).
