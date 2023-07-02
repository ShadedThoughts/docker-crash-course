# This specifies the parent/base image which docker should use. In this case, a NodeJS that runs on an Alpine Linux
FROM node:20-alpine3.17

# Optional commands [Volumes]
# The command is useful with volume mapping which maps volume on the host to the image working directory. Nodemon restarts the npm server when it notices any change in the volume or files
# Once there's changes to files in volumes, nodemon (Node package) which is installed globally, restarts the server to reflect the changes automatically.
RUN npm install -g nodemon

# This tells docker the working directory. It also indicate where it should run the 'Phase 3' or any command.
WORKDIR /app

# To achieve layer caching in docker, This first copy command copies all package* file since that's the location where dependencies are specified 
COPY package*.json .

# Phase three specify the command(s) to be run on the image. This command essentially run all the dependencies in the 'package.json' file
# To install dependencies, we use RUN command. This command is usually ran in the root dir of the image. Hence we use WORKDIR to specify where it should run.
# This command runs during build time. that is as the image is being built
RUN npm install

# Phase two is to copy the source code of the app into the image to be created. In here, it is the root directory and it should be copied into the root dir of the image
COPY . .

# Required for docker desktop port mapping. This tells the container which port to expose. This maps the listening port specified in the source code
EXPOSE 4000

# This is used to start the application. This command will run after the image has started running
# CMD ["node", "app.js"]

# This command run the dev script inside the package.json file. However, we could also add scripts to Dockerfile itself
CMD [ "npm", "run", "dev" ]

## Docker commands - https://stackify.com/docker-build-a-beginners-guide-to-building-docker-images/ and https://devopscube.com/build-docker-image/
## > docker build --tag [name:version] .
## > docker images
## > docker ps
## > docker run --name [container_name] --publish [local_port:container_port] --detach image_name
## > docker stop [container_name]
## > docker ps -a
## > docker start [image_name]
## > docker container rm [container_name]
## > docker container rm -f $(docker container ls -aq)
## > docker image rm [image_name]
## > docker image rm [image_name] --force
## > docker image rm -f $(docker image -q)
## > docker attach [container_name]
## > docker system prune -a [This deletes every image, containers and volumes]
## > docker run --name [container_name] --publish [local_port:container_port] --detach --rm -v [absolute_local_path:image_path] -v /app/node_modules image_name

## > docker network ls
## > docker exec -it [container_id] sh
## > docker exec -it [container_id] -u root api_c sh

# Installing docker-compose using https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-compose-on-ubuntu-20-04
## > docker-compose up --detach
## > docker-compose up --detach --scale api=4
## > docker-compose down --rmi all -v
## > docker-compse config

## https://github.com/daczarne/mosh_docker/tree/main/06_running_multicontainer_applications#creating-a-compose-file
## https://gist.github.com/ju2wheels/3d1a1dfa498977874d03
## https://manpages.ubuntu.com/manpages/xenial/man5/Dockerfile.5.html
## https://docs.docker.com/compose/compose-file/compose-file-v3/ -- Reference