# Ansible role for openssh-server

Setup restricted openssh-server.

## Requirements

- Debian
- Ubuntu
- packages: openssh-server

## Role Variables

- `sshd_allow_users`: `AllowUsers` in `sshd_config`
- `sshd_allow_tcp_wrappers`: Allow hosts in `hosts.allow`

## Dependencies

None.

## Example Playbook

Example:

    - hosts: servers
      become: yes
      roles:
         - role: znz.sshd

Another example:

    - hosts: all
      become: yes
      gather_facts: no
      tasks:
      - name: "Install and configure the necessary dependencies"
        apt:
          name: openssh-server

    - hosts: all
      become: yes
      roles:
      - role: znz.sshd
        sshd_allow_users:
        - vagrant
        - someuser
        sshd_allow_tcp_wrappers:
        - 10.
        - 192.168.
        - .jp

## License

MIT License
