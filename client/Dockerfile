#build stage
FROM alpine:3.16.7 AS build

RUN apk add --no-cache nodejs npm

WORKDIR /usr/src/app

COPY package*.json ./

RUN npm install --only=production

COPY . .

WORKDIR /app

#run time stage
FROM alpine:3.16.7

RUN apk add --no-cache nodejs

WORKDIR /app

COPY --from=build /usr/src/app /app/

EXPOSE 3000

CMD [ "npm", "start" ]