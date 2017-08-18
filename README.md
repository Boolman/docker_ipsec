strongSwan
==========

Forked from: https://github.com/deltaprojects/strongswan-docker

This docker container runs [strongSwan](https://strongswan.org/) on [alpine Linux](https://alpinelinux.org/).

### Configuration
This cookbook uses two volumes `/etc/ipsec.docker` and `/etc/strongswan.docker`.

* `/etc/ipsec.conf` includes `/etc/ipsec.docker/ipsec.*.conf`
* `/etc/ipsec.secrets` includes `/etc/ipsec.docker/ipsec.*.secrets`
* `/etc/strongswan.conf` includes `/etc/strongswan.docker/*.conf`

So put your configuration files accordingly and mount the needed volumes.

### Usage

##### download
```bash
docker pull boolman/docker_ipsec:v1.0
```

##### run
```bash
docker run -d --privileged --net=host \
  -v '/lib/modules:/lib/modules:ro' \
  -v '/etc/localtime:/etc/localtime:ro' \
  -v '/etc/ipsec.docker:/etc/ipsec.docker:ro' \
  -v '/etc/strongswan.docker:/etc/strongswan.docker:ro' \
  --name ipsec boolman/docker_ipsec:v1.0
```
