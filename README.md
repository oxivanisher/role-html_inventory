html_inventory
==============
[![Ansible Lint](https://github.com/oxivanisher/role-html_inventory/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/oxivanisher/role-html_inventory/actions/workflows/ansible-lint.yml)

This role confgures a Python virtual environment for Ansible in a users home.

Notes
-----

* If you use the `oxivanisher.ansible_userspace` role, there are several similarities which is ideal to use the same user for both tasks.

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

| Name                                | Comment                                                                              | Default value      |
|-------------------------------------|--------------------------------------------------------------------------------------|--------------------|
| html_inventory_user_name            | Which user will be used to create the html inventory                                 | `root`             |
| html_inventory_venv_subdir          | Which subdirectory in the users home will be used for the python virtual environment | `dev/ansible-venv` |
| html_inventory_port                 | The port on which lighttpd will be configured to run on                              | `8080`             |
| html_inventory_ssh_key              | Path to a existing and authorized SSH key to be used to gather facts                 |                    |
| html_inventory_gatherfacts_playbook | The name of the playbook used to gather facts of all systems                         | `gather_facts.yml` |
| html_inventory_rebootcheck_playbook | The name of the playbook used to check if a reboot is required                       | `upgrade.yml`      |

Example Playbook
----------------

```yaml
- name: Create HTML inventory from ansible-cmdb
  hosts: jumphosts
  roles:
    - role: oxivanisher.linux_server.html_inventory                 # create HTML Ansible inventory
      tags:
        - ansible
```

License
-------

BSD

Author Information
------------------

This role is part of the [oxivanisher.linux_server](https://galaxy.ansible.com/ui/repo/published/oxivanisher/linux_server/) collection, and the source for that is located on [github](https://github.com/oxivanisher/collection-linux_server).
