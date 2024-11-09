[![Actions Status - Master](https://github.com/juju4/ansible-openobserve/workflows/AnsibleCI/badge.svg)](https://github.com/juju4/ansible-openobserve/actions?query=branch%3Amaster)
[![Actions Status - Devel](https://github.com/juju4/ansible-openobserve/workflows/AnsibleCI/badge.svg?branch=devel)](https://github.com/juju4/ansible-openobserve/actions?query=branch%3Adevel)

# openobserve ansible role

A simple ansible role to setup [https://openobserve.ai openobserve], observability platform (Logs, Metrics, Traces) with low-storage cost, rust-based, SQL based query.

## Requirements & Dependencies

### Ansible
It was tested on the following versions:
 * 2.17

### Operating systems

Tested on Ubuntu 22.04, 24.04.

## Example Playbook

Just include this role in your list.
For example

```
- host: myhost
  roles:
    - juju4.openobserve
```

you probably want to review variables

## Variables

```
```


## Continuous integration

This role has a Github action and molecule tests.
```
$ pip install molecule docker
$ molecule test
$ MOLECULE_DISTRO=ubuntu:24.04 molecule test --destroy=never
```


## Troubleshooting & Known issues

N/A

## License

BSD 2-clause
