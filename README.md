Role Name
=========

airflow: Airflow

[![Build Status](https://travis-ci.org/cmihai-ansible/airflow.svg?branch=master)](https://travis-ci.org/cmihai-ansible/airflow)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.airflow](https://galaxy.ansible.com/devops-toolbox.airflow)

```bash
ansible-galaxy install devops-toolbox.airflow
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
airflow_packages_state: present
airflow_remove_packages: true
airflow_enable_service: true
airflow_enable_selinux: true
airflow_copy_templates: true
airflow_firewall_configure: true
airflow_firewall_rules:
  - service: ssh
  - port: 3389
airflow_users:
  - user: devops
    group: docker
airflow_selinux_booleans:
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
- name: Install airflow on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: airflow is configured
      import_role:
        name: devops-toolbox.airflow
      vars:
        airflow_packages_state: present
        airflow_remove_packages: true
        airflow_enable_service: true
        airflow_enable_selinux: true
        airflow_copy_templates: true
        airflow_firewall_configure: true
        airflow_firewall_rules:
          - service: ssh
          - port: 3389
        airflow_users:
          - user: devops
            group: docker
        airflow_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: airflow
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
