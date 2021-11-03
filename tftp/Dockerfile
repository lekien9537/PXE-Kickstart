
FROM alpine:3.14.2

# Package for syslinux.
ARG SYSLINUX_PACKAGE="https://dl-cdn.alpinelinux.org/alpine/v3.14/main/x86_64/syslinux-6.04_pre1-r9.apk"

RUN apk add --no-cache tftp-hpa && \
    apk --no-cache add curl

RUN mkdir /tmp/syslinux && \
    #wget "$SYSLINUX_PACKAGE" -O /tmp/syslinux/syslinux.apk && \
    curl -o /tmp/syslinux/syslinux.apk "$SYSLINUX_PACKAGE" && \
    tar -C /tmp/syslinux -xvf /tmp/syslinux/syslinux.apk && \
    mkdir -p /tftpboot && \ 
    cp -r /tmp/syslinux/usr/share/syslinux /tftpboot && \
    rm -rf /tmp/syslinux && \
    mkdir -p /tftpboot/syslinux/boot && \
    mkdir -p /tftpboot/syslinux/pxelinux.cfg

COPY bios/pxelinux.cfg /tftpboot/syslinux/pxelinux.cfg

COPY bios/boot /tftpboot/syslinux/boot

EXPOSE 69/udp

CMD  exec in.tftpd -L  --secure --address 0.0.0.0:69  /tftpboot
