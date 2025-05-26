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

For config file and configuration file order:

```
https://docs.ansible.com/ansible/latest/reference_appendices/config.html
```

Most basic config file example in ansible directory `ansible.cfg`:

```sh
[defaults]
inventory = /home/ubuntu/ansible/inventory
private_key_file = /home/ubuntu/.ssh/ansible_ed25519
```
------

## Ansible command

```sh
ansible 
```

### Examples

