# Dockerfile that will build a base image with Ubuntu:14.04 and Oracle JDK 1.8 
# and GVM with Grails and Groovy versions specified in gvm-install.sh file
FROM ubuntu:14.04
MAINTAINER Juan Gramajo, jdgramajo@gmail.com
RUN echo "deb http://archive.ubuntu.com/ubuntu trusty main universe" > /etc/apt/sources.list
RUN apt-get -y update
RUN apt-get -y upgrade
RUN apt-get -y install vim
RUN apt-get -y install curl
RUN apt-get -y install unzip
RUN apt-get -y install git
RUN apt-get -y install tree

## JAVA INSTALLATION
RUN echo "oracle-java8-installer shared/accepted-oracle-license-v1-1 select true" | debconf-set-selections
RUN echo "deb http://ppa.launchpad.net/webupd8team/java/ubuntu trusty main" > /etc/apt/sources.list.d/webupd8team-java-trusty.list
RUN apt-key adv --keyserver keyserver.ubuntu.com --recv-keys EEA14886
RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y --force-yes --no-install-recommends oracle-java8-installer && apt-get clean all

## JAVA_HOME
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle

#Download and Install GVM
RUN curl http://api.gvmtool.net -o /tmp/gvm-install.sh
RUN chmod 744 /tmp/gvm-install.sh
RUN /tmp/gvm-install.sh

# Clean
RUN rm /tmp/gvm-install.sh

# Add install file and execute installation
ADD gvm_installs.sh /tmp/gvm_installs.sh
RUN chmod 744 /tmp/gvm_installs.sh
RUN /tmp/gvm_installs.sh

# Clean
RUN rm /tmp/gvm_installs.sh

# Environment variables
ENV GROOVY_HOME /root/.gvm/groovy/current
ENV PATH $GROOVY_HOME/bin:$PATH
ENV GRAILS_HOME /root/.gvm/grails/current
ENV PATH $GRAILS_HOME/bin:$PATH

# Dummy app just to download all dependencies
RUN grails create-app dummy
WORKDIR ./dummy
RUN grails compile
WORKDIR ../
RUN rm -rf dummy
