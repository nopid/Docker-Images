FROM nopid/quagga:debian10

ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8

ARG DEBIAN_FRONTEND="noninteractive"
RUN apt update
RUN apt upgrade -y
RUN apt install -y \
	locales \
	xinetd \
	postfix \
	maildrop \
	dovecot-imapd \
	python3-scapy \
	alpine \
	lynx \
	lsof \
	dnsmasq \
	man \
	tmux \
	nmap \
	tcpd \
	isc-dhcp-server \
    proftpd ftp \
    tftp tftpd
RUN apt install -y python3-pyroute2

RUN useradd -ms /bin/bash -p $(openssl passwd -6 guest) guest

RUN apt clean && \
    rm -rf /tmp/* /var/lib/apt/lists/* /var/tmp/*

