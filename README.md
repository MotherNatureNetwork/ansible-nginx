[![Travis CI](http://img.shields.io/travis/NarrativeContentGroup/ansible-nginx.svg?style=flat)](http://travis-ci.org/NarrativeContentGroup/ansible-nginx) [![test-suite](http://img.shields.io/badge/test--suite-ansible--nginx-blue.svg?style=flat)](https://github.com/NarrativeContentGroup/ansible-role-tests/tree/master/ansible-nginx/) [![Ansible Galaxy](http://img.shields.io/badge/galaxy-bigjust.nginx-660198.svg?style=flat)](https://galaxy.ansible.com/list#/roles/3059)

nginx
=========

Compiles Nginx, optionally builds pagespeed module.


Requirements
------------

N/A


Role Variables
--------------

see defaults/main.yml, also:

    nginx_pagespeed_enabled: false
    nginx_pagespeed_version: 1.11.33.2
    nginx_version: 1.10.1
    nginx_worker_processes: 2

Most of the variables are self-explanatory, but `nginx_build_options` deserves
an explanation, as it is the primary role of this role. `nginx_build_options` is
a dictionary that passes each item as --<key>=<value>, and keys with no value
are treated as switches.:

    nginx_build_options:
      conf-path: "{{ nginx_conf_path }}"
      error-log-path: "{{ nginx_log_path }}/error.log"
      http-client-body-temp-path: "{{ nginx_lib_path }}/body"
      http-fastcgi-temp-path: "{{ nginx_lib_path }}/fastcgi"
      http-proxy-temp-path: "{{ nginx_lib_path }}/proxy"
      http-scgi-temp-path: "{{ nginx_lib_path }}/scgi"
      http-uwsgi-temp-path: "{{ nginx_lib_path }}/uwsgi"
      http-log-path: "{{ nginx_log_path }}/access.log"
      lock-path: /var/lock/nginx.lock
      pid-path: /run/nginx.pid
      prefix: "{{ nginx_prefix }}"
      with-http_gzip_static_module:
      with-http_realip_module:
      with-http_stub_status_module:
      with-ipv6:
      with-pcre-jit:



Dependencies
------------

N/A


Example Playbook
----------------

standard install

    - hosts: web_servers
      roles:
         - role: ncg.nginx
           nginx_pagespeed_enabled: yes
           nginx_version: 1.10.1

compiles nginx with pagespeed and http_stub_status_module options

License
-------

MIT


Author Information
------------------

This role was written by Justin Caratzas <jcaratzas@mnn.com> for Narrative Content Group.
