# Ansible Role: Process Exporter

[![ubuntu-18](https://img.shields.io/badge/ubuntu-18.x-orange?style=flat&logo=ubuntu)](https://ubuntu.com/)
[![ubuntu-20](https://img.shields.io/badge/ubuntu-20.x-orange?style=flat&logo=ubuntu)](https://ubuntu.com/)
[![debian-9](https://img.shields.io/badge/debian-9.x-orange?style=flat&logo=debian)](https://www.debian.org/)
[![debian-10](https://img.shields.io/badge/debian-10.x-orange?style=flat&logo=debian)](https://www.debian.org/)
[![centos-7](https://img.shields.io/badge/centos-7.x-orange?style=flat&logo=centos)](https://www.centos.org/)
[![centos-8](https://img.shields.io/badge/centos-8.x-orange?style=flat&logo=centos)](https://www.centos.org/)

[![License](https://img.shields.io/badge/license-MIT%20License-brightgreen.svg?style=flat)](https://opensource.org/licenses/MIT)
[![GitHub issues](https://img.shields.io/github/issues/OnkelDom/ansible-role-process-exporter?style=flat)](https://github.com/OnkelDom/ansible-role-process-exporter/issues)
[![GitHub tag](https://img.shields.io/github/tag/OnkelDom/ansible-role-process-exporter.svg?style=flat)](https://github.com/OnkelDom/ansible-role-process-exporter/tags)
[![GitHub action](https://github.com/OnkelDom/ansible-role-process-exporter/workflows/ansible-lint/badge.svg)](https://github.com/OnkelDom/ansible-role-process-exporter)

## Description

Deploy [process-exporter](https://github.com/ncabatoff/process-exporter) using ansible.

## Requirements

- Ansible >= 2.9 (It might work on previous versions, but we cannot guarantee it)
- Community Packages: `ansible-galaxy collection install community.general`

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `proxy_env` | {} | Proxy environment variables |
| `process_exporter_allow_firewall` | false | enable firewall access |
| `process_exporter_binary_install_dir` | /usr/local/bin | default bin dir |
| `process_exporter_version` | 0.7.2 | app version |
| `process_exporter_web_listen_address` | 0.0.0.0 | default listen address |
| `process_exporter_web_listen_port` | 9256 | default listen port |
| `process_exporter_config_dir` | /etc/process_exporter | default config dir |
| `process_exporter_system_user` | "{{ prometheus_user | default('prometheus') }}" | defuault system user |
| `process_exporter_system_group` | "{{ prometheus_group | default('prometheus') }}" | default system group |
| `process_exporter_names` | {} | handling has been set up in an unusual way to handle recommended process-exporter 'Template variables' (such as {{.Comm}}). Follow the example in [defaults/main.yml](defaults/main.yml) if you want to define custom filtering/grouping of processes that use Template variables and make sure to keep the {% raw %} block delimiters. |

## Example

### Playbook

Use it in a playbook as follows:
```yaml
- hosts: all
  roles:
    - onkeldom.process_exporter
```

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
