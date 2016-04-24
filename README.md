SolvAssignment
=========

In this repository you will find several different playbooks build for setting up servers with ansible. Ansible is an IT automation tool. It can configure systems, deploy software, and orchestrate more advanced IT tasks such as continuous deployments or zero downtime rolling updates. [Learn more about ansible](http://docs.ansible.com/ansible/index.html)

To setup a virtualmachine with docker and a container with nginx first run the bootstrap playbook. This playbook will configure a system with some user accounts, ssh access and configure some basics like the EPEL yum repository.

After a virtual machine is setup with the basic configuration the docker/nginx playbook can be executed. A working example can be found at [http://vps550.directvps.nl](http://vps550.directvps.nl)

The reason for this two faced approach is, to run a playbook on a server ansible needs an user with sudo rights to execute the various tasks. Everything could just be executed as root but for the sake of security the root account over ssh is disabled.

Just for fun i've added a third playbook. With this playbook a Provisioning server with cobbler will be setup that automaticaly provisions a server with CentOS 6 after a PXE boot. Ideally this playbook will be enhanced with more functionality (i.e a jenkins server) to automate the installation even furter.

Setup
------------

Needed software:

- Virtualbox 5.0.18
- ansible 1.9.4
- A clone of this git repository


Run Playbooks
------------

To install the bootstrap on a server run the Bootstrap.yml playbook in the Bootstrap directory. Example:

```
cd Bootstrap
ansible-playbook Bootstrap.yml --extra-vars "target=production --limit docker.solvchallenge.nl"

```

To install the docker container with nginx service run the DockNginx.yml playbook in the DockerNginx directory. For example:

```
cd DockerNginx
ansible-playbook DockNginx.yml --extra-vars "target=production" --limit vps550.directvps.nl

```

To install the provisioning server run the Provisioning.yml playbook in the Provisioning directory. For example:

```
cd Provisioning
ansible-playbook Provisioning.yml --extra-vars "target=production"

```

TODO
------------

Edit Provisioning playbook and add jenkins with jobs to automaticly bootstrap new centos images. Furter more add functionality to run DockNginx.yml playbook via a jinkins job based on configuration in cobbler server.