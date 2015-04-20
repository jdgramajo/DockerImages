# Dockerfile that will build a base image with Ubuntu:14.04 and Oracle JDK 1.8.
# Also installs GVM, to be used as base
FROM ubuntu:14.04
MAINTAINER Juan Gramajo, jdgramajo@gmail.com
RUN echo "deb http://archive.ubuntu.com/ubuntu precise main universe" > /etc/apt/sources.list
RUN apt-get -y update
RUN apt-get -y upgrade

## JAVA INSTALLATION
RUN echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 select true" | debconf-set-selections
RUN echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" > /etc/apt/sources.list.d/webupd8team-java-trusty.list
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --force-yes --no-install-recommends oracle-java8-installer && apt-get clean all

## JAVA_HOME
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

# Download and Install GVM
USER root
RUN apt-get -y install curl unzip
RUN curl http://api.gvmtool.net -o /tmp/gvm-install.sh
RUN chmod 744 /tmp/gvm-install.sh
RUN /tmp/gvm-install.sh
ENTRYPOINT source "/root/.gvm/bin/gvm-init.sh"
CMD ["gvm list groovy && gvm list grails"]
