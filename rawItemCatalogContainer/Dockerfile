# Based on a machine with Groovy and Grails installs the app and runs it
FROM ubuntu1404/groovyongrails
MAINTAINER Juan Gramajo, jdgramajo@gmail.com

# Expose Grails web app port
EXPOSE 8080

# Clone Repository and run it!
ENTRYPOINT git clone -b gorm_setup https://c9aa31d620ab387c0594007c53e1adec7f40c886:x-oauth-basic@github.com/jdgramajo/rawItemCatalog.git /rawItemCatalog/
CMD ["cd /rawItemCatalog/", "grails run-app"]
