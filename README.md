# Ansible Role: WireGuard

An Ansible Role that manages setup and configuration of [WireGuard](https://www.wireguard.com/)

## Role Variables

Available variables listed below, along with default values (see `defaults/main.yml`):

    wireguard_port: 51820

The port WireGuard will listen.

    wireguard_interface: wg0

The interface name that WireGuard should use.

## Example Playbook

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: SananGuliyev.rolename, x: 42 }

## License

MIT

## Author Information

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
