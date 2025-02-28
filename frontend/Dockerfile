FROM node:14-alpine AS build
WORKDIR /app
COPY package*.json /app
RUN npm install
COPY . /app
RUN npm run build 

FROM node:14-alpine AS prod
WORKDIR /app
COPY --from=build /app/build ./build
COPY --from=build /app/package*.json ./
EXPOSE 8080
CMD ["npm", "run", "start"]