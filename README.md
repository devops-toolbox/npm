Role Name
=========

npm: Npm

[![Build Status](https://travis-ci.org/cmihai-ansible/npm.svg?branch=master)](https://travis-ci.org/cmihai-ansible/npm)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.npm](https://galaxy.ansible.com/devops-toolbox.npm)

```bash
ansible-galaxy install devops-toolbox.npm
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
npm_packages_state: present
npm_remove_packages: true
npm_enable_service: true
npm_enable_selinux: true
npm_copy_templates: true
npm_firewall_configure: true
npm_firewall_rules:
  - service: ssh
  - port: 3389
npm_users:
  - user: devops
    group: docker
npm_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install npm on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: npm is configured
      import_role:
        name: devops-toolbox.npm
      vars:
        npm_packages_state: present
        npm_remove_packages: true
        npm_enable_service: true
        npm_enable_selinux: true
        npm_copy_templates: true
        npm_firewall_configure: true
        npm_firewall_rules:
          - service: ssh
          - port: 3389
        npm_users:
          - user: devops
            group: docker
        npm_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: npm
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
