# This specifies the parent/base image which docker should use. In this case, a NodeJS that runs on an Alpine Linux
FROM node:20-alpine3.17

# This tells docker the working directory. It also indicate where it should run the 'Phase 3' or any command.
WORKDIR /app

# Phase two is to copy the source code of the app into the image to be created. In here, it is the root directory and it should be copied into the root dir of the image
COPY . .

# Phase three specify the command(s) to be run on the image. This command essentially run all the dependencies in the 'package.json' file
# To install dependencies, we use RUN command. This command is usually ran in the root dir of the image. Hence we use WORKDIR to specify where it should run.
# This command runs during build time. that is as the image is being built
RUN npm install

# Required for docker desktop port mapping. This tells the container which port to expose. This maps the listening port specified in the source code
EXPOSE 4000

# This is used to start the application. This command will run after the image has started running
CMD ["node", "app.js"]