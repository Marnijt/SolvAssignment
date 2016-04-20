Bootstrap Playbook
=========

This playbook can be used to bootstrap any CentOS 6 based server. It will install the basic requirements to use ansible, create the admin users with the right sudo permissions and setup basic ssh access. After this playbook run, you're server will also have the EPEL yum repository's available and will be up to date with the latest packages.

Requirements
------------

Centos image with ssh access for running playbook: 

* Use a basic minimal CentOS 6 with ssh and working network connection

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
* to bootstrap a server manually run `ansible-playbook Bootstrap.yml --extra-vars "target=<machine_hostname_or_ip>"`

