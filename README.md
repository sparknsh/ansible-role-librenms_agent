# Ansible Role: LibreNMS Agent

#### Version: 1.1.1

[![](https://img.shields.io/badge/role-sparknsh.librenms_agent-blue.svg)](https://galaxy.ansible.com/sparknsh/librenms_agent)

Development of this project is managed in a private repository then pushed out to [GitLab](https://gitlab.com/sparknsh/ansible-role-librenms_agent) and [GitHub](https://github.com/sparknsh/ansible-role-librenms_agent) when we have a new version for you. If you have any issues please contact [sparknsh](https://www.sparknsh.com/contact?type=issue&name=ansible-role-librenms_agent)

## Role Variables

```yaml
librenms_agent__snmp_ip: 127.0.0.1
librenms_agent__snmp_port: 161

librenms_agent__snmp_community: public

librenms_agent__snmp_user:
librenms_agent__snmp_auth_type: # md5 or sha
librenms_agent__snmp_password:
librenms_agent__snmp_encryption_type: # aes or des
librenms_agent__snmp_encryption:

librenms_agent__snmp_location:
librenms_agent__snmp_contact:
```
Here are the most common settings for SNMP monitoring.

```yaml
librenms_agent__snmp_no_logging: False
```
Not everyone likes logging everything so this variable allows you to no log the snmp information.

```yaml
librenms_agent__mysql_hostname:
librenms_agent__mysql_username:
librenms_agent__mysql_password:
librenms_agent__mysql_port:
```
To monitor MySQL database performance you need to connect to the databse server with the following variables. Be sure to enable mysql under the Check_MK Scripts or SMTP Scripts section

```yaml
librenms_agent__scripts_update: False
```
This variable allows you to always fetch the scrip from the github repo.

#### Agent Local Scripts

```yaml
librenms_agent__agent_local_scripts:
 - apache
 - bind
 - ceph
 - dmi
 - dpkg
 - drbd
 - freeswitch
 - gpsd
 - hddtemp
 - memcached
 - munin
 - mysql
 - nfsstats
 - nginx
 - nginx-python3.py
 - powerdns
 - powerdns-recursor
 - proxmox
 - rocks.sh
 - rpm
 - rrdcached
 - temperature
 - tinydns
 - unbound.sh
```

#### SNMP Scripts

```yaml
librenms_agent__snmp_scripts:
 - apache-stats
 - apache-stats.py
 - apache-stats.sh
 - asterisk
 - bind
 - certificate.py
 - chip.sh
 - dhcp-status.sh
 - distro
 - entropy.sh
 - exim-stats.sh
 - fail2ban
 - fbsdnfsclient
 - fbsdnfsserver
 - freeradius.sh
 - gpsd
 - mailcow-dockerized-postfix
 - mailscanner.php
 - mdadm
 - mysql
 - mysql-stats
 - nfs-stats.sh
 - nginx
 - nginx-python3.py
 - ntp-client
 - ntp-server.sh
 - nvidia
 - osupdate
 - phpfpmsp
 - pi-hole
 - portactivity
 - postfix-queues
 - postfixdetailed
 - postgres
 - powerdns-dnsdist
 - powerdns-recursor
 - powerdns.py
 - puppet_agent.py
 - pureftpd.py
 - raspberry.sh
 - sdfsinfo
 - seafile.py
 - smart
 - unbound
 - ups-apcups
 - ups-apcups.sh
 - ups-nut.sh
 - zfs-freebsd
 - zfs-freebsd.py
 - zfs-linux
```

#### Example

```yaml
librenms_agent__snmp_ip: 0.0.0.0
librenms_agent__snmp_port: 161

librenms_agent__snmp_community: public

librenms_agent__snmp_location: Nashville, TN, US
librenms_agent__snmp_contact: IT Admin

librenms_agent__snmp_no_logging: True

librenms_agent__snmp_scripts:
  - distro
  - ntp-client
  - os-updates
```

## Example Playbook

```yaml
- hosts: all
  vars_files:
    - vars/main.yml
  roles:
     - { role: sparknsh.librenms_agent }
```

## License

MIT

## Author Information

This role was created in 2018 by [sparknsh](https://www.sparknsh.com) at [Rebel Media, Inc.](https://www.rebelmedia.io/)
