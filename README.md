# ubuntu-cloud-vsphere

## govc installation and configuration

```
wget https://github.com/vmware/govmomi/releases/download/v0.30.7/govc_Linux_x86_64.tar.gz
tar -C .local/bin -xvf govc_Linux_x86_64.tar.gz govc

info@penguin:~/ubuntu-cloud-vsphere$ grep GOVC ~/.bashrc
GOVC_INSECURE=1
GOVC_USERNAME="myusername@mydomain.lan"
GOVC_PASSWORD="mypassword"
GOVC_URL="https://vcenterge.mydomain.lan:443/sdk"
GOVC_NETWORK="/Datacenter GE/network/VLAN14-Server"
GOVC_DATASTORE="/Datacenter GE/datastore/ISO"
GOVC_RESOURCE_POOL="/Datacenter GE/host/Cluster_Test/Resources"
export GOVC_INSECURE GOVC_USERNAME GOVC_PASSWORD GOVC_URL GOVC_NETWORK GOVC_DATASTORE GOVC_RESOURCE_POOL
```

## Useful links

[GOVC Usage](https://github.com/vmware/govmomi/blob/main/govc/USAGE.md)

[Ubuntu 22.04 Cloud Image OVA](https://cloud-images.ubuntu.com/releases/releases/22.04/release/ubuntu-22.04-server-cloudimg-amd64.ova)

[Ubuntu 22.04 OVA Cloud Image does not get a DHCP IPv4 address in vSphere](https://askubuntu.com/questions/1408621/ubuntu-22-04-ova-cloud-image-does-not-get-a-dhcp-ipv4-address-in-vsphere)
[Setting up a base template - Create Ubuntu 18.04 LTS Template](https://hewlettpackard.github.io/simplivity-vsphere-csi-driver/driver-deployment/prerequisites-deployment/setup-base-template/)
[Using cloud-init for VM templating on vSphere](https://blah.cloud/infrastructure/using-cloud-init-for-vm-templating-on-vsphere/)
[unable to set network when using govc import.ova](https://github.com/vmware/govmomi/issues/460)
[Cloud config examples](https://cloudinit.readthedocs.io/en/latest/reference/examples.html)

# Extracting OVF Spec in JSON format from Cloud Image

```
cd ~/Downloads && wget https://cloud-images.ubuntu.com/releases/releases/22.04/release/ubuntu-22.04-server-cloudimg-amd64.ova && cd -
govc import.spec ~/Downloads/ubuntu-22.04-server-cloudimg-amd64.ova | jq . > 2204.json
```
