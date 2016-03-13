FROM resin/raspberrypi3-buildpack-deps:jessie-scm

ENV LANG C.UTF-8
ENV JAVA_HOME /usr/lib/jvm/jdk-8-oracle-arm32-vfp-hflt
ENV JAVA_VERSION 8u40

RUN echo "deb http://archive.raspberrypi.org/debian/ jessie main ui staging" > /etc/apt/sources.list.d/raspi.list
RUN rm -f /usr/bin/entry.sh
RUN wget -qO - http://archive.raspberrypi.org/debian/raspberrypi.gpg.key | apt-key add -

RUN { \
		echo '#!/bin/bash'; \
		echo 'set -e'; \
		echo; \
		echo 'dirname "$(dirname "$(readlink -f "$(which javac || which java)")")"'; \
	} > /usr/local/bin/docker-java-home && \
	chmod +x /usr/local/bin/docker-java-home

RUN set -x && \
    apt-get update && \
    apt-get install -y oracle-java8-jdk && \
    rm -rf /var/lib/apt/lists/* && \
    [ "$JAVA_HOME" = "$(docker-java-home)" ]

ENTRYPOINT []
