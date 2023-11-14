# Ansible playbooks for automated ops

This repository contains configuration files and [Ansible](https://www.ansible.com/) [playbooks](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_intro.html) for automating the deployment and maintenance of our software applications.

Most playbooks should be run with the file `inventory.yaml` used as an [inventory](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html) for Ansible. This file contains the most complete and up-to-date list of virtual machines used as hosts for our services.

## Common tasks

### Updating package dependencies on a host or set of hosts

```sh
ansible-playbook -v -i inventory.yaml update-packages.playbook.yaml --extra-vars "variable_host='<host>'"
```
