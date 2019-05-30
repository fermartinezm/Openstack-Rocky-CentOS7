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

Network: The network and nodes modules are configured as if they have 2 interfaces. Openvswitch create two bridges, one public and one private. In the installation guide is explained what you need modify if you can only use one interface.

## 2. Pre-requisites
- You need Ansible installed in the computer from where the installation is launched. You can install it using the command `yum install ansible` or you can find more information [here](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html?extIdCarryOver=true&sc_cid=701f2000001OH7YAAW#latest-release-via-dnf-or-yum). The last ansible version checked is 2.7.9.

- You need at least 3 machines or virtual machines, one for each module. You can replicate the module node as many times as you want.

- Configure the installation.

## 3. Installation guide
- Configure hosts file: You need modify the IPs for each module. If you only have one interface remove the public_ip.
- Configure the file group_vars/all: In this file you can find all the passwords needed for the installation, the network configuration parameters and the network interfaces' names. You need to modify them adapted to your enviroment.
- Removing modules or services from the installation: If you want do not want all the modules or services you can modify the file site.yml to remove it from the installation. You only need comment the part related with that module or service. For example, if you want a different database:
<br />
#- hosts: control
<br />
#  become: true
<br />
#  roles:
<br />
#    - 04-mariadb
