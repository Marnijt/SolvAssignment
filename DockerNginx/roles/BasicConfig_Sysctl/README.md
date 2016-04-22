BasicConfig_Sysctl
=========

Role for managing sysctl configuration. This role is basically a wrapper around the ansible sysctl core module. 

Requirements
------------

Centos image with ssh access for running playbook.

Role Variables
--------------
Variables defaults:

```
# List of sysctl entries
BasicConfig_Sysctl_entries: []


# Example list of sysctl.conf entries
# Entries used here will switch off IPv6
BasicConfig_Sysctl_entries:
  - name: net.ipv6.conf.all.disable_ipv6
    value: 1
  - name: net.ipv6.conf.default.disable_ipv6
    value: 1

```

Example Playbook
----------------

The playbook below will insert two entries in the sysctl.conf file.

    ---
    - hosts: development
      sudo: yes
      roles:
        - role: BasicConfig_Sysctl
          BasicConfig_Sysctl_entries:
            - name: net.ipv6.conf.all.disable_ipv6
              value: 1
            - name: net.ipv6.conf.default.disable_ipv6
              value: 1

Note: the BasicConfig_Sysctl_entries variable can be defined anywhere. For instance when calling the role (like in the example above) or in the group_vars / host_vars.