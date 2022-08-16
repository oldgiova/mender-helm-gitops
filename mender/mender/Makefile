SHELL := /bin/bash

# HELP
.PHONY: help

help: ## This help.
	@awk 'BEGIN {FS = ":.*?## "} /^[a-zA-Z_-]+:.*?## / {printf "\033[36m%-30s\033[0m %s\n", $$1, $$2}' $(MAKEFILE_LIST)

.DEFAULT_GOAL := help

# TASKS
poc-lint: ## Run helm lint with values-poc.yaml file
	helm lint . -f values-poc.yaml
	
poc-template: ## Run helm template with values-poc.yaml file
	helm template . -f values-poc.yaml \
		| less

poc-dryrun-deploy: ## Run helm upgrade dry run
	helm upgrade \
		-i \
		--dry-run \
		--debug \
		hm-poc \
		-f values-poc.yaml \
		. \
		| less
