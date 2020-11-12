[![Build Status](https://travis-ci.com/SananGuliyev/ansible-role-wireguard.svg?branch=master)](https://travis-ci.com/SananGuliyev/ansible-role-wireguard)
[![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/SananGuliyev/ansible-role-wireguard)](https://galaxy.ansible.com/sananguliyev/wireguard)
[![Ansible Galaxy](https://img.shields.io/badge/role-sananguliyev.wireguard-blue.svg)](https://galaxy.ansible.com/sananguliyev/wireguard/)
[![Ansible Galaxy Quality Score](https://img.shields.io/ansible/quality/51749)](https://galaxy.ansible.com/sananguliyev/wireguard/)
[![Ansible Galaxy Downloads](https://img.shields.io/ansible/role/d/51749.svg?color=blue)](https://galaxy.ansible.com/sananguliyev/wireguard/)

# Ansible Role: WireGuard

An Ansible Role that manages setup and configuration of [WireGuard](https://www.wireguard.com/)

## Role Variables

Available variables listed below, along with default values (see `defaults/main.yml`):

    wireguard_port: 51820

The port WireGuard will listen.

    wireguard_interface: wg0

The interface name that WireGuard should use.

    wireguard_postup: 
      - iptables -A FORWARD -i wg0 -j ACCEPT; iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE;

The hooks for to do some network related stuff after a WireGuard interface comes up.

    wireguard_postdown: 
      - iptables -D FORWARD -i wg0 -j ACCEPT; iptables -t nat -D POSTROUTING -o eth0 -j MASQUERADE;

The hooks for to do some network related stuff after a WireGuard interface goes down.

    wireguard_group_destinations:
      some-group:
        - 8.8.8.8 # or 8.8.8.8/32

Destination groups are for routing traffic to specific group hosts (WireGuard `AllowedIPs`) 

    wireguard_allowed_groups:
      - some-client-groups

Allowed groups is for granting access to the server hosts for client hosts.

## Example Playbook

    - hosts: servers
      roles:
         - sananguliyev.wireguard
      vars:
         wireguard_port: 51820
         wireguard_interface: wg0

## Development

Use [docker-molecule](https://github.com/infrastructr/docker-molecule) following the instructions to run [Molecule](https://molecule.readthedocs.io/en/stable/)
or install [Molecule](https://molecule.readthedocs.io/en/stable/) locally (not recommended, version conflicts might appear).

Provide Hetzner Cloud token:

    export HCLOUD_TOKEN=123abc456efg

Use following to run tests:

    molecule test --all

## Maintainers

- [SananGuliyev](https://github.com/SananGuliyev)

## License

See the [LICENSE.md](LICENSE.md) file for details.

## Author Information

This role was created in 2020 by [Sanan Guliyev](https://sanan.guliev.info/).
