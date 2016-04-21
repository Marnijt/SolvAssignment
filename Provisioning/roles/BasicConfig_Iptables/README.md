BasicConfig_Iptables
=========

This role installs a file containing the iptables configuration and an iptables file containing the firewall rules. This currently only handles the iptables settings for ipv4.

Requirements
------------
Centos image with ssh access for running playbook.

Role Variables
--------------

- **BasicConfig_Iptables_iptables_config_template** - path to the iptables configuration file (relative to the &lt;role&gt;/templates directory or the &lt;playbook&gt; directory).
- **BasicConfig_Iptables_iptables_file** - path to the iptables configuration file (relative to the &lt;role&gt;/files directory or the &lt;playbook&gt; directory).

The following variables are templated in the iptables-config file:

- **BasicConfig_Iptables_save_on_stop** - sets the IPTABLES_SAVE_ON_STOP setting in the iptables-config (yes or no)
- **BasicConfig_Iptables_save_on_restart** - sets the IPTABLES_SAVE_ON_RESTART setting in the iptables-config (yes or no)
- **BasicConfig_Iptables_save_counter** - sets the IPTABLES_SAVE_COUNTER setting in the iptables-config (yes or no)
- **BasicConfig_Iptables_status_numeric** - sets the IPTABLES_STATUS_NUMERIC setting in the iptables-config (yes or no)
- **BasicConfig_Iptables_status_verbose** - sets the IPTABLES_STATUS_VERBOSE setting in the iptables-config (yes or no)
- **BasicConfig_Iptables_status_linenumbers** - sets the IPTABLES_STATUS_LINENUMBERS setting in the iptables-config (yes or no)
	
Example Playbook
----------------

The most simple example which installs the default iptables-config and iptables firewall rules (&lt;role&gt;/templates/iptables-config.default.j2 and &lt;role&gt;/files/iptables.default)

    - hosts: development
      sudo: yes
      roles:
        - role: BasicConfig_Iptables

An example using a different iptables rules file and sets different variable values for the iptables-config template file:

    - hosts: development
      sudo: yes
      roles:
        - role: BasicConfig_Iptables
          BasicConfig_Iptables_iptables_file: "files/iptables-0030-rules"
          BasicConfig_Iptables_save_on_stop: "yes"
		  BasicConfig_Iptables_save_on_restart: "yes"
          BasicConfig_Iptables_save_counter: "yes"
          BasicConfig_Iptables_status_numeric: "no"
          BasicConfig_Iptables_status_verbose: "yes"
          BasicConfig_Iptables_status_linenumbers: "no"



