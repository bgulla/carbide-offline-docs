DOCKER_USERNAME ?= bgulla
APPLICATION_NAME ?= kubernetes
HOST_PORT ?=3000
APP_PORT ?=80
IMAGE_NAME?= docs-$(APPLICATION_NAME)

build:
	docker build --tag ${DOCKER_USERNAME}/${IMAGE_NAME} .

prep:
	docker buildx create --use; \
	docker buildx ls

build-multi:
	docker buildx build --tag ${DOCKER_USERNAME}/${IMAGE_NAME} --platform linux/amd64,linux/arm64 .

push:
	docker buildx build --tag ${DOCKER_USERNAME}/${IMAGE_NAME} --platform linux/amd64,linux/arm64 . --push
run:
	docker rm --force docs-$(APPLICATION_NAME); \
	docker run -d --name=docs-$(APPLICATION_NAME)  -p 3000:80 -t  $(DOCKER_USERNAME)/$(IMAGE_NAME); \
	docker logs -f docs-$(APPLICATION_NAME)

