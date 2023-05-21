lint: ## runs the linter
	@markdownlint DEPLOY.md README.md

build: ## in charge of building the website
	@docker run --volume ${GITHUB_WORKSPACE}/module4_task0/:/go golang:1.15.8-buster ls && go build
	@hugo > /dev/null 2>&1

run: ## run app
	@./awesome-api >./awesome-api.log 2>&1 &

post: ## writes up a new post
	@hugo new posts/$(POST_NAME).md
	@echo "---\
	title: '$(POST_TITLE)'\
	date: $(date +"%Y-%m-%dT%H:%M:%S%z")\
	---" > content/posts/$(POST_NAME).md

stop: ## kill the app
	@pkill awesome-api

clean: ## clean contents of dir
	@rm -rf dist
	@rm -f awesome-api awesome-api.log coverage-units.out coverage-integrations.out
	@pkill awesome-api

test: unit-tests integration-tests validate ## tests the tests!
	

help: ## shows help
	@awk -F ': ' '/^[^#].*: /{printf "  %-15s%s\n", $$1, $$2}' $(MAKEFILE_LIST)

unit-tests: ## self-explanatory
	@docker run --volume ${GITHUB_WORKSPACE}/module4_task0/:/go golang:1.15.8-buster ls && go test -v -short -coverprofile=coverage-units.out

integration-tests: ## self-explanatory
	@docker run --volume ${GITHUB_WORKSPACE}/module4_task0/:/go golang:1.15.8-buster ls && go test -v -coverprofile=coverage-integrations.out

check: ## checker
	@markdownlint ./content/posts/*
	@markdown-link-check ./content/posts/*

validate: ## validator
	@./W3C-Validator/w3c_validator.py ./dist/index.html || true

package: ## packages a file named awesome-website.zip
	zip -r awesome-website awesome-api dist/
