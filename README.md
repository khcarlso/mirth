# Overview
MirthConnect allows organizations to standardize and exchange health related information. This repository contains:
* A Dockerfile for building the mirthconnect server image
* A Docker Compose YAML file for spinning up the environment


# Spinning up the environment
To create a local dockerized environment running Mirth and Postgres, use the following command:
`docker-compose up`

The first time this is run it will download the postgres:alpine image and build the khcarlso/mirth:latest image. also, You'll need ports 8080 and 8443 available on the host for the service to start successfully.

# Getting started with MirthConnect
After docker-compose has done its thing, navitage to http://localhost:8080 in a browser. Once the page loads, click on the admin
button to download the .jnlp file and run it from your desktop. The default username/password is admin/admin. You're in!

MirthConnect documentation is avialable here: http://www.mirthcorp.com/community/wiki/display/mirth/Getting+Started+Guide

# Other stuff

## Rebuild the Mirth image
To rebuild the mirth image, use:
`docker-compose build`

## Data Persists in a local Volume
The docker-compose.yml file makes use of a volume for storing the Postgres data so data used by Mirthconnect will persist across starts/stops of containers. If you wish to wipe out the volume and start again, use the following command:
`docker-compose down -v`

## Cleanup
To remove volumes, images, containers associated with the environment:
`docker-compose down -v --rmi all`








