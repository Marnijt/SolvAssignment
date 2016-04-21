BasicConfig_Sudo
=========

Configure sudo with a template configuration file. 

Requirements
------------

Centos 6 image with ssh access for running playbook. 

Role Variables
--------------
Variables defaults, see defaults/main.yml for more information

```YAML
# defaults file for BasicConfig_Sudo

# package name (version)
BasicConfig_Sudo_sudo_package: sudo
# list of username or %groupname
BasicConfig_Sudo_sudo_users: []
# list of username or %groupname and their defaults
BasicConfig_Sudo_sudo_defaults: []
```

Example Playbook
----------------

    ---
    - hosts: {{ target }}
      roles:
        - BasicConfig_Sudo