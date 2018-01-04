# zabbix-openvpn

Script for OpenVPN users monitoring.  
It shows an OpenVPN user’s status, and its uplink and downlink traffic.  
The "items" by the files certificates names are made using LLD.

#### Supported versions
 - Zabbix 3.0
 - Zabbix 4.0

## Setup

1. On the OpenVPN server, copy the scripts to any directory, for example `/etc/zabbix/scripts`:
```console
$ mkdir /etc/zabbix/sripts
$ cp *.sh /etc/zabbix/scripts
$ chmod +x /etc/zabbix/scripts/*.sh
```
Customize `/etc/zabbix/scripts/discover_vpn.sh` specifing the path to directory where OpenVPN certificates are (line #3).
2. Copy `userparameter_openvpn.conf` into Zabbix agent configuration directory:
```console
$ cp userparameter_openvpn.conf /etc/zabbix/zabbix_agentd.d/
```
The items defined read informations from OpenVPN logs, so:
 - ensure openvpn log paths are correct;
 - ensure log files are readable from `zabbix` user;
 - ensure SELinux permit to `zabbix` user read those files.

3. On the Zabbix server, import `openvpn.xml` template and assign it to the OpenVPN server.
