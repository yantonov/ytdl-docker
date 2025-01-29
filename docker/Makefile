help:
	@cat Makefile

DOCKER_FILE=Dockerfile
SRC?=$(HOME)/Downloads
CONTAINER_SRC=/root/ytdl

IMAGE=yantonov/ytdl
CONTAINER_NAME?=$(shell echo "$(IMAGE)_$(shell date +%s)" | tr '/' '_')

ifeq (run, $(firstword $(MAKECMDGOALS)))
  RUN_ARGS := $(wordlist 2, $(words $(MAKECMDGOALS)), $(MAKECMDGOALS))
  $(eval $(RUN_ARGS):;@:)
endif

EXECUTABLE=$(shell command -v docker >> /dev/null 2>&1 && echo "docker" || echo "podman")

build:
	$(EXECUTABLE) build \
		-t $(IMAGE) \
		-f $(DOCKER_FILE) .

run:
	$(EXECUTABLE) run \
			-i -t \
			--name "$(CONTAINER_NAME)" \
			-v "$(SRC):$(CONTAINER_SRC)" \
			--rm \
			"$(IMAGE)" \
			"yt-dlp" "-f bv*[ext=mp4]+ba[ext=m4a]/b[ext=mp4] / bv*+ba/b" "$(RUN_ARGS)"

ssh:
	$(EXECUTABLE) run -i -t \
			--name "$(CONTAINER_NAME)" \
			-v "$(SRC):$(CONTAINER_SRC)" \
			--rm \
			"$(IMAGE)" \
			/bin/bash

stop:
	$(EXECUTABLE) stop "$(CONTAINER_NAME)"

pull:
	$(EXECUTABLE) pull "$(IMAGE)"

uninstall:
	$(EXECUTABLE) image rm "$(IMAGE)"
