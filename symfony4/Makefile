CONSOLE = bin/console
PHPCSFIXER ?= php -d memory_limit=1024m vendor/bin/php-cs-fixer

##
## Project setup
## ---------------------------------------------------------------------------
##

clear: ## Remove all the cache, the logs, the sessions and the built assets
clear:
	rm -rf var/cache/*
	rm -rf var/sessions/*
	rm -rf var/logs/*
	rm -rf public/build
	rm .php_cs.cache

clean: ## Clear and remove dependencies
clean: clear
	rm -rf vendor node_modules

cc: ## Clear the cache in dev env
cc:
	$(CONSOLE) cache:clear --no-warmup
	$(CONSOLE) cache:warmup

.PHONY: clear clean cc

##
## Database
## ---------------------------------------------------------------------------
##

db-diff: ## Generate a migration by comparing your current database to your mapping information
db-diff: vendor
	$(CONSOLE) doctrine:migration:diff

db-migrate: ## Migrate database schema to the latest available version
db-migrate: vendor
	$(CONSOLE) doctrine:migration:migrate -n

db-update: ## Force database update
db-update: vendor
	$(CONSOLE) doctrine:schema:update --force

db-rollback: ## Rollback the latest executed migration
db-rollback: vendor
	$(CONSOLE) doctrine:migration:migrate prev -n

db-load: ## Reset the database fixtures
db-load: vendor
	$(CONSOLE) doctrine:fixtures:load -n

db-validate: ## Check the ORM mapping
db-validate: vendor
	$(CONSOLE) doctrine:schema:validate

.PHONY: db-diff db-migrate db-update db-rollback db-load db-validate

##
## Assets
## ---------------------------------------------------------------------------
##

watch: ## Watch the assets and build their development version on change
watch: node_modules
	yarn run encore dev --watch

assets: ## Build the development version of the assets
assets: node_modules
	yarn run encore dev

assets-prod: ## Build the production version of the assets
assets-prod: node_modules
	yarn run encore production

.PHONY: watch assets assets-prod

##
## Dependencies
## ---------------------------------------------------------------------------
##

deps: ## Install the project PHP and JS dependencies
deps: vendor public/build

.PHONY: deps

##
## Tests
## ---------------------------------------------------------------------------
##

phpcs: ## Lint PHP code
phpcs: vendor
	$(PHPCSFIXER) fix --diff --dry-run --no-interaction -v

phpcsfix: ## Lint and fix PHP code to follow the convention
phpcsfix: vendor
	$(PHPCSFIXER) fix

.PHONY: phpcs phpcsfix

# Rules from files

vendor: composer.lock
	composer install -n

composer.lock: composer.json
	@echo compose.lock is not up to date.

node_modules: yarn.lock
	yarn install

yarn.lock: package.json
	@echo yarn.lock is not up to date.

public/build: front node_modules
	yarn run encore dev



.DEFAULT_GOAL := help
help:
	@grep -E '(^[a-zA-Z_-]+:.*?##.*$$)|(^##)' $(MAKEFILE_LIST) | awk 'BEGIN {FS = ":.*?## "}; {printf "\033[32m%-30s\033[0m %s\n", $$1, $$2}' | sed -e 's/\[32m##/[33m/'
.PHONY: help
