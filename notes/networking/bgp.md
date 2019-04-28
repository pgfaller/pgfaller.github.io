---
layout: page
---

## Cisco BGP Example

Customer side

```
router bgp 65010
 no synchronization
 bgp log-neighbor-changes
 network 203.0.113.16 mask 255.255.255.248
 neighbor 203.0.113.81 remote-as 65042
 no auto-summary
!
```

ISP side

```
router bgp 65042
 no synchronization
 bgp log-neighbor-changes
 network 0.0.0.0
 network 198.19.10.0
 network 203.0.113.88 mask 255.255.255.252
 neighbor 203.0.113.82 remote-as 65010
 no auto-summary
!
```
