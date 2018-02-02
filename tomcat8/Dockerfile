FROM jdk8:latest

ARG TOMCAT_MAJOR=8
ARG TOMCAT_MINOR=0
ARG TOMCAT_PATCH=49

RUN apt-get update \
   && apt-get install -y curl \
   && rm -rf /var/lib/apt/lists/*

# Get Tomcat Installer
ENV CATALINA_HOME /usr/local/tomcat
ENV PATH $CATALINA_HOME/bin:$PATH
RUN mkdir -p "$CATALINA_HOME"
WORKDIR $CATALINA_HOME

ENV TOMCAT_MAJOR $TOMCAT_MAJOR
ENV TOMCAT_VERSION ${TOMCAT_MAJOR}.${TOMCAT_MINOR}.${TOMCAT_PATCH}

# Download and install tomcat
RUN TOMCAT_TGZ_URL=https://www.apache.org/dist/tomcat/tomcat-$TOMCAT_MAJOR/v$TOMCAT_VERSION/bin/apache-tomcat-$TOMCAT_VERSION.tar.gz \
  && curl -SLk "$TOMCAT_TGZ_URL" -o tomcat.tar.gz \
  && tar -xvf tomcat.tar.gz --strip-components=1 \
  && rm bin/*.bat \
  && rm -rf webapps/docs \
  && rm -rf webapps/examples \
  && rm -rf webapps/manager \
  && rm -rf webapps/host-manager \
  && rm tomcat.tar.gz*

EXPOSE 8080

CMD ["catalina.sh", "run"]
