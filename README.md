# Ansible Role: Cron

[![Build Status](https://api.travis-ci.com/agmalpartida/ansible-role-cron.svg?branch=master)](https://travis-ci.com/github/agmalpartida/ansible-role-cron)

This role will deal with the setup of __Cron__.

Requirements
------------

-

Role Variables
--------------

-

Dependencies
------------

-

Example Playbook
----------------

### Configuration example

```yaml
# cron
entries:
    jobs1:
        name: "backup sites"
        job:    "/root/bin/bkp-duplicity.sh /sites"
        minute: 30
        hour:   00
    jobs2:
        name: "backup mysql"
        job:    "/root/bin/automysqlbackup"
        minute: 30
        hour:   23
```

### Example playbook

```yaml
- hosts: all
  gather_facts: true
  become: yes

  pre_tasks:
    - include_vars: "{{ item }}"
      with_items:
        - "../host_vars/{{ ansible_hostname }}.yml"
        - "../group_vars/linux.yml"
      tags:
        node_check

  roles:
    - role: cron
```

License
-------

BSD

Author Information
------------------

agmalpartida
