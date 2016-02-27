FROM alpine:latest
MAINTAINER Jeyson Maia <jeyson@upspeck.io>

# Utilities
RUN apk upgrade --update \
    && apk add --update ca-certificates wget bash \
    && wget -qO /tmp/glibc-2.21-r2.apk "https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64/glibc-2.21-r2.apk" \
    && apk add --allow-untrusted /tmp/glibc-2.21-r2.apk \
    && wget -qO /tmp/glibc-bin-2.21-r2.apk "https://circle-artifacts.com/gh/andyshinn/alpine-pkg-glibc/6/artifacts/0/home/ubuntu/alpine-pkg-glibc/packages/x86_64/glibc-bin-2.21-r2.apk" && \
    apk add --allow-untrusted /tmp/glibc-bin-2.21-r2.apk \
    && /usr/glibc/usr/bin/ldconfig /lib /usr/glibc/usr/lib \
    && mkdir /opt \
# Install Java.
    && cd /tmp \
    && wget -qO jdk7.tar.gz \
       --header "Cookie: oraclelicense=accept-securebackup-cookie" \
       http://download.oracle.com/otn-pub/java/jdk/7u79-b15/jdk-7u79-linux-x64.tar.gz \
    && tar xzf jdk7.tar.gz -C /opt \
    && mv /opt/jdk* /opt/java

# Define commonly used JAVA_HOME variable
ENV JAVA_HOME /opt/java

# Clean S.O

RUN rm -rf  /opt/java/jre/plugin \
       /opt/java/jre/bin/javaws \
       /opt/java/jre/bin/jjs \
       /opt/java/jre/bin/keytool \
       /opt/java/jre/bin/orbd \
       /opt/java/jre/bin/pack200 \
       /opt/java/jre/bin/policytool \
       /opt/java/jre/bin/rmid \
       /opt/java/jre/bin/rmiregistry \
       /opt/java/jre/bin/servertool \
       /opt/java/jre/bin/tnameserv \
       /opt/java/jre/bin/unpack200 \
       /opt/java/jre/lib/javaws.jar \
       /opt/java/jre/lib/deploy* \
       /opt/java/jre/lib/desktop \
       /opt/java/jre/lib/*javafx* \
       /opt/java/jre/lib/*jfx* \
       /opt/java/jre/lib/jfr* \
       /opt/java/jre/lib/amd64/libdecora_sse.so \
       /opt/java/jre/lib/amd64/libprism_*.so \
       /opt/java/jre/lib/amd64/libfxplugins.so \
       /opt/java/jre/lib/amd64/libglass.so \
       /opt/java/jre/lib/amd64/libgstreamer-lite.so \
       /opt/java/jre/lib/amd64/libjavafx*.so \
       /opt/java/jre/lib/amd64/libjfx*.so \
       /opt/java/jre/lib/ext/jfxrt.jar \
       /opt/java/jre/lib/ext/nashorn.jar \
       /opt/java/jre/lib/oblique-fonts \
       /opt/java/jre/lib/plugin.jar \
       /tmp/* /var/cache/apk/* \
       && apk del wget
