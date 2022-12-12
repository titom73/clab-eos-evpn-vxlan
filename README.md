# Arista ATD Emulation on Containerlab

An AVD builder is available in branch [`avd-builder`](https://github.com/titom73/atd-containerlab/tree/avd-builder)

## Topology

![](diagram.jpg)

> CVP is not part of this lab

- Deploy lab:

```bash
$ cd containerlab-topology

$ sudo containerlab deploy --topo topology.yml
```

- Save lab

```bash
$ cd containerlab-topology

$ sudo containerlab save --topo topology.yml
```

- Destroy lab

```bash
$ cd containerlab-topology

$ sudo containerlab destroy --topo topology.yml
```

## Authentication

- Username: __admin__ (password: _none_)
- Username: __ansible__ (password: `ansible`)
- Username: __cvpadmin__ (password: `ansible`)

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

Devices configuration are saved under [containerlab-topology/configs](containerlab-topology/configs) folder

## Configure SSH client

- Copy `ssh-config` file to `~/.ssh/config.d/ssh-atd-containerlab`

```bash
$ mkdir -p ~/.ssh/config.d

$ cp ssh-config ~/.ssh/config.d/ssh-atd-containerlab
```

- Update your ssh configuration file

```bash
$ vim ~/.ssh/config

# Insert at the top of your file
Include config.d/atd-containerlab
```

### Configure remote access

Only applicable if your containerlab topology is running on a remote server:

```bash
$ vim ~/.ssh/config.d/ssh-atd-containerlab

# Host jump-clab
#     IdentityFile ~/.ssh/id-tom
#     UserKnownHostsFile ~/.ssh/atd_known_hosts
#     HostName 10.0.0.1
#     ControlMaster   auto
#     ControlPath     ~/.ssh/mux-%r@%h:%p
#     ControlPersist  15m
#     User arista
```

Uncomment this section and update information:
- `HostName` section with IP address of your remote server
- `User`: Your remote username
- `IdentityFile`: (Optional) your ssh key
