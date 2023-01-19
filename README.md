
# Ansible Role:  `nginx-exporter`

Ansible role to install and configure [Nginx Prometheus Exporter](https://github.com/nginxinc/nginx-prometheus-exporter).

[![GitHub Workflow Status](https://img.shields.io/github/actions/workflow/status/bodsch/ansible-nginx-exporter/main.yml?branch=main)][ci]
[![GitHub issues](https://img.shields.io/github/issues/bodsch/ansible-nginx-exporter)][issues]
[![GitHub release (latest by date)](https://img.shields.io/github/v/release/bodsch/ansible-nginx-exporter)][releases]
[![Ansible Quality Score](https://img.shields.io/ansible/quality/50067?label=role%20quality)][quality]

[ci]: https://github.com/bodsch/ansible-nginx-exporter/actions
[issues]: https://github.com/bodsch/ansible-nginx-exporter/issues?q=is%3Aopen+is%3Aissue
[releases]: https://github.com/bodsch/ansible-nginx-exporter/releases
[quality]: https://galaxy.ansible.com/bodsch/nginx_exporter


If `latest` is set for `nginx_exporter_version`, the role tries to install the latest release version.  
**Please use this with caution, as incompatibilities between releases may occur!**

The binaries are installed below `/usr/local/bin/nginx_exporter/${nginx_exporter_version}` and later linked to `/usr/bin`.
This should make it possible to downgrade relatively safely.

The application archive is stored on the Ansible controller, unpacked and then the binaries are copied to the target system.
The cache directory can be defined via the environment variable `CUSTOM_LOCAL_TMP_DIRECTORY`.
By default it is `${HOME}/.cache/ansible/nginx_exporter`.
If this type of installation is not desired, the download can take place directly on the target system.
However, this must be explicitly activated by setting `nginx_exporter_direct_download` to `true`.


## Operating systems

Tested on

* Arch Linux
* Debian based
  - Debian 10 / 11
  - Ubuntu 20.10

## Contribution

Please read [Contribution](CONTRIBUTING.md)

## Development,  Branches (Git Tags)

The `master` Branch is my *Working Horse* includes the "latest, hot shit" and can be complete broken!

If you want to use something stable, please use a [Tagged Version](https://github.com/bodsch/node_exporter/tags)!

## Configuration

```yaml
nginx_exporter_version: '0.11.0'
nginx_exporter_nginx_plus: false

nginx_exporter_system_group: nginx-exporter
nginx_exporter_system_user: "{{ nginx_exporter_system_group }}"

nginx_exporter_release:
  download_url: https://github.com/nginxinc/nginx-prometheus-exporter/releases
  file: nginx-prometheus-exporter_{{ nginx_exporter_version }}_linux_{{ go_arch }}.tar.gz

nginx_exporter_direct_download: false

nginx_exporter_config: {}
```

Look to the [defaults](defaults/main.yml) properties file to see the possible configuration properties.

You can also look at the [molecule](molecule/default/group_vars/all) test.


## Operating systems

Tested on

* Debian 10
* Ubuntu 18.04 / 20.04

----

## Author and License

- Bodo Schulz

## License

[Apache](LICENSE)

`FREE SOFTWARE, HELL YEAH!`
