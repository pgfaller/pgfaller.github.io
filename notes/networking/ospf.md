---
layout: page
---

## OSPF

General OSPF configuration:

- Backbone network is usually area 0
- Area 0 must exist, even in a multi-area network
- Other areas must border on area 0
- Routers advertise networks to neighbours
- Originally class-based, so not CIDR-aware

Cisco OSPF configuration

- Passive interface indicates an interface where no OSPF neighbour is expected
- OSPF process ID is local to the router - no special meaning
- OSPFv3 (for IPv6) is configured on each advertised interface

### Cisco OSPF example

```
interface FastEthernet0/0
 ip address 10.0.0.1 255.255.255.0
 duplex auto
 speed auto
!
interface FastEthernet0/1
 ip address 172.16.0.1 255.255.255.252
 duplex auto
 speed auto
!
router ospf 10
 log-adjacency-changes
 passive-interface FastEthernet0/0
 network 10.0.0.0 0.0.0.255 area 0
 network 172.16.0.0 0.0.0.3 area 0
!
```

### Cisco OSPFv3 (IPv6) example

```
interface FastEthernet0/0
 no ip address
 duplex auto
 speed auto
 ipv6 address 2001:DB8:42:60::1/64
 ipv6 ospf 10 area 0
!
interface Serial0/0/0
 no ip address
 ipv6 address 2001:DB8:99:10::1/64
 ipv6 ospf 10 area 0
!
interface Serial0/1/0
 no ip address
 ipv6 address 2001:DB8:99:12::1/64
 ipv6 ospf 10 area 0
!
ipv6 router ospf 10
 router-id 1.1.1.1
 log-adjacency-changes
 passive-interface FastEthernet0/0
!
```

### Distribute static route

Only required on egress router

```
router ospf 10
 router-id 2.2.2.2
 log-adjacency-changes
 auto-cost reference-bandwidth 10000
 network 10.0.0.4 0.0.0.3 area 0
 network 10.0.0.8 0.0.0.3 area 0
 network 10.0.2.0 0.0.0.255 area 0
 default-information originate
!
```

'default-information originate' will distribute e.g.

```
ip route 0.0.0.0 0.0.0.0 FastEthernet0/0
```
