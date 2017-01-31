# unbound-nagios-plugins
Nagios Plugins for the DNS application Unbound
User configuration
Topology:

 ________________					          ________________
| Nagios Server  | ----- NRPE ---- | Unbound Server |
 ________________					          ________________
 
 Unbound side:

1. Get the plugin (and put it on /usr/lib/nagios/plugins/)
$ wget ABCDE.org

2. Set the execution permission
$ sudo chmod +x /usr/lib/nagios/plugins/check_unbound.py

3. Install Nagios NRPE server
$ sudo apt-get install nagios-nrpe-server

4. Edit the nrpe configuration (/etc/nagios/nrpe.cfg)
nrpe_user=nrpeuser

5. Execute the command visudo as root and add the following lines:
nrpeuser    ALL=(root)  NOPASSWD: /usr/lib/nagios/plugins/check_unbound.py ""
nrpeuser    ALL=(root)  NOPASSWD: /usr/sbin/unbound-control

6. Restart NRPE service:
$ sudo service nagios-nrpe-server restart
