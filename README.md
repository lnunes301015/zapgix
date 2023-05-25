# zapgix
Repositório para monitoramento de banco de dados PostgreSQL
zapgix

PostgreSQL Monitoring

This script is part of a monitoring solution that allows to monitor several services and applications.

For more information about this monitoring solution please check out this post on my site.


Dependencies


Packages

- ksh
- sudo

Debian/Ubuntu

#~ sudo apt install ksh sudo
#~

Red Hat

#~ sudo yum install ksh sudo
#~

Deploy


PostgreSQL

We may need to enable some extensions.

sudo -u postgres psql

postgres=# CREATE EXTENSION pg_buffercache;
CREATE EXTENSION
postgres=# \dx pg_buffercache
List of installed extensions
Name | Version | Schema | Description
----------------+---------+--------+---------------------------------
pg_buffercache | 1.0 | public | examine the shared buffer cache
(1 row)
postgres=#

Zabbix

Zabbix user has to have sudo privileges.

nano /etc/sudoers.d/zabbix
# Allow the user zabbix to execute any command without password
Defaults:zabbix !requiretty
zabbix ALL=(ALL:ALL) NOPASSWD:ALL

comando: su - zabbix -s /bin/bash
Then you can run the deploy_zabbix script

git clone https://github.com/lnunes301015/Zabbix.git

sudo ./zapgix/deploy_zabbix.sh
sudo systemctl restart zabbix-agent
