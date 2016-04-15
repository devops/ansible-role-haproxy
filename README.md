# Ansible Role: haproxy

Installs HAProxy on RedHat/CentOS servers.

## Requirements

- On RedHat/CentOS 6 must enable EPEL repo to install the socat package.

## Role Variables

### `defaults/main.yml`

* `haproxy_manage_config: true`
* `haproxy_etc_prefix: /etc`

* `haproxy_defaults`
    - see defaults/main.yml

* `haproxy_global`
    - see defaults/main.yml

* `haproxy_stats`
    - see defaults/main.yml

### `vars/RedHat.yml`

* `haproxy_config: "/etc/haproxy/haproxy.cfg"`

## Dependencies

None.

## Example Playbook

    - hosts: servers
      roles:
        - role: haproxy
          haproxy_frontends:
          - name: 'fe-testsite'
            ip: '{{ ansible_default_ipv4.address }}'
            port: '80'
            maxconn: '1000'
            default_backend: 'be-testsite'
          haproxy_backends:
          - name: 'be-testsite'
            description: 'testsite'
            servers:
              - name: 'be-testsite-01'
                ip: '192.168.1.100'

## Author Information

z
