# Deploy bind9 server on Centos7

## Description
Use Ansible Playbook and role to deploy bind9 DNS server on a Centos7 server.

## Requirements
* Python (≥ 2.6)
* Ansible
* PyVmomi

## Configuration
The required files are:
```
├── ansible.cfg
├── answerfile.yml
├── deploy-bind-server.yaml
├── nfs-vm
├── README.md
└── roles
    ├── deploy-bind9-template
    │   ├── tasks
    │   │   └── main.yml
    │   └── templates
    │       ├── db.forward.j2
    │       ├── db.reverse.j2
    │       ├── dns.keys.conf.j2
    │       ├── named.conf.j2
    │       └── named.conf.local.j2
    ├── deploy-prerequisites-template
    │   └── tasks
    │       └── main.yml
    └── deploy-pubkey-template
        └── tasks
            └── main.yml
```

1. Edit the ```vms-to-deploy``` file to define where to install bind9.
2. Edit the ```answerfile.yml``` file to define the dns zone you want create and the DNS forwarders.

## Execution

```
ansible-playbook -i nfs-vm deploy-bind-server.yaml --ask-pass
```
