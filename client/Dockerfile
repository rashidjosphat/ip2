FROM node:14-alpine AS build

WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install
COPY . .

FROM node:14-alpine
WORKDIR /app
COPY --from=build /usr/src/app /app
EXPOSE 3000
CMD ["npm", "start"]
