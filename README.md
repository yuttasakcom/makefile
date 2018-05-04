# Makefile

```
#
# Run `make ENVIRONMENT=machinename` to override the default
#

ENVIRONMENT=default
TLS_VERIFY=$(shell docker-machine env $(ENVIRONMENT) | grep 'DOCKER_TLS_VERIFY=".*"' | cut -d\" -f2)
HOST=$(shell docker-machine env $(ENVIRONMENT) | grep 'DOCKER_HOST=".*"' | cut -d\" -f2)
CERT_PATH=$(shell docker-machine env $(ENVIRONMENT) | grep 'DOCKER_CERT_PATH=".*"' | cut -d\" -f2)
MACHINE_NAME=$(shell docker-machine env $(ENVIRONMENT) | grep 'DOCKER_MACHINE_NAME=".*"' | cut -d\" -f2)
export DOCKER_MACHINE_NAME=$(MACHINE_NAME)
export DOCKER_TLS_VERIFY=$(TLS_VERIFY)
export DOCKER_HOST=$(HOST)
export DOCKER_CERT_PATH=$(CERT_PATH)

default:
	docker ps
```
