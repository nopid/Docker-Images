BUILDX=docker buildx build --platform linux/amd64,linux/arm64

.PHONY: 3ia all pushall all-multi create-builder 3ia-multi delete-builder

all: 3ia
all-multi: create-builder 3ia-multi delete-builder

pushall:
	docker push nopid/3ia:debian10
	docker image tag nopid/3ia:debian10 nopid/3ia:latest
	docker push nopid/3ia:latest

3ia:
	docker build -t nopid/3ia:debian10 3ia

3ia-multi: create-builder
	$(BUILDX) -t nopid/3ia:debian10 -t nopid/3ia:latest --push 3ia

create-builder:
	docker buildx create --name kat-builder --use
	docker buildx inspect --bootstrap

delete-builder:
	docker buildx rm kat-builder
