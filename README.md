# Ansible check_mk_agent_logwatch role

This is an [Ansible](http://www.ansible.com) role to setup Check_MK agent logwatch.

## Role Variables

A list of all the default variables for this role is available in `defaults/main.yml`.

## Example Playbook

This is an example playbook:

```yaml
---

- hosts: all
  roles:
    - amtega.check_mk_agent_logwatch
  vars:  
    check_mk_agent_logwatch:
      - file: /var/log/messages
        checks:
          - type: critical
            regex: "Fail event detected on md device"
          - type: ignore
            regex: "mdadm.*: Rebuild.*event detected"
          - type: warning
            regex: "mdadm\\["
          - type: warning
            regex: "ata.*hard resetting link"
          - type: warning
            regex: "ata.*soft reset failed (.*FIS failed)"
          - type: warning
            regex: "device-mapper: thin:.*reached low water mark"
          - type: critical
            regex: "device-mapper: thin:.*no free space"
          - type: critical
            regex: "Error: (.*)"
```

## Testing

Tests are based on docker containers. You can setup docker engine quickly using the playbook `files/setup.yml` available in the role [amtega.docker_engine](https://galaxy.ansible.com/amtega/docker_engine).

Once you have docker, you can run the tests with the following commands:

```shell
$ cd amtega.check_mk_agent_logwatch/tests
$ ansible-playbook main.yml
```

## License

Copyright (C) 2019 AMTEGA - Xunta de Galicia

This role is free software: you can redistribute it and/or modify it under the terms of:

GNU General Public License version 3, or (at your option) any later version; or the European Union Public License, either Version 1.2 or – as soon they will be approved by the European Commission ­subsequent versions of the EUPL.

This role is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU General Public License for more details or European Union Public License for more details.

## Author Information

- Juan Antonio Valiño García.
