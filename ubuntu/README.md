# Ubuntu image with systemd enabled

You can use this image as a base container to run systemd services inside.

## Supported tags
 - `latest`, `18.04`
 - `16.04`

## Usage

Run the container as a daemon

`docker run -d --name ubuntu --privileged -v /sys/fs/cgroup:/sys/fs/cgroup:ro notsag/ubuntu-systemd`

Enter to the container

`docker exec -it ubuntu /bin/bash`

Remove the container

`docker rm -f ubuntu`
