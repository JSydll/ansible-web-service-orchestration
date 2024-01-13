# Multitenant Service Hosting

Ansible-based orchestration for self-hosted services with multi-tenancy support.

Fork from https://git.jotbe.io/jotbe/ansible-selfhosted-services/src/branch/master.

Picks up the concept of putting the services behind the Traefik reverse proxy, 
allowing to route outside requests by (sub-)domain. The individual services run totally 
isolated from each other.

The service orchestration is implemented with
- a hierarchical configuration of hosts in the `inventory.ini`, leading to the services for different 
  tenants being deployed on the same machine, and
- environment variables being passed to the service roles for unique identification and proper routing 
  by Traefik.

The hierarchy of hosts in the inventory can be categorized as follows:

```
machine hosts [representing actual servers]
'- tenant hosts [representing isolated tenants]
   '- service hosts 
```

## Repository structure

| Path              | Description                                                                          |
| ----------------- | ------------------------------------------------------------------------------------ |
| `host_vars`       | Actual configuration of hosts and services (see below)                               |
| `playbooks`       | Mapping of service hosts to ansible roles                                            |
| `requirements.yml`| Project requirements to be installed by Ansible                                      |
| `ansible.cfg`     | General Ansible configuration                                                        |
| `inventory.ini`   | Hierarchy of hosts and mapping to actual remote machines                             |
| `site.yml`        | The collection of playbooks to be executed on an Ansible run                         |

## Host and service configuration

The configuration of each tenant's services is done using `host_vars`. A distinct subdirectory is used per 
machine and tenant host defined in the inventory. In there, the actual configuration files for the service hosts
can be found (like firewall, traefik, ...). 

To write your own configuration files, checkout the `examples` provided. 

## Running Ansible

Executing the deployment can be done after configuration with `ansible-playbook --ask-become-pass site.yml`.

## Known limitations

- Currently, only the Jitsi service was tested in multitenancy setup

## Roadmap

- Push local changes for multitenancy in jotbe roles to upstream
- Enable/test other services
- Grafana dashboard for system and individual service monitoring