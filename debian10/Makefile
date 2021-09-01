BUILDX=docker buildx build --platform linux/amd64,linux/arm64

.PHONY: base quagga frr sdn 3ia all pushall

all: base quagga 3ia

base:
	$(BUILDX) -t nopid/base:debian10 --push base

quagga: base
	$(BUILDX) -t nopid/quagga:debian10 --push quagga

frr: base
	$(BUILDX) -t nopid/frr:debian10 --push frr

sdn: base
	$(BUILDX) -t nopid/sdn:debian10 --push sdn

p4: base
	$(BUILDX) -t nopid/p4:debian10 --push p4

3ia: base
	$(BUILDX) -t nopid/3ia --push 3ia
