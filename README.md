# NFS server configuration: ansible role

## Description

You can use this role to install and config NFS server
The role was tested with RedHat.

## Avaliable variable

It has three types of variable.
  - required
  - default
  - permanent

### Required
You MUST set these variables. The role does not work without it!:

The main thing is to define NFS server shares:
```
# Example:
nfs_shares:
  - dir: /opt/nfs/
    networks:
      - net: 192.168.0.0/24
        options: "rw,sync,fsid=1"
      - net: 172.30.10.0/24
        options: "rw,sync,fsid=1"
```
### Default

You can change them if it nessesary:
```
state: present
nfs_version: 4
nfs_create_dir: false
```
- [ ] nfs_version:
    It has two options:
    - 3
    - 4

- [ ] nfs_create_dir: false

- [ ] state:
    It has two optiosn:
    - present - to install and config NFS servers
    - absent - to remove services and configs

### Permanent

Almost it is vars with packages names to install with different conditions.

```
rhel_packages_list:
  - nfs-utils
nfs3_packages:
  - rpcbind

debian_packages_list:
  - nfs-kernel-server

```
