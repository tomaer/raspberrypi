FROM armbuild/ubuntu
MAINTAINER tomaer <i@tomaer.com>

RUN mkdir -p /app && rm /bin/sh && \
    ln -s /bin/bash /bin/sh && ln -s /lib/arm-linux-gnueabihf/ld-linux.so.3 /lib/ld-linux.so.3

COPY thunder /app/
COPY start.sh /app/

VOLUME /app/TDDOWNLOAD

WORKDIR /app
RUN chmod +x ./start.sh && chmod +x ./portal
CMD ["./start.sh"]
