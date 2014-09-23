# Pull nodejs base image
FROM google/nodejs:0.10.30

# Author for nagging
MAINTAINER Adam Cmiel <adamcmiel@gmail.com>

# Add ripple-rest
ADD ripple-rest /ripple-rest
RUN cd /ripple-rest && npm install

# Add config
ADD config.json /ripple-rest/config.json

EXPOSE 5990

CMD ["node", "/ripple-rest/server.js"]
