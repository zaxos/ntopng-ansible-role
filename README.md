[![Ansible Galaxy](https://img.shields.io/badge/galaxy-%20zaxos.ntopng--ansible--role-blue.svg)](https://galaxy.ansible.com/zaxos/ntopng-ansible-role/)


ntopng-ansible-role
==================

Ansible role to install and configure ntopng.

Requirements
------------
* centos/rhel 7  
* ansible >=2.1
* selinux disabled

Installation
------------
```
$ ansible-galaxy install zaxos.ntopng-ansible-role
```

Example Playbook
----------------
```yaml
    - hosts: servers
      vars:
        ntopng_nprobe_flow_collector_port: 2055
      roles:
        - role: zaxos.ntopng-ansible-role
```

Role Variables
--------------
The main variable:
- `ntopng_nprobe_flow_collector_port`: The udp port of nProbe to collect flows.

Some defaults (probably not requiring tampering):
- `ntopng_use_default_nic_as_monitor_interface`: False  
Set this variable to "True" if you want to use the default network card as ntopng monitor interface.
- `ntopng_http_port`: 3000  
Sets the HTTP port of the embedded web server. If set to 0, the http server will be disabled.
- `ntopng_runas_daemon`: True  
- `ntopng_dns_mode`: 1
    - 0 = Decode DNS responses and resolve only local (-m) numeric IPs.
    - 1 = Decode DNS responses and resolve all numeric IPs.
    - 2 = Decode DNS responses and don't resolve numeric IPs.
    - 3 = Don't decode DNS responses and don't resolve numeric IPs.
- `ntopng_data_dir`: /var/tmp/ntopng
- `ntopng_pid_path`: /var/run/ntopng.pid
- `ntopng_disable_autologout`: False  
Set this variable to "True" in order to disable web interface logout for inactivity.
- `ntopng_community_edition`: True
- `ntopng_nprobe_tcp_port`: 5556  
The tcp port of nProbe from which ntopng collects data.
