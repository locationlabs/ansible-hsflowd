# hsflow

This role installs the host sflow daemon for gathering and sending metrics using sFlow.

## Requirements

Requires ansible >= 2.1 due to using the `apt` module to download hsflowd

## Role Variables

* `hsflow_version`: Version of hsflowd to install
* `deploy_mode`: Controls deploy mode, mutually exclusive actions, default value _install_.
 * `install`: Install basic hsflow config
 * `hv`: Update hsflow config with KVM integration

The following ganglia variables are unique to every environment:
* `ganglia_listener_ip'`: MANDATORY - The hostname or ip address of the ganglia listener node receiving metrics
* `ganglia_monitor_send_port'`: MANDATORY - Port number used to send metrics

## Dependencies

None

## Example Playbook

To just install hsflow on a host:

    - hosts: servers
      roles:
         - hsflow

To enable KVM integration on a host that already has hsflow installed via this role

    - hosts: hypervisors
      roles:
        - { role: hsflow, deploy_mode: 'hv' }
