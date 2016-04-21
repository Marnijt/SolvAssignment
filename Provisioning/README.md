Provisioning Playbook
=========

This playbook can be used to create a provisioning service on any CentOS 6 based server. It will install the cobbler service, 

Requirements
------------

Centos 6 image bootstrapped with Bootstrap playbook and ssh access for running playbook.

Variables and used roles
--------------
Used roles:

* BasicConfig_Yum
* BasicConfig_Selinux
* BasicConfig_Users
* BasicConfig_Sudo
  * BasicConfig_Sudo_sudo_users

Example
----------------
To run this playbook:

* clone this repository
* cd into cloned directory
* to bootstrap a server manually run `ansible-playbook Provisioning.yml --extra-vars "target=<machine_hostname_or_ip>"`

