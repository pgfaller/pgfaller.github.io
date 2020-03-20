---
layout: page
---

## Enable screen brightness control in Ubuntu

Edit /etc/default/grub:
```
$ sudo vi /etc/default/grub
```
Change the line:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
```
and then run:
```
$ sudo update-grub
```
