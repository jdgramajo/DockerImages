# Installs GVM on the base image 
FROM ubuntu1404/jdk8
MAINTAINER Juan Gramajo, jdgramajo@gmail.com

# Download and Install GVM
RUN curl http://api.gvmtool.net -o /tmp/gvm-install.sh
RUN chmod 744 /tmp/gvm-install.sh
RUN /tmp/gvm-install.sh

# Clean
RUN rm /tmp/gvm-install.sh
