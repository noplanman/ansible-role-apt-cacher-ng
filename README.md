# Ansible Role for Apt-Cacher NG

[![Build Status][1]][2]

Installs and configures [Apt-Cacher NG][3] on Debian/Ubuntu servers and respective clients.

## Requirements

For clients, a running Apt-Cacher NG server they can connect to.

## Role Variables

```
# Define this in your playbook to set up on client.
# apt_cacher_ng_server: "1.1.1.1"

# Define this if you'd like to use the backports version.
# (you must have the jessie-backports ource installed).
# apt_cacher_ng_default_release: jessie-backports

apt_cacher_ng_bind_address: "0.0.0.0"
apt_cacher_ng_port: "3142"
apt_cacher_ng_report_page: "acng-report.html"
apt_cacher_ng_cache_dir: "/var/cache/apt-cacher-ng"
apt_cacher_ng_log_dir: "/var/log/apt-cacher-ng"
apt_cacher_ng_verbose_log: "0"
apt_cacher_ng_local_dirs: "acng-doc /usr/share/doc/apt-cacher-ng"
apt_cacher_ng_support_dir: "/usr/lib/apt-cacher-ng"
apt_cacher_ng_pid_file: "/var/run/apt-cacher-ng/pid"
apt_cacher_ng_ex_treshold: "4"
#apt_cacher_ng_proxy: "https://username:proxypassword@proxy.example.net:3129"
apt_cacher_ng_remap_debrep: "file:deb_mirror*.gz /debian ; file:backends_debian"
apt_cacher_ng_remap_uburep: "file:ubuntu_mirrors /ubuntu ; file:backends_ubuntu"
apt_cacher_ng_remap_alxrep: "file:archlx_mirrors /archlinux ; file:backend_archlx"
apt_cacher_ng_remap_fedora: "file:fedora_mirrors"
apt_cacher_ng_remap_epel:   "file:epel_mirrors"
apt_cacher_ng_remap_slrep:  "file:sl_mirrors"
apt_cacher_ng_remap_gentoo: "file:gentoo_mirrors.gz /gentoo ; file:backends_gentoo"
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

```
# playbook.yml
---
- hosts: servers
  become: yes
  vars_files:
    - vars/main.yml
  roles:
    - { role: noplanman.apt-cacher-ng }
```
```
# vars/main.yml (server)
---
apt_cacher_ng_port: "3142"
apt_cacher_ng_cache_dir: "/var/cache/apt-cacher-ng"
apt_cacher_ng_log_dir: "/var/log/apt-cacher-ng"
```
```
# vars/main.yml (client)
---
apt_cacher_ng_server: "1.1.1.1"
apt_cacher_ng_port: "3142"
```

## License

MIT

[1]: https://travis-ci.org/noplanman/ansible-apt-cacher-ng.svg?branch=master "Travis-CI Build Status"
[2]: https://travis-ci.org/noplanman/ansible-apt-cacher-ng "Travis-CI Tests"
[3]: https://www.unix-ag.uni-kl.de/~bloch/acng/ "Apt-Cacher NG"
