# `kagent-docker`

## Overview

Directory containing a `Dockerfile` to build an Ubuntu 18.04 image 
with an installed SSH server.

Addionally there is a `docker-compose` file `kagent-docker-compose.yaml` which
will start up a KAgent docker container along with two other containers named
`head` and `worker`. The KAgent container can be used to provision a
two node Kinetica cluster using the `head` and `worker` containers.

During installation you will need the ip addresses of the two containers and they are set to fixed ip addresses of: -

* head container - `kinetica-api-java-training_gpudb-head_1` - 172.20.0.10
* worker container - `kinetica-api-java-training_gpudb-worker_1` - 172.20.0.20


## Building the Docker Image (Optional)

Firstly, we build the docker container image from the commandline using the following: -

```Bash
docker build -t donstewart/ubuntu:18.04-ssh .
```

Docker will look in the `.` directory i.e. current directory for a file called Dockerfile. This means you need to run
the command in the same directory as the `Dockerfile` if you use `.`.

the `-t` parameters tags the build image and is followed by the name of the image e.g. `donstewart/ubuntu:18.04-ssh` 
which will be the name on the local machine if you run a `docker image ls` and what you need to do on a 
`docker run` command.

!!! tip
    You do not need to do this step as the docker compose file will pull the image from the Docker Hub if it does not 
    find it locally meaning the build is not needed nless there are modification made to the image.

## Starting the Three Node Cluster





