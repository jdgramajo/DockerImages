# Dockerfile that will build a base image with Ubuntu:14.04 and Oracle JDK 1.8
FROM ubuntu:14.04
MAINTAINER Juan Gramajo, jdgramajo@gmail.com
RUN echo "deb http://archive.ubuntu.com/ubuntu trusty main universe" > /etc/apt/sources.list
RUN apt-get -y update
RUN apt-get -y upgrade
RUN apt-get -y install vim
RUN apt-get -y install curl
RUN apt-get -y install unzip
RUN apt-get -y install git
