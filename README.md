SolvAssignment
=========

With this playbook 

Setup
------------



Run Playbooks
------------

To install the bootstrap a server run the Bootstrap.yml playbook in the Bootstrap directory. Example:

```
cd Bootstrap
ansible-playbook Bootstrap.yml --extra-vars "target=production --limit docker.solvchallenge.nl"

```


To install the provisioning server run the Provisioning.yml playbook in the Provisioning directory. For example:

```
cd Provisioning
ansible-playbook Provisioning.yml --extra-vars "target=production"

```

To install the docker container with nginx service run the DockNginx.yml playbook in the DockerNginx directory. For example:

```
cd DockerNginx
ansible-playbook DockNginx.yml --extra-vars "target=production" --limit vps550.directvps.nl

```
