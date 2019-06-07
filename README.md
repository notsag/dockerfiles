# Dockerfiles systemd

These images are systemd-enabled to be used with [molecule](https://molecule.readthedocs.io/en/latest/getting-started.html).

**Do not use this containers for production**. They need to be run in **privileged mode**, meaning will have **elevated access to the host system**.

## Usage

### Docker cli

Run the container as a daemon

`docker run -d --privileged --name ubuntu -v /sys/fs/cgroup:/sys/fs/cgroup:ro notsag/ubuntu-systemd`

Enter to the container

`docker exec -it ubuntu /bin/bash`


### Molecule

This is an exemple of a `molecule.yml` file using these images :

```
---
dependency:
  name: galaxy
driver:
  name: docker
lint:
  name: yamllint
platforms:
  - name: centos7
    image: notsag/centos-systemd:7
    command: /sbin/init
    privileged: true
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:ro
  - name: xenial
    image: notsag/ubuntu-systemd:16.04
    command: /sbin/init
    privileged: true
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:ro
  - name: bionic
    image: notsag/ubuntu-systemd:18.04
    command: /sbin/init
    privileged: true
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:ro
  - name: stretch
    image: notsag/debian-systemd:9
    command: /lib/systemd/systemd
    privileged: true
    volumes:
      - /sys/fs/cgroup:/sys/fs/cgroup:ro
provisioner:
  name: ansible
  lint:
    name: ansible-lint
scenario:
  name: default
verifier:
  name: testinfra
  lint:
    name: flake8
```

