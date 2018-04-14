CHANGE = php bin/change.phar

##
## Project setup
## ---------------------------------------------------------------------------
##

start: ## Install the project
start: init pre-build build install

init: ## Initialize the project structure
init: vendor
	./project.sh init

pre-build: ## Install plugins by performing the Application step
pre-build: assets
	./project.sh pre-build

build: ## Generate working configuration files
build:
	./project.sh build

install: ## Install plugins by performing the DbSchema and Services steps
install:
	./project.sh install

use: ## Switch between countries by specifying the locale
use:
	@read -p "Enter Locale: " locale; \
	./project.sh use $$locale

install-module: ## Install or re-install the specified module by performing the Application step
install-module:
	@read -p "Enter Module Name: " module; \
	$(CHANGE) change:install-plugin --type=module --vendor={Vendor} --steps=Application $$module

install-theme: ## Install or re-install the specified theme by performing the Application step
install-theme:
	@read -p "Enter Theme Name: " theme; \
	$(CHANGE) change:install-plugin --type=theme --vendor={Vendor} --steps=Application $$theme

cc: ## Clear the cache
cc:
	$(CHANGE) change:clear-cache

.PHONY: start init pre-build build install use install-module install-theme cc

##
## Assets
## ---------------------------------------------------------------------------
##

watch: ## Watch the assets and build their development version on change
watch: node_modules
	grunt watch

assets: ## Build the assets
assets: node_modules
	grunt --gruntfile ./Plugins/Themes/{Vendor}/{Theme}/Gruntfile.js

.PHONY: watch assets

##
## Utils
## ---------------------------------------------------------------------------
##

cron: ## Execute cron jobs
cron:
	php Change/Job/Assets/cron.php

.PHONY: cron

# Rules from files

vendor: composer.lock
	composer install -n

composer.lock: composer.json
	@echo composer.lock is not up to date.

node_modules:
	npm install --prefix ./Plugins/Themes/{Vendor}/{Theme}



.DEFAULT_GOAL := help
help:
	@grep -E '(^[a-zA-Z_-]+:.*?##.*$$)|(^##)' $(MAKEFILE_LIST) | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[32m%-30s\033[0m %s\n", $$1, $$2}' | sed -e 's/\[32m##/[33m/'
.PHONY: help
