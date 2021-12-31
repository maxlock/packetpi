# PacketPi
Is an ansible configuration that provisions linux AX25 tools on a Raspberry Pi.

# Quick start 
Run the following commands on your Raspberry Pi.

```
git clone https://github.com/maxlock/packetpi
cd packetpi
``` 

At this point you can now run Ansible to configure your Pi.

```
ansible-playbook -i inventory site.yaml
```
