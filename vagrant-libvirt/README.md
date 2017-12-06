# Installation
```bash
sudo -i

# up to v1.8 supported
wget https://releases.hashicorp.com/vagrant/1.8.7/vagrant_1.8.7_x86_64.deb
dpkg -i vagrant_1.8.7_x86_64.deb ; apt-get -fy install

# confirm Vagrant 1.8.7
vagrant --version

# dependencies
# NEEDED??? sudo apt-get build-dep vagrant ruby-libvirt
apt-get install qemu libvirt-bin ebtables dnsmasq
apt-get install libxslt-dev libxml2-dev libvirt-dev zlib1g-dev ruby-dev

# exit root

vagrant plugin install vagrant-libvirt
```

# Add Box
- Browse https://app.vagrantup.com/boxes/search?provider=libvirt
```bash
vagrant init generic/ubuntu1604
vagrant up --provider=libvirt
```