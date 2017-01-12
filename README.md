# hsflow

This role installs the host sflow daemon for gathering and sending metrics using sFlow.

## Requirements

Requires ansible >= 2.1 due to using the `apt` module to download hsflowd

## Role Variables

* `hsflow_version`: Version of hsflowd to install

## Dependencies

None

## Example Playbook

    - hosts: servers
      roles:
         - hsflow
