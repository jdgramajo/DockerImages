# From a machine with JDK and GVM installed, installs Groovy and Grails based in the gvm_install.sh file.
FROM ubuntu1404/gvm
MAINTAINER Juan Gramajo, jdgramajo@gmail.com

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
