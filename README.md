# hsflow

This role installs the host sflow daemon for gathering and sending metrics using sFlow.

The expectation is this role will be deployed against hosts where it can retrieve the ganglia
variables from the environment and begin sending baseline metrics to the ganglia infrastructure for
that environment. For KVM hosts, this role will be utilized by `ig/deploy/kvm_hypervisors` and
enable the libvirt integration to gather additional metrics.

## Requirements

Requires

* ansible >= 2.4
* netaddr for determining host IP network
* hsflowd version >= 2.0.7 due to the change in their download url. See https://github.com/sflow/host-sflow/releases

## Role Variables

* `hsflow_version`: Version of hsflowd to install
* `hsflow_kvm`: boolean - Enable libvirt integration when true
* `hsflow_systemd`: boolean - Enable systemd integration when true

The following ganglia variables are unique to every environment:
* `ganglia_listener_ip'`: MANDATORY - The hostname or ip address of the ganglia listener node receiving metrics
* `ganglia_monitor_send_port'`: MANDATORY - Port number used to send metrics

## Dependencies

None

## Example Playbook

To install hsflow on a host:

    - hosts: servers
      tasks:
        - import_role:
            name: hsflow

To enable the integrations:

    - hosts: hypervisors
      tasks:
        - import_role:
            name: hsflow
          vars:
            hsflow_kvm: true
            hsflow_systemd: true
