BasicConfig_Yum
=========

Installs different repositories in /etc/yum.repo.d/. Uses the default CentOS-Base.repo filename so it does not get overwritten by a `yum update`.

Requirements
------------

Centos 6 image with ssh access for running playbook. 

Role Variables
--------------

Requires the variable "repo_url" to be set correctly. This is used in the template files.

Example Playbook
----------------

    ---
    - hosts: development
      sudo: yes
      vars:
        repo_url: http://repo.example.nl
      roles:
        - { role: BasicConfig_Yum }

