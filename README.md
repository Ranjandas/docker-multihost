# Introduction

This repo contains Vagrantfile and Ansible playbook for setting up Docker Multi-Host Networking (Experimental) using Ubuntu Vivid and Docker 1.8 Experimental builds.

## Pre-Requisites

* Vagrant
* VirtualBox (compatible with your vagrant version)
* Ansible (latest)

## Usage

Bring up the vagrant vms

```
$vagrant up
```

Change to Ansible Directory and run the playbook.

```
cd ansible
ansible-playbook -i inventory playbook.yml -skK
```

The default password for the vagrant user (vm user) is 'vagrant'

After the complete successful run of Ansible, set the `DOCKER_HOST` environment variable as shown below.

```
export DOCKER_HOST=192.168.88.100:3375
```

To Test the swarm cluster is working properly do a `docker info` you can see a similar output.

```
$ docker info
Containers: 4
Images: 4
Storage Driver:
Role: primary
Strategy: spread
Filters: affinity, health, constraint, port, dependency
Nodes: 4
 node1: 192.168.88.101:2375
  └ Containers: 1
  └ Reserved CPUs: 0 / 1
  └ Reserved Memory: 0 B / 513.5 MiB
  └ Labels: com.docker.network.driver.overlay.bind_interface=eth1, com.docker.network.driver.overlay.neighbor_ip=192.168.88.101, executiondriver=native-0.2, kernelversion=3.19.0-26-generic, operatingsystem=Ubuntu 15.04, storagedriver=aufs
 node2: 192.168.88.102:2375
  └ Containers: 1
  └ Reserved CPUs: 0 / 1
  └ Reserved Memory: 0 B / 513.5 MiB
  └ Labels: com.docker.network.driver.overlay.bind_interface=eth1, com.docker.network.driver.overlay.neighbor_ip=192.168.88.101, executiondriver=native-0.2, kernelversion=3.19.0-26-generic, operatingsystem=Ubuntu 15.04, storagedriver=aufs
 node3: 192.168.88.103:2375
  └ Containers: 1
  └ Reserved CPUs: 0 / 1
  └ Reserved Memory: 0 B / 513.5 MiB
  └ Labels: com.docker.network.driver.overlay.bind_interface=eth1, com.docker.network.driver.overlay.neighbor_ip=192.168.88.101, executiondriver=native-0.2, kernelversion=3.19.0-26-generic, operatingsystem=Ubuntu 15.04, storagedriver=aufs
 node4: 192.168.88.104:2375
  └ Containers: 1
  └ Reserved CPUs: 0 / 1
  └ Reserved Memory: 0 B / 513.5 MiB
  └ Labels: com.docker.network.driver.overlay.bind_interface=eth1, com.docker.network.driver.overlay.neighbor_ip=192.168.88.101, executiondriver=native-0.2, kernelversion=3.19.0-26-generic, operatingsystem=Ubuntu 15.04, storagedriver=aufs
Execution Driver:
Kernel Version:
Operating System:
CPUs: 4
Total Memory: 2.006 GiB
Name: infra
ID:
```
