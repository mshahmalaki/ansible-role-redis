Redis Ansible Role
=========

Install Redis, clustering for setup redundant service.

Requirements
------------

Use [Redis configuration refrences](https://redis.io/docs/management/config/) to customize [redis.conf jinja template](./templates/etc/redis/redis.conf.j2).

For test this role you can use [Molecule](https://ansible.readthedocs.io/projects/molecule/).

Categorize target servers with 3 categories in inventory file:

| Group | Description |
|:-------|:------------|
|**redis-masters**|first node|
|**redis-replicas**|other nodes|
|**redis-cluster**|parent of 2 above groups|

For example: **inventory.ini**

```ini
[all]
redis01
redis02
redis03
redis04
redis05
redis06

[redis-masters]
redis01
redis02
redis03

[redis-replicas]
redis04
redis05
redis06

[redis-cluster:children]
redis-masters
redis-replicas

```

Role Variables
--------------

According to [defaults](./defaults/main.yml), you find some variables that you can use on group_vars or host_vars in inventories directory.

Dependencies
------------

Not yet. There is no dependencies.

Example Playbook
----------------

```yaml
---
- hosts: all
  become: true
  roles:
    - mshahmalaki.redis

```

License
-------

MIT

Author Information
------------------

This role was created in 2023 by [Mohammad Shahmaleki](https://github.com/mshahmalaki), for any suggestions and questions about this ansible role contact with me on [Linkedin](https://www.linkedin.com/in/mohammad-shahmaleki/).
