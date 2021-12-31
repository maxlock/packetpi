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

At this point you have a fully operational packet node. You can connect to the netrom node app by telnetting to port 4444

```
pi@raspberrypi:~ $ telnet localhost 4444
Trying ::1...
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.

LinuxNode v0.3.2 (g7uoz-1)

login: g7uoz
#UOZNOD:G7UOZ-1 Welcome to g7uoz-1 network node

Type ? for a list of commands. help <commandname> gives a description
of the named command.

--

?
#UOZNOD:G7UOZ-1 Commands:
?, Bye, Connect, ECho, Escape, Finger, Help, HOst, Info, Links
Mheard, NLinks, Nodes, PIng, Ports, Routes, Status, TAlk, Telnet, TIme
Users, ZConnect, ZTelnet

```
