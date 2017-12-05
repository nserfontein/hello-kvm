# Install KVM on Ubuntu 16.04
```bash
# checklist
egrep -c '(vmx|svm)' /proc/cpuinfo
uname -m

sudo apt-get install -y qemu-kvm libvirt-bin ubuntu-vm-builder bridge-utils
sudo adduser `id -un` libvirtd
# relogin
groups

# confirm
kvm-ok
virsh list --all
sudo ls -la /var/run/libvirt/libvirt-sock
ls -l /dev/kvm

sudo chown root:libvirtd /dev/kvm
# relogin
```

#  Install virt-manager (GUI)
```bash
sudo apt-get install -y virt-manager
sudo rmmod kvm_intel
sudo rmmod kvm
sudo modprobe kvm
sudo modprobe kvm_intel
```
- Open "Virtual Machine Manager"
- File > Add > Connection > QEMU/KVM

# Resources
https://help.ubuntu.com/community/KVM/Installation