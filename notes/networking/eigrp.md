---
layout: page
---

## Configuration

'no auto-summary' prevents summarisation on class A/B/C boundaries.

## Cisco Example

```
router eigrp 10
 network 10.0.0.4 0.0.0.3
 network 10.0.0.8 0.0.0.3
 network 10.0.2.0 0.0.0.255
 network 10.0.3.0 0.0.0.255
 no auto-summary
!
```

To redistribute static routes:

```
router eigrp 10
 redistribute static
 ...
!
```
