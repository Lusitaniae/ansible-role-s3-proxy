Ansible Role: S3 Proxy
==================

[![Build Status](https://travis-ci.org/Lusitaniae/ansible-role-s3-proxy.svg?branch=master)](https://travis-ci.org/Lusitaniae/ansible-role-s3-proxy)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](https://raw.githubusercontent.com/Lusitaniae/ansible-role-s3-proxy/master/LICENSE)
[![Ansible Galaxy](https://img.shields.io/badge/ansible--galaxy-Lusitaniae.s3--proxy-blue.svg)](https://galaxy.ansible.com/Lusitaniae/ansible-role-s3-proxy)


Role for installing a Nginx reverse proxy cache for your S3 repository.

Why use this role
------------
While S3 is a great service to store your static assets, there is a number of benefits that you should be able to enjoy by caching these assets on a external server, such as:

 - Hide your origin bucket;
 - Reduce bandwidth costs;
 - Lower latency.

Depending on your use case, this role might be a good option otherwise a real CDN should do.


Requirements
------------

* geerlingguy.nginx

Role Variables
--------------

Variables you *should* or *might want* to set, including their default values (see `defaults/main.yml`):

    s3_repository_url: sentinel-s2-l1c.s3.amazonaws.com

    nginx_cache_valid: 3d
    nginx_cache_invalid: 30s
    nginx_cache_max_size: 40g
    nginx_cache_inactive: 30d


Example Playbooks
-----------------

Minimal playbook:

```yaml
- hosts: localhost

  vars:
    s3_repository_url: sentinel-s2-l1c.s3.amazonaws.com

  roles:
    - geerlingguy.nginx
    - Lusitaniae.s3-proxy

```


License
-------

MIT
