BasicConfig_Docker
=========

This role will install the Docker daemon on a CentOS 6 server.

Requirements
------------

Centos 6 image with ssh access for running playbook. 

Role Variables
--------------

```YAML

```

Example Playbook
----------------

    ---
    - hosts: {{ target }}
      roles:
        - BasicConfig_Docker