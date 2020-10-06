# Ansible Role: process_exporter

## Description

Deploy [process-exporter](https://github.com/ncabatoff/process-exporter) using ansible.

## Requirements

- Ansible >= 2.6 (It might work on previous versions, but we cannot guarantee it)

## Role Variables

All variables which can be overridden are stored in [defaults/main.yml](defaults/main.yml) file as well as in table below.

| Name           | Default Value | Description                        |
| -------------- | ------------- | -----------------------------------|
| `proxy_env` | {} | Proxy environment variables |
| `process_exporter_version` | 0.5.0 | Process exporter package version. Also accepts latest as parameter |
| `process_exporter_web_listen_address` | "0.0.0.0:9256" | Address on which process_exporter will listen |
| `process_exporter_config_dir` | "/etc/process_exporter" | Path to directory with process_exporter configuration |
| `process_exporter_names` | [see: defaults/main.yml](defaults/main.yml#L8) | Processes which should be monitored. Syntax is the same as in https://github.com/ncabatoff/process-exporter#using-a-config-file Default is consistent with deb/rpm packages.|
| `process_exporter_create_consul_agent_service` | "true" | Add consul agent config snipped |

`process_exporter_names` handling has been set up in an unusual way to handle recommended process-exporter 'Template variables' (such as {{.Comm}}). Follow the example in [defaults/main.yml](defaults/main.yml) if you want to define custom filtering/grouping of processes that use Template variables and make sure to keep the {% raw %} block delimiters.

## Example

### Playbook

Use it in a playbook as follows:
```yaml
- hosts: all
  roles:
    - ansible-role-process_exporter
```

## Contributing

See [contributor guideline](CONTRIBUTING.md).

## License

This project is licensed under MIT License. See [LICENSE](/LICENSE) for more details.
