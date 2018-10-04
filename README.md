# Ansible Role: LibreNMS Agent

#### Version: 1.0.1

[![pipeline status](https://gitlab.com/sparknsh/ansible-role-librenms-agent/badges/master/pipeline.svg)](https://gitlab.com/sparknsh/ansible-role-librenms-agent/commits/master)
[![Ansible Role](https://img.shields.io/ansible/role/30333.svg)](https://galaxy.ansible.com/sparknsh/librenms_agent)
[![Ansible Role](https://img.shields.io/ansible/role/d/30333.svg)](https://galaxy.ansible.com/sparknsh/librenms_agent)

Development of this project is managed in a private repository then pushed out to [GitLab](https://gitlab.com/sparknsh/ansible-role-librenms-agent) and [GitHub](https://github.com/sparknsh/ansible-role-librenms-agent) when we have a new version for you. If you have any issues please contact [sparknsh](https://www.sparknsh.com/contact?type=issue&name=ansible-role-librenms-agent)

## Role Variables

```yaml
librenms_agent_snmp_ip: 127.0.0.1
librenms_agent_snmp_port: 161

librenms_agent_snmp_community: public

librenms_agent_snmp_user:
librenms_agent_snmp_auth_type: # md5 or sha
librenms_agent_snmp_password:
librenms_agent_snmp_encryption_type: # aes or des
librenms_agent_snmp_encryption:

librenms_agent_snmp_location:
librenms_agent_snmp_contact:
```
Here are the most common settings for SNMP monitoring.

```yaml
librenms_agent_snmp_no_logging: False
```
Not everyone likes logging everything so this variable allows you to no log the snmp information.

```yaml
librenms_agent_snmp_mysql_hostname:
librenms_agent_snmp_mysql_username:
librenms_agent_snmp_mysql_password:
librenms_agent_snmp_mysql_port:
```
To monitor MySQL database performance you need to connect to the databse server with the following variables. Be sure to enable mysql under the Check_MK Scripts or SMTP Scripts section

```yaml
librenms_agent_scripts_update: False
```
This variable allows you to always fetch the scrip from the github repo.

```yaml
librenms_agent_check_mk: False
```
By default Check_MK is not installed without enabled scripts below. If you want to install it without any scripts change this variable to True.

#### Check_MK Scripts

```yaml
librenms_agent_check_mk_scripts:
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
  - powerdns
  - powerdns-recursor
  - proxmox
  - rocks
  - rpm
  - rrdcached
  - temperature
  - tinydns
  - unbound
```

#### SNMP Scripts

```yaml
librenms_agent_snmp_scripts:
  - apache-stats
  - asterisk
  - bind
  - chip
  - dhcp-status
  - distro
  - entropy
  - exim-stats
  - fail2ban
  - fbsdnfsclient
  - fbsdnfsserver
  - freeradius
  - mysql
  - mysql-stats
  - nfs-stats
  - nginx-stats
  - ntp-client
  - ntp-server
  - nvidia
  - os-updates
  - phpfpm-sp
  - pi-hole
  - postfix-queues
  - postfixdetailed
  - postgres
  - powerdns-dnsdist
  - powerdns-recursor
  - raspberry
  - sdfsinfo
  - smart
  - squid
  - unbound
  - ups-apcups
  - ups-nut
  - zfs-freebsd
  - zfs-linux
```

#### Example

```yaml
librenms_agent_snmp_ip: 0.0.0.0
librenms_agent_snmp_port: 161

librenms_agent_snmp_community: public

librenms_agent_snmp_location: Nashville, TN, US
librenms_agent_snmp_contact: IT Admin

librenms_agent_snmp_no_logging: True

librenms_agent_snmp_scripts:
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
