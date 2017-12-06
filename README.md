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

# Cleanup
```bash
virsh list --all

VM_NAME=juju

# get VMs storage files
virsh dumpxml --domain $VM_NAME | grep 'source file'

# graceful shutdown
virsh shutdown --domain $VM_NAME

# forceful shutdown
virsh destroy --domain $VM_NAME

# delete VM
virsh undefine --domain $VM_NAME

# remove storage file (see above)
rm -rf /home/team/dev/vms/$VM_NAME.img
```

# Resources
https://help.ubuntu.com/community/KVM/Installation
https://www.cyberciti.biz/faq/howto-linux-delete-a-running-vm-guest-on-kvm/