BasicConfig_Network
=========

Role to add interface related configuration files to the system. Files can be ifcfg-em* or route-em* etc.

Requirements
------------
Centos 6 image with ssh access for running playbook. 

Role Variables
--------------

A list of Ethernet network interface configuration files to add to the system

- **BasicConfig_Networking_ifcfg_config_to_add: []**
    
Optional parameters:

- src: - Default source is ${PLAYBOOKBASEDIR}/files/{{ item.name }}
- dest: - Default destination is /etc/sysconfig/network-scripts/{{ item.name }}


 
A list of Ethernet network interface configuration files to remove from the system

- **BasicConfig_Networking_ifcfg_config_to_delete: []**

Optional paramaters:
- path: - Default path is /etc/sysconfig/network-scripts/{{ item.name }} 


Example Playbook
----------------

```
---
- hosts: development
  sudo: yes
  Vars:
      BasicConfig_Networking_ifcfg_config_to_add:
        - name: ifcfg-dummyinterface200
          src: files/BasicConfig_Networking/ifcfg-dummyinterface200
        - name: ifcfg-dummyinterface300
      BasicConfig_Networking_ifcfg_config_to_delete:
        - name: ifcfg-dummyinterface200
        - name: ifcfg-dummyinterface300
  roles:
    - BasicConfig_Network
```

