# Network-automation
This project demonstrate the use of Ansible Network Modules to easily perform Network Automation tasks such as configuration managment, test and validation of existing state and backups etc.
These playbooks will run on CISCO NX-OS and Juniper switches.

# Playbook info
+ config_vlan.yml configures the vlan on CISCO NX-OS switch. The playbook first check is the vlan exists, if it exists it does nothing. If it doesn't exists, it creates a vlan.   
+ facts.yml gather facts on filesystems and memory on CISCO NX-OS and Juniper switches.
+ backup.yml creates a seperate directory for each switch and stores backup file in it.

# Required Ansible
Ansible version required 2.10+

# How to use these playbooks
* Clone the project 
https://github.com/m-1990/Network-automation.git

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
If an inventory file doesn't exists, create a new one for example,
vi /etc/ansible/hosts

* Syntax check:
```
ansible-playbook facts.yml --syntax-check
ansible-playbook traceroute.yml --syntax-check
```
* Run playbooks:
```

ansible-playbook facts.yml

ansible-playbook config_vlans.yml
```
