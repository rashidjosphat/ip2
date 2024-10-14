FROM node:18-alpine as build

WORKDIR /usr/src/app/

COPY package*.json /usr/src/app/

RUN npm install

COPY . .

#running stage
FROM alpine:3.16.7

WORKDIR /app/

COPY --from=build /usr/src/app/ /app/


RUN apk add --no-cache npm nodejs


EXPOSE 3000

CMD [ "npm", "start" ]
