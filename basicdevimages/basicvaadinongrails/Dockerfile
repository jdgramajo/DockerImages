# This docker file creates an image with dependencies loaded for a Vaadin on Grails app 
FROM jdgramajo/basicgvm:G244G251
MAINTAINER Juan Gramajo, jdgramajo@gmail.com
# Create a dummy app with vaadin plugin and load all dpeendencies
RUN grails create-app dummyApp
ADD BuildConfig.groovy /tmp/BuildConfig.groovy
RUN chmod 666 /tmp/BuildConfig.groovy
RUN rm dummyApp/grails-app/conf/BuildConfig.groovy
RUN mv /tmp/BuildConfig.groovy dummyApp/grails-app/conf/BuildConfig.groovy
RUN cd dummyApp && grails compile
RUN cd dummyApp && grails vaadin-quickstart
# cleanup
RUN rm -rf dummyApp
