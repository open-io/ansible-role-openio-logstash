[![Build Status](https://travis-ci.org/open-io/ansible-role-openio-logstash.svg?branch=master)](https://travis-ci.org/open-io/ansible-role-openio-logstash)
# Ansible role `logstash`

An Ansible role for logstash. Specifically, the responsibilities of this role are to:

- install logstash
- configure logstash with OpenIO template

## Requirements

- Ansible 2.4+

## Role Variables

| Variable   | Default | Comments (type)  |
| :---       | :---    | :---             |
| `openio_logstash_beats_address` | `localhost` | ... |
| `openio_logstash_beats_port` | `5044` | ... |
| `openio_logstash_beats_ssl` | `false` | ... |
| `openio_logstash_elasticsearch_address` | `localhost` | ... |
| `openio_logstash_elasticsearch_login` | `logstash` | ... |
| `openio_logstash_elasticsearch_password` | `logstash` | ... |
| `openio_logstash_elasticsearch_port` | `6400` | ... |
| `openio_logstash_gridinit_dir` | `"/etc/gridinit.d/{{ openio_logstash_namespace }}"` | ... |
| `openio_logstash_gridinit_file_prefix` | `""` | ... |
| `openio_logstash_ignore_key_error` | `false` | ... |
| `openio_logstash_java_args` | `...` | ... |
| `openio_logstash_memory` | `512M` | ... |
| `openio_logstash_namespace` | `"OPENIO"` | ... |
| `openio_logstash_pid_directory` | `/run/logstash/{{ openio_logstash_namespace }}/logstash-{{ openio_logstash_serviceid }}` | ... |
| `openio_logstash_provision_only` | `false` | ... |
| `openio_logstash_repo` | `"6.x"` | ... |
| `openio_logstash_serviceid` | `"0"` | ... |
| `openio_logstash_volume` | `` | ... |

## Dependencies

No dependencies.

## Example Playbook

```yaml
- hosts: localhost
  become: true
  vars:
    NS: OPENIO
  roles:
    - role: repo
    - role: gridinit
      openio_gridinit_namespace: "{{ NS }}"
      openio_gridinit_per_ns: true
    - role: logstash
      openio_logstash_namespace: "{{ NS }}"
      openio_logstash_memory: "256M"
```


```ini
[all]
node1 ansible_host=192.168.1.173
```

## Contributing

Issues, feature requests, ideas are appreciated and can be posted in the Issues section.

Pull requests are also very welcome.
The best way to submit a PR is by first creating a fork of this Github project, then creating a topic branch for the suggested change and pushing that branch to your own fork.
Github can then easily create a PR based on that branch.

## License

GNU AFFERO GENERAL PUBLIC LICENSE, Version 3

## Contributors

- [Cedric DELGEHIER](https://github.com/cdelgehier) (maintainer)
