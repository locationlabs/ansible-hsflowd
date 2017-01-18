# hsflow

This role installs the host sflow daemon for gathering and sending metrics using sFlow.

## Requirements

Requires ansible >= 2.1 due to using the `apt` module to download hsflowd

## Role Variables

* `hsflow_version`: Version of hsflowd to install

The following ganglia variables are unique to every environment:
* `ganglia_listener_ip'`: MANDATORY - The hostname or ip address of the ganglia listener node receiving metrics
* `ganglia_monitor_send_port'`: MANDATORY - Port number used to send metrics

## Dependencies

None

## Example Playbook

    - hosts: servers
      roles:
         - hsflow
