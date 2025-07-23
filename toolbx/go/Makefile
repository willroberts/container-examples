.PHONY: setup
setup:
	toolbox rm -f toolbx-go 2>/dev/null
	toolbox create toolbx-go --distro ubuntu --release 24.04 || :
	toolbox run -c toolbx-go -- sudo apt update
	toolbox run -c toolbx-go -- sudo apt install -y golang

.PHONY: build
build:
	rm -rf build
	mkdir -p build
	toolbox run -c toolbx-go -- go build -o build/main main.go

.PHONY: run
run:
	toolbox run -c toolbx-go -- go run main.go

.PHONY: test
test:
	toolbox run -c toolbx-go -- go test -v ./...
