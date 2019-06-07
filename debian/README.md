# Debian image with systemd enabled

You can use this image as a base container to run systemd services inside.

## Supported tags
 - `latest`, `9`
 - `sid`

## Usage

Run the container as a daemon

`docker run -d --name debian --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro notsag/debian-systemd`

Enter to the container

`docker exec -it debian /bin/bash`

Remove the container

`docker rm -f debian`
