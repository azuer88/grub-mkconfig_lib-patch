grub-mkconfig_lib-patch
=======================

A simple patch to make update-grub in ubuntu use partition labels instead of UUID

I sometimes find myself changing my partitions once too often.  Depending on UUID sometimes caused conflicts after cloning partitions, or confusion when booting on either the clone or orignal partition.

So I came to depend on labelling my partitions, and using the labels to find the correct partition to use.

This simple patch makes update-grub create the grub.cfg using labels instead of UUID during searching for the root partition to boot.

## Install ##

        # apply the patch
        sudo patch -p0 -i `pwd`/grub-use-labels.patch -d /usr/share/grub
        
        # update grub:
        sudo update-grub2


## Notes ##

I usually also edit /etc/default/grub (root permission required) and uncomment the line 

        GRUB_DISABLE_LINUX_UUID="true"

So GRUB will use LABELs instead of using UUIDs.

I also usually edit /etc/fstab and change UUID=yyy to LABEL=xxx.



