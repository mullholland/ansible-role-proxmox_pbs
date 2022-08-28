# [proxmox_pbs](#proxmox_pbs)

|GitHub|GitLab|
|------|------|
|[![github](https://github.com/mullholland/ansible-role-proxmox_pbs/workflows/Ansible%20Molecule/badge.svg)](https://github.com/mullholland/ansible-role-proxmox_pbs/actions)|[![gitlab](https://gitlab.com/mullholland/ansible-role-proxmox_pbs/badges/main/pipeline.svg)](https://gitlab.com/mullholland/ansible-role-proxmox_pbs)|

description

## [Role Variables](#role-variables)

These variables are set in `defaults/main.yml`:
```yaml
---
# Mostly tested and planned for Proxmox Backuper Server 2+/Debian 11 Bullseye
# Older versions may work

# https://pbs.proxmox.com/docs/installation.html#secureapt
proxmox_pve_repository_key: "https://enterprise.proxmox.com/debian/proxmox-release-bullseye.gpg"

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


## [Example Playbook](#example-playbook)

This example is taken from `molecule/default/converge.yml` and is tested on each push, pull request and release.
```yaml
---
- name: Converge
  hosts: all
  become: true
  gather_facts: true
  # vars:
  #   example_var: "value"
  roles:
    - role: "mullholland.proxmox_pbs"
```

The machine needs to be prepared in CI this is done using `molecule/default/prepare.yml`:
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





## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/mullholland):

-   [debian11](https://hub.docker.com/r/mullholland/docker-molecule-debian11)

The minimum version of Ansible required is 2.10, tests have been done to:

-   The previous versions.
-   The current version.



## [Exceptions](#exceptions)

Some variations of the build matrix do not work. These are the variations and reasons why the build won't work:

| variation                 | reason                 |
|---------------------------|------------------------|
| Redhat/CentOS/Fedora | Proxmox is based on Debian |
| Rocky Linux | Proxmox is based on Debian |
| Almalinux | Proxmox is based on Debian |
| Ubuntu | Proxmox is based on Debian |
| AmazonLinux | Proxmox is based on Debian |
| Debian10 | Testet only with Proxmox Backup Server 2/Debian 11 |


If you find issues, please register them in [GitHub](https://github.com/mullholland/ansible-role-proxmox_pbs/issues)

## [License](#license)

MIT


## [Author Information](#author-information)

[Mullholland](https://github.com/mullholland)

## [Special Thanks](#special-thanks)

Template inspired by [Robert de Bock](https://github.com/robertdebock)
