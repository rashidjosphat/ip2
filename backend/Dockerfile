
FROM node:18-alpine AS build

WORKDIR /usr/src/app

COPY package*.json /usr/src/app/

RUN npm install --omit=dev

COPY . .

#running stage
FROM alpine:3.16.7

WORKDIR /app

COPY --from=build /usr/src/app /app

RUN apk add --no-cache npm nodejs

EXPOSE 5000

CMD [ "node", "server.js" ]