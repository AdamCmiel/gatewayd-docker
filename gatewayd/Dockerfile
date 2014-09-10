# Pull nodejs base image
FROM google/nodejs:0.10.30

# Author for nagging
MAINTAINER Adam Cmiel <adamcmiel@gmail.com>

# Install dependencies
RUN apt-get -y install postgresql-client

# Install gatewayd's dependencies using NPM:
RUN npm install --global pg pm2 grunt grunt-cli forever db-migrate jshint

# Clone project to /gatewayd
RUN git clone https://github.com/ripple/gatewayd.git /gatewayd
RUN cd /gatewayd && npm install

# Add configuration files
ADD config.json /gatewayd/config/config.json
ADD database.json /gatewayd/lib/data/database.json

EXPOSE 5000

CMD ["/gatewayd/bin/gateway", "start"]
