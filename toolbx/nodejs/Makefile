.PHONY: setup
setup:
	toolbox rm -f toolbx-node 2>/dev/null
	toolbox create toolbx-node --distro ubuntu --release 24.04 || :
	toolbox run -c toolbx-node -- sudo apt update
	toolbox run -c toolbx-node -- sudo apt install -y nodejs

.PHONY: run
run:
	toolbox run -c toolbx-node -- node main.js

.PHONY: test
test:
	toolbox run -c toolbx-node -- node --test
