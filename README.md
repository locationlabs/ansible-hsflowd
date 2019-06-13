# hsflowd

This role installs the [host-sflow agent][1] for gathering and sending metrics using [sFlow][2].

## Requirements

Requires:

* ansible >= 2.4

## Role Variables

Minimal required variables:

* `hsflowd_url`: URL of the hsflowd package - See their [github releases][3] or build/provide your
 own
 * `hsflowd_package_name`: Alternatively if a URL is not provided, will attempt to install from the
  target's available repos using this package name
* `hsflowd_collectors`: A list of sflow collectors, at least **one** must be defined

See `defaults/main.yml` for example variable usage based on [sflow documentation examples][4] to
configured additional modules.

## Dependencies

None

## Example Playbook

Minimal required example:

```yaml
- hosts: servers
  tasks:
    - import_role:
        name: hsflow
      vars:
        hsflowd_url: https://github.com/sflow/host-sflow/releases/download/v2.0.19-1/hsflowd-centos7-2.0.19-1.x86_64.rpm
        hsflowd_collectors:
          - ip: 10.100.12.13
```

[1]: https://github.com/sflow/host-sflow
[2]: https://sflow.net/index.php
[3]: https://github.com/sflow/host-sflow/releases
[4]: https://sflow.net/host-sflow-linux-config.php
