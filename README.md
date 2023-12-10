# [Ansible role proxmox_pbs](#proxmox_pbs)

configure proxmox backup server

|GitHub|Downloads|Version|
|------|---------|-------|
|[![github](https://github.com/mullholland/ansible-role-proxmox_pbs/actions/workflows/molecule.yml/badge.svg)](https://github.com/mullholland/ansible-role-proxmox_pbs/actions/workflows/molecule.yml)|[![downloads](https://img.shields.io/ansible/role/d/mullholland/proxmox_pbs)](https://galaxy.ansible.com/mullholland/proxmox_pbs)|[![Version](https://img.shields.io/github/release/mullholland/ansible-role-proxmox_pbs.svg)](https://github.com/mullholland/ansible-role-proxmox_pbs/releases/)|
## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/mullholland/ansible-role-proxmox_pbs/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  roles:
    - role: "mullholland.proxmox_pbs"
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/mullholland/ansible-role-proxmox_pbs/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: true
  gather_facts: true

  tasks:
    - name: Copy PVE Repository Template
      ansible.builtin.copy:
        content: |
            deb https://enterprise.proxmox.com/debian/pbs {{ ansible_distribution_release }} pbs-enterprise
        dest: /etc/apt/sources.list.d/pbs-enterprise.list
```



## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/mullholland/ansible-role-proxmox_pbs/blob/master/defaults/main.yml):

```yaml
---
# Mostly tested and planned for Proxmox Backuper Server 2+/Debian 11 Bullseye
# Older versions may work

# https://pbs.proxmox.com/docs/installation.html#secureapt
proxmox_pve_repository_key: "https://enterprise.proxmox.com/debian/proxmox-release-{{ ansible_distribution_release }}.gpg"

# manages the Proxmox /etc/apt/sources.list
proxmox_pbs_enable_default_repository: true

# Disable Enterprise Repository
# https://pve.proxmox.com/wiki/Package_Repositories#sysadmin_enterprise_repo
proxmox_pbs_enable_enterprise_repository: false

# Enable the no subscription repository
# https://pve.proxmox.com/wiki/Package_Repositories#sysadmin_no_subscription_repo
# NOT recommended for production use
proxmox_pbs_enable_no_subscription_repository: true
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/mullholland/ansible-role-proxmox_pbs/blob/master/requirements.txt).


## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://mullholland.net) for further information.

Here is an overview of related roles:
![dependencies](https://raw.githubusercontent.com/mullholland/ansible-role-proxmox_pbs/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

|container|tags|
|---------|----|
|[Debian](https://hub.docker.com/r/mullholland/debian)|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-proxmox_pbs/issues).

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-proxmox_pbs/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)
