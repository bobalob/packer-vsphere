# ubuntu-vmware

Basic build template and script for packer vsphere-iso. See [my blog post](https://blog.superautomation.co.uk/2023/03/ubuntu-with-packer-on-vsphere.html) for more information.

Create a new file called variables.auto.pkvars.hcl and add the following

```
temp_dns = "192.168.2.254"
temp_gw = "192.168.2.254"
temp_ip = "192.168.2.90"
temp_mask = "255.255.255.0"
vcenter_cluster = "mycluster.domain.local"
vcenter_datacenter = "Home"
vcenter_datastore = "Datastore1"
vcenter_iso_path = "[Datastore1] ISO/ubuntu-22.04.1-live-server-amd64.iso"
vcenter_network = "VM network"
vcenter_server = "vcenter.domain.local"
vcenter_user = "administrator@vsphere.local"
ssh_authorized_keys = [
    "ssh-rsa AAAAB3NzaC1... user@box1",
    "ssh-rsa AAAAB3NzaC1... user@box2"
]
```

The temporary IP is because in my environment, the machine would get a different DHCP assigned address after reboot and packer would not reconnect to the new IP.

Build with ```./build.sh <hostname> <username> <initial-password>```
