This is an role for installing and maintaining the zabbix-agent.

This role will work on the following operating systems:
 * Debian wheezy
 * Debian jessie

# Role Variables
## mysql variables
* 'mysql_root_password': Password for mysql root user
* 'mysql_zabbix_password': Password for zabbix mysql user

##zabbix-server
* 'server_dbname': Database Name for zabbix-server
* 'server_dbuser': Database user for zabbix-server
* 'server_dbpassword': Database password for zabbix-server
* 'server_include': Inclide dir for servers config

##zabbix-agent
* 'agent_server': Adress of zabbix server (!!!must be specified in playbook!!!)
* 'agent_serveracrive': Adress of zabbix server for active checks (!!!must be specified in playbook!!!)
* 'agent_logfilesize': Max size of zabbix-agent log file
* 'zabbix_url: "http://192.168.21.73/zabbix/"
* 'zabbix_api_user': Name of zabbix api user
* 'zabbix_api_pass': Password for zabbix api user 
* 'zabbix_api_create_hostgroup': Specifies whether to create a group of hosts
* 'zabbix_api_create_hosts: Specifies whether to create a  hosts
* 'zabbix_create_host: Specifie if the host needs to be created or absent
* 'zabbix_create_hostgroup: Specifie if the hostgroup needs to be created or absent
* 'zabbix_host_status: Specifie host status
* 'zabbix_proxy: Specifie proxy using
* 'zabbix_host_groups: Specifie hosygroup for host
* 'zabbix_link_templates: Specifie template for host
* 'agent_interfaces: Specifie interface information for host

## Zabbix API
When you want to automatically create the hosts in the webinterface, you'll need on your own machine the zabbix-api package.
You can install this locally with the following command: `pip install zabbix-api`.

##example playbook

---
- hosts: test-nodes
  sudo: yes
  roles:
    - role: mysql
    - role: zabbix-server
    - role: zabbix-agent
      agent_server: 192.168.21.73
      agent_serveractive: 192.168.21.73
 



