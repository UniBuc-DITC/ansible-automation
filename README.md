# Ansible playbooks for automated ops

This repository contains configuration files and [Ansible](https://www.ansible.com/) [playbooks](https://docs.ansible.com/ansible/latest/playbook_guide/playbooks_intro.html) for automating the deployment and maintenance of our software applications.

Most playbooks should be run with the file `inventory.yaml` used as an [inventory](https://docs.ansible.com/ansible/latest/inventory_guide/intro_inventory.html) for Ansible. This file contains the most complete and up-to-date list of virtual machines used as hosts for our services.

## Configuring Ansible

To simplify usage, we recommend using an [Ansible configuration file](https://docs.ansible.com/ansible/latest/reference_appendices/config.html) with some sane defaults.

Create a new `ansible.cfg` file in this directory, with the following contents:

```ini
[defaults]
# Ansible inventory sources
inventory=inventory.yaml

# Path to SSH private key
private_key_file=~/.ssh/id_unibuc

[inventory]
# Give an error when host pattern doesn't match anything
host_pattern_mismatch=error

# Give an error if inventory file could not be parsed
any_unparsed_is_failed=True
```

Replace `~/.ssh/id_unibuc` with the pass to your SSH private key.

The commands listed below assume that you have, at the very least, configured the default inventory file path and the SSL private key to be used.

## Common tasks

### Running an ad-hoc command on a host or a set of hosts

```sh
ansible '<host>' -m ansible.builtin.shell -a '<some command>'
```

### Updating package dependencies on a host or set of hosts

```sh
ansible-playbook -v update-packages.playbook.yaml --extra-vars "variable_host='<host>'"
```
