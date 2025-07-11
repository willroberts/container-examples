# Creating Containers

## With `runc`
```bash
mkdir rootfs
podman export $(podman create busybox) | tar -C rootfs -xvf -
runc spec --rootless
runc run busybox
```

## With `containerd` (using `runc` internally)
Supports image and storage management on top of `runc`.
```bash
# requires containerd to be running
# raises several socket permissions errors, only works as root
ctr images pull docker.io/library/busybox:latest
ctr run docker.io/library/busybox:latest busybox
```

## With `podman` (using `runc` internally)
```bash
podman run -it docker.io/library/busybox
```

## With `podman compose`
```bash
mkdir -p ~/.docker/cli-plugins
wget https://github.com/docker/compose/releases/download/v2.38.1/docker-compose-linux-x86_64 \
  -O ~/.docker/cli-plugins/docker-compose
podman compose up
```
