# hsflow

This role installs the host sflow daemon for gathering and sending metrics using sFlow.

The expectation is this role will be deployed against hosts where it can retrieve the ganglia
variables from the environment and begin sending baseline metrics to the ganglia infrastructure for
that environment. For KVM hosts, this role will be utilized by `ig/deploy/kvm_hypervisors` and
enable the libvirt integration to gather additional metrics.

## Requirements

Requires ansible >= 2.1 due to using the `apt` module to download hsflowd

## Role Variables

* `hsflow_version`: Version of hsflowd to install
* `kvm`: boolean - Enable libvirt integration when true

The following ganglia variables are unique to every environment:
* `ganglia_listener_ip'`: MANDATORY - The hostname or ip address of the ganglia listener node receiving metrics
* `ganglia_monitor_send_port'`: MANDATORY - Port number used to send metrics

## Dependencies

None

## Example Playbook

To install hsflow on a host:

    - hosts: servers
      roles:
         - hsflow

To enable KVM integration:

    - hosts: hypervisors
      roles:
        - { role: hsflow, kvm: true }
