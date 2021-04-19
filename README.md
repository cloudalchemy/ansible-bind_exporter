# Ansible Role: bind_exporter

[![Build Status](https://travis-ci.com/cloudalchemy/ansible-bind_exporter.svg?branch=master)](https://travis-ci.com/cloudalchemy/ansible-bind_exporter)
[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg)](https://opensource.org/licenses/MIT)
[![Ansible Role](https://img.shields.io/badge/ansible%20role-cloudalchemy.bind_exporter-blue.svg)](https://galaxy.ansible.com/cloudalchemy/bind_exporter/)
[![GitHub tag](https://img.shields.io/github/tag/cloudalchemy/ansible-bind_exporter.svg)](https://github.com/cloudalchemy/ansible-bind_exporter/tags)

## Description

Deploy [bind_exporter](https://github.com/prometheus/bind_exporter) using ansible.

## Requirements

- Ansible >= 2.7 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `bind_exporter_version | "0.3.0" | Version of the bind_exporter. Also accepts latest as a parameter. |
| `bind_exporter_binary_local_dir:` | "" | Allows to use local packages instead of ones distributed on github. As parameter it takes a directory where `bind_exporter` binary is stored on host on which ansible is ran. This overrides `bind_exporter_version` parameter |
| `bind_exporter_web_listen_address` | "0.0.0.0:9119" | Address on which bind_exporter will listen. |
| `bind_exporter_pid_file:` | "/run/named/named.pid" | The PID file of the bind process. |
| `bind_exporter_stats_groups` | "server,view" | A list of stats groups to poll. |
| `bind_exporter_stats_url` | "http://localhost:8053/" | The URL of the bind statistics-channel. |
| `bind_exporter_stats_version` | "auto" | Which polling API to use. |

## Example

### Playbook

Use it in a playbook as follows:
```yaml
- hosts: all
  roles:
    - cloudalchemy.bind_exporter
```

### Demo site

We provide demo site for full monitoring solution based on prometheus and grafana. Repository with code and links to running instances is [available on github](https://github.com/cloudalchemy/demo-site) and site is hosted on [DigitalOcean](https://digitalocean.com).

## Local Testing

The preferred way of locally testing the role is to use Docker and [molecule](https://github.com/ansible-community/molecule) (v3.x). You will have to install Docker on your system. See "Get started" for a Docker package suitable to for your system. Running your tests is as simple as executing `molecule test`.

## Continuous Intergation

Combining molecule and circle CI allows us to test how new PRs will behave when used with multiple ansible versions and multiple operating systems. This also allows use to create test scenarios for different role configurations. As a result we have a quite large test matrix which can take more time than local testing, so please be patient.

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## Troubleshooting

See [troubleshooting](TROUBLESHOOTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
