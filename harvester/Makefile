DOCKER_USERNAME ?= bgulla
APPLICATION_NAME ?= carbidinator

build:
	docker build --tag ${DOCKER_USERNAME}/${APPLICATION_NAME} .
run:
	docker rm --force dev; docker run -d --name=dev  -p 3000:80 -t  ${DOCKER_USERNAME}/${APPLICATION_NAME}; docker logs -f dev
