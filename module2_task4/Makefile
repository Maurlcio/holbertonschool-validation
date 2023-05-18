lint: ## linter checker
	@golangci-lint run

build: lint check ## creates the website!
	@hugo
	@go build -o awesome-api

run: ## runs an app
	@./awesome-api >./awesome-api.log 2>&1 &

post: ## writes up a new post
	@hugo new posts/$(POST_NAME).md
	@echo "---\
	title: '$(POST_TITLE)'\
	date: $(date +"%Y-%m-%dT%H:%M:%S%z")\
	---" > content/posts/$(POST_NAME).md

stop: ## stop app
	@pkill awesome-api

clean: ## clean contents
	@rm -rf dist
	@rm -f awesome-api awesome-api.log coverage-units.out coverage-integrations.out

test: unit-tests integration-tests ## test the test


help: ## help
	@awk -F ': ' '/^[^#].*: /{printf "  %-15s%s\n", $$1, $$2}' $(MAKEFILE_LIST)

unit-tests: ## execute unit tests
	@go test -v -short -coverprofile=coverage-units.out

integration-tests: ## execute tests
	@go test -v -coverprofile=coverage-integrations.out

check: ## checks if a link is bad
	@markdownlint ./content/posts/*
	@markdown-link-check ./content/posts/*

validate: ## imported validator
	@./W3C-Validator/w3c_validator.py ./dist/index.html || true
