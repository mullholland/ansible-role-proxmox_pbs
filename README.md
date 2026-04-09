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
    - role: "{{ lookup('env', 'MOLECULE_PROJECT_DIRECTORY') }}"
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/mullholland/ansible-role-proxmox_pbs/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  become: true
  gather_facts: true

  roles:
    - role: mullholland.proxmox_pve
```


## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/mullholland/ansible-role-proxmox_pbs/blob/master/defaults/main.yml):

```yaml
---
# https://pbs.proxmox.com/docs/installation.html#secureapt
proxmox_pve_repository_key: 'https://enterprise.proxmox.com/debian/proxmox-release-{{ ansible_facts["distribution_release"] }}.gpg'
proxmox_pve_repository_keyring: '/etc/apt/keyrings/proxmox-release-{{ ansible_facts["distribution_release"] }}.gpg'

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

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | GitLab |
|-------------|--------|--------|
|[mullholland.proxmox_pve](https://galaxy.ansible.com/mullholland/proxmox_pve)|[![Build Status GitHub](https://github.com/mullholland/ansible-role-proxmox_pve/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-proxmox_pve/actions)|[![Build Status GitLab](https://gitlab.com/mullholland-github-mirror/ansible-role-proxmox_pve/badges/master/pipeline.svg)](https://gitlab.com/mullholland-github-mirror/ansible-role-proxmox_pve)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://mullholland.net) for further information.

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

|container|tags|
|---------|----|
|[Debian](https://hub.docker.com/r/mullholland/debian)|all|

The minimum version of Ansible required is 2.10, tests have been done to:

- The version before the previous version.
- The previous version.
- The current version.

If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-proxmox_pbs/issues).

## [License](#license)

[MIT](https://github.com/mullholland/ansible-role-proxmox_pbs/blob/master/LICENSE).

## [Author Information](#author-information)

[Mullholland](https://mullholland.net)
