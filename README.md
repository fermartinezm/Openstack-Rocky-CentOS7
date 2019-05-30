# Openstack Rocky deployment on Centos 7
In this proyect you can find the deployment of Openstack, Rocky version, on Centos 7. The modules installed are:
- Keystone
- Glance
- Nova
- Neutron (using openvirtualswitch)
- Horizon
- Heat
- Celiometer

Besides the modules Openstack also needs some services. The services installed are:
- Chrony
- MariaDB
- RabbitMQ
- Memcached
- etcd

## 1. Enviroment
The installation is divided in three modules:
- Controller (MariaDB, Memcached, RabbitMQ, httpd, Keystone, Glance, Nova API, Neutron Server, Metadata Agent, Horizon, Heat and Celiometer Central)
- Network (Openvswitch, L2 Agent, L3 Agent and Metadata Agent)
- Node (Libvirt, Nova Compute, Celiometer Compute, Openvswitch and L2 Agent)

Network: The network and nodes modules are configured as if they have 2 interfaces. Openvswitch create two brides, one public and one private. In the installation guide is explained what you need modify if you can only use one interface.

## 2. Pre-requisites
- You need Ansible installed in the computer from where the installation is launched. You can install it using the command `yum install ansible` or you can find more information [here](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html?extIdCarryOver=true&sc_cid=701f2000001OH7YAAW#latest-release-via-dnf-or-yum). The last ansible version checked is 2.7.9.

- You need at least 3 machines or virtual machines, one for each module. You can replicate the module node as many times as you want.

- Configure the installation.

## 3. Installation guide
