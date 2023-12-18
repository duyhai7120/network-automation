# Network-automation
Using Ansible Network Modules allow to easily perform Network Automation tasks such as sending the same commands to multiple devices and configuration management.
These playbooks will run on CISCO NX-OS and Juniper switches.

# Playbook info
traceroute.yml runs traceroute command on CISCO NX-OS switch    
facts.yml gather facts on filesystems and memory on CISCO NX-OS and Juniper switches.
backup.yml creates a seperate directory for each switch and stores backup file in it.

# Required Ansible
Ansible version required 2.10+

# How to use these playbooks
* Clone the project 
https://github.sec.samsung.net/SECA-DevOps/Network-automation.git

Update your inventory file located at /etc/ansible/hosts, for example
add the following lines at the end of hosts file
```
[routers]
nxos ansible_host=<IP of the Router>


[routers:vars]

ansible_network_os = nxos
ansible_connection=ansible.netcommon.network_cli
ansible_user=<Login_user>
ansible_ssh_pass=<Login_password>
```


* Syntax check:
```
ansible-playbook facts.yml --syntax-check
ansible-playbook traceroute.yml --syntax-check
```
* Run playbooks:
```

ansible-playbook facts.yml

ansible-playbook traceroute.yml -e 'dest=ip_address'
Example: ansible-playbook traceroute -e 'dest=10.64.6.100'
```
