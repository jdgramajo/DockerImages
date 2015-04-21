# Dockerfile that will build a base image with Ubuntu:14.04 and Oracle JDK 1.8.
# Also installs GVM, and latest Groovy and Grails, based in the gvm_installs.sh file.
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

# Add install file and execute installation
ADD gvm_installs.sh /tmp/gvm_installs.sh
RUN chmod 744 /tmp/gvm_installs.sh
RUN /tmp/gvm_installs.sh

# Clean
RUN rm /tmp/gvm-install.sh
RUN rm /tmp/gvm_installs.sh

# Expose Grails web app port
EXPOSE 8080

# Clone Repository and run it!
ENTRYPOINT git clone -b gorm_setup https://c9aa31d620ab387c0594007c53e1adec7f40c886:x-oauth-basic@github.com/jdgramajo/rawItemCatalog.git /rawItemCatalog/
CMD ["cd /rawItemCatalog/", "grails run-app"]
