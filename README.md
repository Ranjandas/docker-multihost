This repo contains Vagrantfile and Ansible playbook for setting up Docker Multi-Host Networking (Experimental) using Ubuntu Vivid and Docker 1.8 Experimental builds.

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


