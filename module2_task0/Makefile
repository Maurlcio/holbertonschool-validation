build: ## Initiates the website
	@hugo
	@go build -o awesome-api

run: ## Runs the application awesome-api
	@./awesome-api >./awesome-api.log 2>&1 &

clean: ## Cleans up dist dir
	@pkill awesome-api
	@rm -rf awesome-api awesome-api.log

post: ## In charge of creating new blog posts
	@hugo new posts/$(POST_NAME).md
	@echo "---\
	title: '$(POST_TITLE)'\
	date: $(date +"%Y-%m-%dT%H:%M:%S%z")\
	---" > content/posts/$(POST_NAME).md

stop: ## stop
	@pkill awesome-api

test: ## run tests
	@curl http://localhost:9999
	@curl http://localhost:9999/health

help: ## help command!
	@awk -F ': ' '/^[^#].*: /{printf "  %-15s%s\n", $$1, $$2}' $(MAKEFILE_LIST)
