BasicConfig_Sshd
=========

Configure the sshd daemon with a template configuration file. Also this role can be used to install users public ssh keys in either a centralized authorized_keys directory or the users hidden .ssh/authorized_keys file.

Requirements
------------

Centos 6 image with ssh access for running playbook. 

Role Variables
--------------
Variables defaults, see defaults/main.yml for more information

```YAML
# defaults file for BasicConfig_Sshd

# List with user name(s) and their public key
BasicConfig_Sshd_users_to_create: []

BasicConfig_Sshd_loglevel: "INFO"
BasicConfig_Sshd_addressfamily: "any"
BasicConfig_Sshd_authorizedkeysfile_dir: ""
BasicConfig_Sshd_listenaddress: ["0.0.0.0:22"]
BasicConfig_Sshd_passwordauthentication: "yes"
BasicConfig_Sshd_challengeresponseauthentication: "no"
BasicConfig_Sshd_x11forwarding: "yes"
BasicConfig_Sshd_permitrootlogin: "yes"
BasicConfig_Sshd_allowgroups: ""
BasicConfig_Sshd_usedns: "no"
BasicConfig_Sshd_subsystem: "sftp    /usr/libexec/openssh/sftp-server"
```

Example Playbook
----------------

    ---
    - hosts: {{ target }}
      roles:
        - BasicConfig_Sshd


