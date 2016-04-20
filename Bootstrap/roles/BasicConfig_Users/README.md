BasicConfig_Users
=========

This role is used to create and remove unix users and groups.

Requirements
------------

Centos 6 image with ssh access for running playbook. 

Role Variables
--------------

- **BasicConfig_Users_users_to_create** - Default value: empty list - A list of users to create (see examples below for the format)
- **BasicConfig_Users_create_user_group** - Default value: no - This specifies whether a group should be created with the same name as the user.
- **BasicConfig_Users_users_to_delete** - Default value: empty list - A list of users to delete.
- **BasicConfig_Users_groups_to_create** - Default value: empty list - A list of groups to create.
- **BasicConfig_Users_groups_to_delete** - Default value: empty list - A list of groups to delete.

An example list of users to create (all the user attributes supported by the ansible user module can be specified in the list as well):

    BasicConfig_Users_users_to_create:
        - name: "user1"
          home: "/home/chroot/home/user1"
          password: "$6$IKv1bpqL$NXpbvjzcdsfg8gfd8j9zJlPMpSP.UYobtGcIo7bcZchmgFVmTmoEJ/W7LFfvMmAwO4KSlXBRzDn79VfIBbLJU8/"
          update_password: on_create
        - name: "user2"
          password: "$6$IKv1bpqL$NXpbvjzcxd0yHeSBj9zJlPMpSP.UYoboFjn_8yfKNugh7FVmTmoEJ/W7LFfvMmAwO4KSlXBRzDn79VfIBbLJU8/"
          update_password: on_create

An example list of users to delete:

    BasicConfig_Users_users_to_delete:
        - name: "user1"
        - name: "user2"

Example Playbook
----------------

An example playbook that uses this role and creates two users:

    - hosts: servers
      roles:
        - role: BasicConfig_Users
          BasicConfig_Users_users_to_create:
              - name: "abc"
                home: "/home/chroot/home/abc"
                password: "$6$IKv1bpqL$NXpbvjzcxd0yHeSBj9zJlPMpSP.UYobtGcIo7bcZchmgFVmTmoEJ/W7LFfvMmAwO4KSlXBRzDn79VfIBbLJU8/"
                update_password: on_create
              - name: "def"
                home: "/home/chroot/home/def"
                password: "$6$IKv1bpqL$NXpbvjzcxd0yHeSBj9zJlPMpSP.UYobtGcIo7bcZchmgFVmTmoEJ/W7LFfvMmAwO4KSlXBRzDn79VfIBbLJU8/"
                update_password: on_create
          BasicConfig_Users_create_user_group: yes
