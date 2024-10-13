
FROM node:18-alpine AS build

WORKDIR /usr/src/app

COPY pack*.json /src/app/

RUN npm install --only=production

COPY . .

#running stage
FROM alpine:3.16.7

WORKDIR /app

COPY --from=build /usr/src/app /app

RUN apk add --no-cache npm nodejs

EXPOSE 5000

CMD [ "node", "server.js" ]