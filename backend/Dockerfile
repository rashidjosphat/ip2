# # Use an official Node runtime as a parent image
# FROM node:14 AS build

# # Set the working directory in the container
# WORKDIR /usr/src/app

# # Copy the package.json and package-lock.json files to the container
# COPY package*.json ./

# # Install application dependencies
# RUN npm install

# # Copy the rest of the application code to the container
# COPY . .

# #Add multi-stage build
# FROM alpine:3.16.7

# WORKDIR /app

# RUN apk update && apk add --update nodejs

# COPY --from=build /usr/src/app /app

# # Expose the port the app runs on
# EXPOSE 5000

# # Define the command to run your app
# CMD ["node", "server.js"]

# build stage
FROM alpine:3.16.7 AS build

WORKDIR /src/app

RUN apk add --no-cache nodejs npm

COPY pack*.json /src/app/

RUN npm install --only=production

COPY . .

#running stage
FROM alpine:3.16.7

WORKDIR /app

COPY --from=build /src/app /app

EXPOSE 5000

CMD [ "node", "server.js" ]