BasicConfig_Selinux
=========

This role can be used to configure activate or deactivate SELinux. 

Requirements
------------

Centos 6 image with ssh access for running playbook.

Role Variables
--------------
Variables defaults:

	BasicConfig_Selinux_config_selinux: disabled
BasicConfig_Selinux_config_selinux can be set to disabled, enforcing or permissive.	

	BasicConfig_Selinux_config_setenforce: 0
BasicConfig_Selinux_config_setenforce is used in handler 'set selinux'. Needs to be 0 when BasicConfig_Selinux_config_selinux is disabled or permissive. Needs to be 1 when enforcing.

Example Playbook
----------------

    ---
    - hosts: development
      sudo: yes
      roles:
        - BasicConfig_Selinux
