# Install gatewayd with docker

This project breaks up the gatewayd app into two docker containers:
 - gatewayd
 - postgres (note this is for development, and data will not persist after the docker daemon is closed)


This is the docker way, ship the different pieces of your app in different containers and link them when running.

## Install Instructions

Download gatewayd into the gatewayd directory

    git clone https://github.com/ripple/gatewayd.git ./gatewayd/gatewayd

All of the building required is provided by the install.sh

    ./install

Most docker installations require `sudo ./install`

## Run that gateway

    docker run --link db:db -d -p 5000:5000 --name gatewayd_start adamcmiel/gatewayd:1.1.0

Now the webapp should be available on port 5000 of the running machine.
If you are running Boot2Docker or another VM install, you'll need to map the VM port to the host OS port.

## How to build locally

    ./build

Most docker installations require `sudo ./install`

#### If you built with ./build

    docker run --link db:db -d -p 5000:5000 --name gatewayd_start gatewayd

# TODO:

 - refactor db data to separate storage container
 - put all images (storage, db, app) in another container behind nginx
