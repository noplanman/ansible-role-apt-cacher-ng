# Ansible Role for Apt-Cacher NG

[![Build Status][travis-build-status]][travis-tests] [![Ansible Role][ansible-role-shield]][ansible-role]

---

:rocket: Development has moved to **[git.feneas.org]**.

(The repository on GitHub is only a mirror, so fork on Feneas to contribute. No registration needed, just sign in with your GitHub account.)

---

Installs and configures [Apt-Cacher NG] on Debian/Ubuntu servers and respective clients.

## Requirements

For clients, a running Apt-Cacher NG server they can connect to.

## Role Variables

See the [`defaults/main.yml`][defaults] file for more details.

Main variables:

```yaml
# Define this in your playbook to set up on client.
# apt_cacher_ng_server: "1.1.1.1"

apt_cacher_ng_bind_address: "0.0.0.0"
apt_cacher_ng_port: "3142"
apt_cacher_ng_report_page: "acng-report.html"
apt_cacher_ng_cache_dir: "/var/cache/apt-cacher-ng"
```

## Role Tags

Each part of the setup has a tag.

```
apt-cacher-ng:install
apt-cacher-ng:configure
apt-cacher-ng:client
```

## Dependencies

None.

## Example Playbook

```yaml
# playbook.yml
---
- hosts: servers
  become: yes
  vars_files:
    - vars/main.yml
  roles:
    - { role: noplanman.apt_cacher_ng }
```
```yaml
# vars/main.yml (server)
---
apt_cacher_ng_port: "3142"
apt_cacher_ng_cache_dir: "/var/cache/apt-cacher-ng"
apt_cacher_ng_log_dir: "/var/log/apt-cacher-ng"
```
```yaml
# vars/main.yml (client)
---
apt_cacher_ng_server: "1.1.1.1"
apt_cacher_ng_port: "3142"
```

## Tests

Docker is used to test the role with different operating systems.

Check the [`tests`] folder.

## License

MIT

[travis-build-status]: https://img.shields.io/travis/noplanman/ansible-role-apt-cacher-ng.svg?style=flat-square "Travis-CI Build Status"
[travis-tests]: https://travis-ci.org/noplanman/ansible-role-apt-cacher-ng "Travis-CI Tests"
[ansible-role-shield]: https://img.shields.io/ansible/role/17388.svg?style=flat-square "Apt Cacher NG on Ansible Galaxy"
[ansible-role]: https://galaxy.ansible.com/noplanman/apt_cacher_ng "Apt Cacher NG on Ansible Galaxy"
[git.feneas.org]: https://git.feneas.org/noplanman/ansible-role-apt-cacher-ng "Ansible Role Apt Cacher NG on Feneas"
[Apt-Cacher NG]: https://www.unix-ag.uni-kl.de/~bloch/acng/ "Apt-Cacher NG"
[defaults]: https://git.feneas.org/noplanman/ansible-role-apt-cacher-ng/blob/master/defaults/main.yml "Default variables"
[`tests`]: https://git.feneas.org/noplanman/ansible-role-apt-cacher-ng/tree/master/tests "Tests"
