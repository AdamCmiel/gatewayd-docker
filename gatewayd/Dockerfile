# Pull ubuntu
FROM ubuntu:14.04

# Author for nagging
MAINTAINER Adam Cmiel <adamcmiel@gmail.com>

# Install node.js and dependencies
RUN apt-get -y update
RUN apt-get -y install git python g++ make libpq-dev wget
#RUN apt-get -y install git python-software-properties python g++ make libpq-dev
#RUN apt-get -y install software-properties-common

# Install nodejs
RUN wget http://nodejs.org/dist/v0.10.29/node-v0.10.29-linux-x64.tar.gz
RUN tar -zxvf node-v0.10.29-linux-x64.tar.gz
RUN ln -s /node-v0.10.29-linux-x64/bin/node /usr/local/bin
RUN ln -s /node-v0.10.29-linux-x64/bin/npm /usr/local/bin
RUN apt-get -y install postgresql-client

# Install gatewayd's dependencies using NPM:
RUN npm install --global pg pm2 grunt grunt-cli forever db-migrate jshint

# Clone project to /gatewayd
RUN git clone https://github.com/ripple/gatewayd.git /gatewayd
RUN cd /gatewayd && npm install

# Add configuration files
ADD config.js /gatewayd/config/config.js
ADD database.json /gatewayd/lib/data/database.json

CMD ["/gatewayd/bin/gateway", "start"]
