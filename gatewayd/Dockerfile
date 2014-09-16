# Pull nodejs base image
FROM google/nodejs:0.10.30

# Author for nagging
MAINTAINER Adam Cmiel <adamcmiel@gmail.com>

# Install dependencies
RUN apt-get -y install postgresql-client supervisor

# Install gatewayd's dependencies using NPM:
RUN npm install --global pg pm2 grunt grunt-cli forever db-migrate jshint

# Clone project to /gatewayd
ADD gatewayd /gatewayd
RUN cd /gatewayd && npm install

# Add configuration files
ADD config.json /gatewayd/config/config.json
ADD database.json /gatewayd/lib/data/database.json
ADD supervisor.conf /gatewayd/config/supervisor.conf

# Expose running port
EXPOSE 5000

CMD ["supervisord", "-n", "-c", "/gatewayd/config/supervisor.conf"]
