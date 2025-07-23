# Toolbx Testing

This directory contains minimal examples of launching containers with
[Toolbx](https://containertoolbx.org/). Toolbx leverages Podman and OCI to
launch lightweight containers on Linux systems.

This is useful for creating development environments on immutable Linux systems,
such as Fedora Silverblue or Bazzite.

Contains examples for C++, Go, Node.js, and Python.

## Makefile Commands

There are some preconfigured `make` commands for interacting with Toolbox:
```bash
make setup  # create (or recreate) a container
make build  # compile an application (for C++/Go only)
make run    # run an application
make test   # run unit tests
```

## Toolbox Commands

You can also interact with Toolbox directly:
```bash
# Create a container
toolbox create <name> --distro ubuntu --release 24.04

# Delete a container
toolbox rm -f <name>

# Start an interactive shell in the container
toolbox enter <name>

# Run a command inside the container
toolbox run -c <name> -- <command>
```
