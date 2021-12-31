# PacketPi
Is an ansible configuration that provisions linux AX25 tools on a Raspberry Pi.

# Quick start 
Edit the variables in inventory/hosts.yml, update your callsign and netrom alias
Run the following commands on your Raspberry Pi.

```
apt-get install ansible
git clone https://github.com/maxlock/packetpi
cd packetpi
ansible-galaxy install -r ./requirements.yml -p roles
ansible-playbook -i ./inventory/ site.yml
``` 

At this point you can now run Ansible to configure your Pi.

```
ansible-playbook -i inventory site.yaml
```
