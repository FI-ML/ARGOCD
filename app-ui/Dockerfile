FROM node:18-alpine as build

WORKDIR /usr/src/app

COPY . .

RUN npm install
RUN npm install -g http-server
RUN npm run build --prod  --outputHashing=all


FROM nginx:stable-alpine
LABEL version="1.0"

WORKDIR /usr/share/nginx/html
COPY --from=build /usr/src/app/dist/angular-app /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/conf.d/default.conf


