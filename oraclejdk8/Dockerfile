FROM ubuntu:latest

# JAVA Env
ENV JAVA_HOME /usr/local/java
ENV PATH $JAVA_HOME/bin:$PATH
RUN mkdir -p "$JAVA_HOME"

COPY jdk-8u161-linux-x64.tar.gz /usr/local/java

RUN JAVA_TGZ_FILE=jdk-8u161-linux-x64.tar.gz \
  && cd $JAVA_HOME \
  && tar -xvf $JAVA_TGZ_FILE --strip-components=1 \
  && rm $JAVA_TGZ_FILE src.zip
