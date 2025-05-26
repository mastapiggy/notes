# Ansible installation and commands

## Installation:

Install from official repo or with python

```
https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#installation-guide
```  
or for specific linux  
```
https://docs.ansible.com/ansible/latest/installation_guide/installation_distros.html
```

### Configuration  

Configuration file reference:
```
https://docs.ansible.com/ansible/latest/reference_appendices/config.html
```

Configuration file will be searched for in the following order:  
```
ANSIBLE_CONFIG (environment variable if set)
ansible.cfg (in the current directory)
~/.ansible.cfg (in the home directory)
/etc/ansible/ansible.cfg
```  


Most basic config file example in ansible directory `ansible.cfg`:

```sh
[defaults]
inventory = /home/ubuntu/ansible/inventory
private_key_file = /home/ubuntu/.ssh/ansible_ed25519
```
------

## Ansible command  

Running a ping with specific inventory and key file:
```sh
ansible all --key-file ~/.ssh/ansible -i inventory -m ping
```  
running from ansible directory will take local config file so command can be shorten to:
```sh
ansible all -m ping 
```

### Examples

