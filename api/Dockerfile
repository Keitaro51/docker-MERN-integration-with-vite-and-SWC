FROM node:20-alpine

RUN npm install -g nodemon

# app files isolation (naming conflict, security, better organisation, etc...). Avoid working on root directory
WORKDIR /app

COPY package.json .

# during build time. Running this layer before COPY allow to cache it (remember, layer is not cached, stack of layers are copied) but need package.json to be available before
RUN npm install

COPY . .

# Container exposed port, not computer port. Should be mapped with local machine port
EXPOSE 4000

# during runtime
CMD ["npm", "run", "dev"]

# docker build -t imageName:eventualVersionName . (build image, not running container)
# docker images  (list of images with id)
# docker run --name myapp_c -p 4000:4000 -d -rm -v absoluteLocalPath:containerMappedPath imageName or imageID (run image, so create a new container, with myapp_c as name, mapping local_port to container_port, in detached terminal mode then remove container after stopped)

#  docker ps (list running containers flag -a for all existing containers)
# docker stop containerId or containerName
# docker star containerId or containerName (restart an existing container by default in detached mode)

# docker image rm imageName or imageId (delete an unsused image or use -f flag to force deletion)
# docker container rm containerName or containerId (delete one or more container)

# docker system prune -a (delete everything)