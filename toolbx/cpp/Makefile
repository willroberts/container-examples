.PHONY: setup
setup:
	toolbox rm -f toolbx-cpp 2>/dev/null
	toolbox create toolbx-cpp --distro ubuntu --release 24.04 || :
	toolbox run -c toolbx-cpp -- sudo apt update
	toolbox run -c toolbx-cpp -- sudo apt install -y g++

.PHONY: build
build:
	rm -rf build
	mkdir -p build
	toolbox run -c toolbx-cpp -- g++ hello.cpp -o build/hello
