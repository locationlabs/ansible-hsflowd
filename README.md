# hsflow

This role installed the host sflow daemon for gathering and sending metrics using sFlow.

## Requirements

None

## Role Variables

* `hsflow_version`: Version of hsflowd to install

## Dependencies

None

## Example Playbook

    - hosts: servers
      roles:
         - hsflow
