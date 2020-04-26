Add disk to LVM

---
layout: page
---

## Add disk to logical volume

```
# vgextend VolGroup00 /dev/sdc
# lvextend -r -l +100%PVS /dev/mapper/VolGroup00-root /dev/sdc
```

- Power off the virtual machine.
- Edit the virtual machine settings and extend the virtual disk size. For more information, see Increasing the size of a virtual disk (1004047).
- Power on the virtual machine.
- Identify the device name, which is by default /dev/sda, and confirm the new size by running the command:

```
# fdisk -l
```

1. Create a new primary partition:
2. Run the command:

```
# fdisk /dev/sda ### (depending the results of the step 4)
```

- Press p to print the partition table to identify the number of partitions. By default there are 2: sda1 and sda2.
- Press _n_ to create a new primary partition.
- Press _p_ for primary.
- Press _3_ for the partition number, depending the output of the partition table print.
- Press Enter two times.
- Press _t_ to change the system's partition ID
- Press _3_ to select the newly creation partition
- Type _8e_ to change the Hex Code of the partition for Linux LVM
- Press _w_ to write the changes to the partition table.
- Restart the virtual machine.

3. Run this command to verify that the changes were saved to the partition table and that the new partition has an *8e* type:

```
# fdisk -l
```

4. Run this command to convert the new partition to a physical volume:

Note: The number for the sda can change depending on system setup. Use the sda number that was created in step 5.

```
# pvcreate /dev/sda3
```

5. Run this command to extend the physical volume:

```
# vgextend VolGroup00 /dev/sda3
```

Note: To determine which volume group to extend, use the command vgdisplay.

6. Run this command to verify how many physical extents are available to the Volume Group:

```
# vgdisplay VolGroup00 | grep "Free"
```

7. Run the following command to extend the Logical Volume:

```
# lvextend -L+#G /dev/VolGroup00/LogVol00
```

Where _#_ is the number of Free space in GB available as per the previous command. Use the full number output from Step 10 including any decimals.

Note: to determine which logical volume to extend, use the command lvdisplay.

8. Run the following command to expand the ext3 filesystem online, inside of the Logical Volume:

```
# ext2online /dev/VolGroup00/LogVol00
```

Note: Use resize2fs instead of ext2online if it is not a Red Hat virtual machine.

9. Run the following command to verify that the / filesystem has the new space available:

```
# df -h /
```
