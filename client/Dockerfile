# specify the base image
FROM node:alpine as builder

# do the setup
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . . 
RUN npm run bild

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf ./etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html