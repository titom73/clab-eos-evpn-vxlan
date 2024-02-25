# Arista ATD Emulation on Containerlab

Lab versions:

- Configuration with ansible management via eAPI or CVP: [`main`](https://github.com/titom73/atd-containerlab/tree/main) or [`avd-builder`](https://github.com/titom73/atd-containerlab/tree/avd-builder) branches
- Configuration managed manually without automation: [`no-ansible`](https://github.com/titom73/atd-containerlab/tree/no-ansible) branch

## Topology

![](diagram.jpg)

> CVP is not part of this lab

- Deploy lab:

```bash
$ cd containerlab-topology

$ sudo containerlab deploy
```

- Save lab

```bash
$ cd containerlab-topology

$ sudo containerlab save
```

- Destroy lab

```bash
$ cd containerlab-topology

$ sudo containerlab destroy
```

## Configuration Management

__Inventory:__

  - Inventory file: [atd-inventory/inventory.yml](atd-inventory/inventory.yml)
  - AVD variables: [atd-inventory/group_vars](atd-inventory/group_vars)

__Commands__

- Build and deploy

```bash
ansible-playbook playbooks/atd-fabric-deploy.yml
```

- Build only

```bash
ansible-playbook playbooks/atd-fabric-deploy.yml --tags build
```

- Build & deploy via eAPI

```bash
ansible-playbook playbooks/atd-fabric-deploy.yml --tags build,deploy_eapi
```

- Build & deploy via CVP

> Be sure to update CVP information in your inventory file.

```bash
ansible-playbook playbooks/atd-fabric-deploy.yml --tags build,deploy_cvp
```

## Authentication

- Username: __admin__ (password: _none_ no ssh access)
- Username: __ansible__ (password: `ansible`)
- Username: __cvpadmin__ (password: `ansible`)
- Username: __arista__ (password: `arista`)

## Management IPs

| Hostname | Managemnt Interface | IP Address      |
| -------- | ------------------- | --------------  |
| Spine1   | Management0         | 192.168.0.10/24 |
| Spine2   | Management0         | 192.168.0.11/24 |
| Leaf1    | Management0         | 192.168.0.12/24 |
| Leaf2    | Management0         | 192.168.0.13/24 |
| Leaf3    | Management0         | 192.168.0.14/24 |
| Leaf4    | Management0         | 192.168.0.15/24 |
| Host1    | Management0         | 192.168.0.16/24 |
| Host2    | Management0         | 192.168.0.17/24 |

## Startup configuration

Devices configuration are saved under [containerlab-topology/configs](containerlab-topology/configs) folder for host devices.
