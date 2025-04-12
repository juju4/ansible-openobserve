[![Actions Status - Master](https://github.com/juju4/ansible-openobserve/workflows/AnsibleCI/badge.svg)](https://github.com/juju4/ansible-openobserve/actions?query=branch%3Amaster)
[![Actions Status - Devel](https://github.com/juju4/ansible-openobserve/workflows/AnsibleCI/badge.svg?branch=devel)](https://github.com/juju4/ansible-openobserve/actions?query=branch%3Adevel)

# openobserve ansible role

A simple ansible role to setup [Openobserve](https://openobserve.ai) (https://github.com/openobserve/openobserve), observability platform (Logs, Metrics, Traces) with low-storage cost, rust-based, SQL based query.

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

* Service fails to start "openobserve.service: Main process exited, code=killed, status=4/ILL". Manual start results in "Illegal instruction". Check `cat /proc/cpuinfo`. Tool default x86 release requires: +sse2,+ssse3,+sse4.1,+sse4.2,+aes, mostly because gxhash. Fallback is source build.
https://github.com/ogxd/gxhash/blob/main/README.md
https://github.com/tteck/Proxmox/discussions/1480
https://github.com/openobserve/openobserve/issues/966
https://discuss.openobserve.ai/2K9df2
https://github.com/openobserve/openobserve/issues/4859
https://github.com/openobserve/openobserve/issues/3495
https://github.com/openobserve/openobserve/issues/3910

* When building openobserve, you will usually need more RAM. 2-3GB may be enough to run a collector, 4-8GB to do the build.

* It does not seem possible to switch an instance with extra cpu instructions to one without (for example, VM/container cluster with different CPU). May cause error like "Error: Migration file of version 'm20241204_143100_create_table_search_queue' is missing, this migration has been applied but its file is missing"

* SSO is only available for enterprise version in self-host mode, which can only be install through helm chart or terraform/aws as per https://openobserve.ai/docs/openobserve-enterprise-edition-installation-guide/. It is free for up to 200 GB of ingestion per day. See also https://openobserve.ai/blog/sso-tax/

## License

BSD 2-clause
