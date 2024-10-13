#build stage
FROM node:18-alpine AS build

WORKDIR /usr/src/app

RUN apk add --no-cache nodejs npm



COPY package*.json ./

RUN npm install --omit=dev

COPY . .

WORKDIR /app

#run time stage
FROM alpine:3.16.7

WORKDIR /app/


RUN apk add --no-cache nodejs npm


COPY --from=build /usr/src/app /app/

EXPOSE 3000

CMD [ "npm", "start" ]