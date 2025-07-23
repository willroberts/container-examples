.PHONY: setup
setup:
	toolbox rm -f toolbx-py 2>/dev/null
	toolbox create toolbx-py --distro ubuntu --release 24.04 || :

.PHONY: run
run:
	toolbox run -c toolbx-py -- python3 main.py

.PHONY: test
test:
	toolbox run -c toolbx-py -- python3 -m unittest main_test
