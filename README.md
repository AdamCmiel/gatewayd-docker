# Warning
This software is for development purposes only and the author provides no warranty of any kind.

# Note
Most docker installations require super-user permissions, e.g. `sudo ./install`

# Install gatewayd with docker

This project breaks up the gatewayd app into two docker containers:
 - gatewayd
 - postgres (note this is for development, and data will not persist after the docker daemon is closed)
 - ripple-rest should be able to run in another container when rest wants to be actively developed

This is the docker way, ship the different pieces of your app in different containers and link them when running.

## Install Instructions

All of the building required is provided by the install.sh

    ./install

### Run that gateway

    ./run

Now the webapp should be available on port 5000 of the running machine.
If you are running Boot2Docker or another VM install, you'll need to map the VM port to the host OS port.

## How to build locally

Download gatewayd  into their respective directories 

    git clone https://github.com/ripple/gatewayd.git ./gatewayd/gatewayd
    ./build

### If you built with ./build, to run:

    ./run-build

# TODO:

 - refactor db data to separate storage container
 - put all images (storage, db, app) in another container behind nginx

