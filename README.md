# unbound-nagios-plugins
Nagios Plugins for the DNS application Unbound

User configuration

Topology:

 ________________					          ________________
| Nagios Server  | ----- NRPE ---- | Unbound Server |
 ________________					          ________________
 
 Unbound side:

- Get the plugin (and put it on /usr/lib/nagios/plugins/)

`$ wget ABCDE.org`


- Set the execution permission


`$ sudo chmod +x /usr/lib/nagios/plugins/check_unbound.py`

- Install Nagios NRPE server

`$ sudo apt-get install nagios-nrpe-server`


- Edit the nrpe configuration (/etc/nagios/nrpe.cfg)

`nrpe_user=nrpeuser`


- Execute the command visudo as root and add the following lines:

`nrpeuser    ALL=(root)  NOPASSWD: /usr/lib/nagios/plugins/check_unbound.py ""`

`nrpeuser    ALL=(root)  NOPASSWD: /usr/sbin/unbound-control`


- Restart NRPE service:

`$ sudo service nagios-nrpe-server restart`
