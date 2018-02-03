FROM ubuntu:latest

ARG JAVA_MAJOR=8
ARG JAVA_UPDATE=161
ARG JAVA_REVISION=b12
ARG COOKIE="Cookie: gpw_e24=http%3A%2F%2Fwww.oracle.com%2F; oraclelicense=accept-securebackup-cookie"

RUN apt-get update \
   && apt-get install -y wget \
   && rm -rf /var/lib/apt/lists/*

# JAVA Env
ENV JAVA_HOME /usr/local/java
ENV PATH $JAVA_HOME/bin:$PATH
RUN mkdir -p "$JAVA_HOME"

ENV JAVA_MAJOR ${JAVA_MAJOR}
ENV JAVA_VERSION ${JAVA_MAJOR}u${JAVA_UPDATE}
ENV JAVA_FULL_VERSION $JAVA_VERSION-$JAVA_REVISION
RUN JDK_FILE=jdk-$JAVA_VERSION-linux-x64.tar.gz \
  && JDK_URL=http://download.oracle.com/otn-pub/java/jdk/8u161-b12/2f38c3b165be4555a1fa6e98c45e0808/$JDK_FILE \
  && cd $JAVA_HOME \
  && wget --no-cookies --no-check-certificate --header "$COOKIE" $JDK_URL \
  && tar -xvf $JDK_FILE --strip-components=1 \
  && rm $JDK_FILE src.zip
