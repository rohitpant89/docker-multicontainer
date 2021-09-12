FROM node:14.14.0-alpine as builder
WORKDIR '/usr/local/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx
##Used in deployement like AWS EBS
EXPOSE 3000
COPY --from=builder  /usr/local/app/build /usr/share/nginx/html
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
