# CentOS image with systemd enabled

You can use this image as a base container to run systemd services inside.

## Supported tags
 - `latest`, `7`

## Usage

Run the container as a daemon

`docker run -d --name centos --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro notsag/centos-systemd`

Enter to the container

`docker exec -it centos /bin/bash`

Remove the container

`docker rm -f centos`
