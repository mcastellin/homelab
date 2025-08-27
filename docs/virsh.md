# Virsh Cheatsheet

Running a new virtual machine:
```
virt-install --name ubuntu2004 --ram 2048 --disk path=/var/lib/libvirt/images/ubuntu2004.qcow2,size=20 --vcpus 2 --os-type linux --os-variant ubuntu20.04 --network network=default --graphics none --console pty,target_type=serial --location 'http://archive.ubuntu.com/ubuntu/dists/focal/main/installer-amd64/' --extra-args 'console=ttyS0,115200n8 serial'
```

Connecting to running VM:
```
virsh --connect qemu:///system console <guest-name>
```

**Troubleshooting console connections**
```
sudo apt install libguestfs-tools
sudo virt-edit -d myVM /boot/grub/grub.cfg
```

Replace all occurrences of `quiet` with `quiet console=ttyS0` and restart the virtual machine.

Additional information in [this thread](https://unix.stackexchange.com/questions/288344/accessing-console-of-ubuntu-16-04-kvm-guest).
