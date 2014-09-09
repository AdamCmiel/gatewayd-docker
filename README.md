# Install gatewayd with docker

This project breaks up the gatewayd app into two docker containers:
 - gatewayd
 - postgres


This is the docker way, ship the different pieces of your app in different containers and link them when running.

## Install Instructions

All of the building required is provided by the install.sh

    ./install

## Run that gateway

    docker run --link db:db -d -p 5000:5000 --name gatewayd_start gatewayd
