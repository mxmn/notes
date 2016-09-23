## Docker Cheatsheet

For more detailed information, see the
[original docker docs](https://docs.docker.com/).

#### Running docker images

##### Run Command
A simple version of running/launching a docker container:

`docker run [options] image command`

###### Run Options

Option | Description
----------|----------
`-it` | connect container to terminal & stdout
`-d`  | run in deamon mode
`--rm` | remove container after it exits
`--name app` | name the container
`-p 5000:80` | expose port 5000 externally and map to port 80
`-v ~/progs:/home/user/progs` | mount directory/volume from inside the host to the container

##### Other Image Interaction Commands

Command | Description
--------|-----------
`docker stop app` |
`docker kill app` |
`docker ps`       |
`docker network ls` |
`docker rm app` | Delete container `app`
`docker exec -it app bash` | Create a new bash process inside the container and connect it to the terminal
`docker logs --tail 42 app` | Print the last 42 lines of a container's logs
`docker images` | List all images that are locally stored within the Docker engine


#### Some sample commands

SSH tunnel to run docker image on a remote host:

    ssh -tL 7777:localhost:9999 remote-hostname docker run -it --rm -p 127.0.0.1:9999:8888 my-docker-image

Related/tunneled web page on local machine:

    http://127.0.0.1:7777

Launching a bash on the remote docker container with a volume mount:

    docker run -it --name=app -v /home/user/progs:/home/user/progs my-docker-image /bin/bash

Create an overlay network and specify a subnet:

    docker network create --subnet 10.1.0.0/24 --gateway 10.1.0.1 -d overlay mynet`
