FROM node:alpine as builder
WORKDIR /app
COPY ./package.json ./
RUN yarn install && yarn cache clean
COPY . .
RUN yarn build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
WORKDIR /usr/share/nginx/html
COPY  --from=builder /app/build .