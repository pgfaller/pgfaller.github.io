---
layout: page
---

## Keeping path and environment

One way to maintain environment variables, especially PATH, is to use the _exempt_group_ setting. It can be added into /etc/sudoers.d by means of:

```
$ sudo visudo -f /etc/sudoers.d/00-vars
$ ls -l /etc/sudoers.d
total 8
-r--r----- 1 root root  30 Jun 21 18:13 00-vars
-r--r----- 1 root root 958 Mar 30  2016 README
$ sudo cat /etc/sudoers.d/00-vars
Defaults exempt_group = wheel
```
