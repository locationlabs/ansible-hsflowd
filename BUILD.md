I've chosen to build the agent from source as they no longer have rpm packages available for later
versions, in particular the version where openvswitch support has been added.

# Requirements
Docker

# Instructions

1. `git clone https://github.com/sflow/host-sflow.git`
  * Then `cd host-sflow`
2. `git checkout v2.0.17-1`
  * This is the current release when this was written
3. ```docker run -it -v `pwd`:/build centos bash```
  * Here we are bind mounting the git repo into the container
4. `yum groupinstall 'Development Tools'` and `yum install libvirt-devel libxml2-devel libpcap-devel dbus-devel openssl-devel`
  * See INSTALL.Linux for this list of dependancies
5. `cd /build && make rpm FEATURES="KVM PCAP OVS SYSTEMD"`
  * INSTALL.KVM only lists the first three features, but I've added SYSTEMD because it would be interesting to see the stats gathered from the various services.
6. Exit the container and enjoy your fresh rpm
7. I then put this file on the repo server so the isolated openstack nodes can fetch it from there
