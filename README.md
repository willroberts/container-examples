# Container Examples

This repo contains examples of running OCI container images with various tools,
including `podman`, `toolbx`, `quadlet`, and `runc`.

## With `runc`
```bash
mkdir rootfs
podman export $(podman create busybox) | tar -C rootfs -xvf -
runc spec --rootless
runc run busybox
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

## With Quadlet

Quadlet runs Podman containers as systemd units.

Create a container unit:
```
mkdir -p ~/.config/containers/systemd
cat <<EOF
[Container]
ContainerName=nginx
Environment=FOO=Bar
Image=docker.io/nginxinc/nginx-unprivileged
AutoUpdate=registry
PublishPort=8080:8080
Volume=/path/to/data:/data:z

[Install]
WantedBy=default.target # Automatically start on boot.
EOF > ~/.config/containers/systemd/nginx.container

systemctl --user daemon-reload
systemctl --user start nginx
curl -I http://localhost:8080
```
