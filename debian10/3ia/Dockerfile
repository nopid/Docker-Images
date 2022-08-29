FROM kathara/base:debian10

ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8

RUN curl -s https://deb.frrouting.org/frr/keys.asc | apt-key add -   
   
RUN echo deb https://deb.frrouting.org/frr $(lsb_release -s -c) "frr-7" | tee -a /etc/apt/sources.list.d/frr.list 

RUN apt update && DEBIAN_FRONTEND=noninteractive apt install -y frr frr-pythontools

RUN sed -i -e 's/service/no service/' /etc/frr/vtysh.conf \
    && rm /etc/frr/frr.conf

ARG DEBIAN_FRONTEND="noninteractive"
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
    tftp tftpd \
    python3-pyroute2 \
    radvd

RUN useradd -ms /bin/bash -p $(openssl passwd -6 guest) guest

RUN apt clean && \
    rm -rf /tmp/* /var/lib/apt/lists/* /var/tmp/*

