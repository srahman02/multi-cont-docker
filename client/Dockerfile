# select base image as node:alpine and give it a name for second phase of the build
FROM node:alpine as builder
# create an app folder inside the container
WORKDIR '/app'
# copy package.json file inside app folder from work directory
COPY ./package.json ./
# Run npm install command
RUN npm install
# copy all source code from work directory to app folder in container
COPY . .
#Run npm run build for production enviornment
RUN npm run builder


FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html