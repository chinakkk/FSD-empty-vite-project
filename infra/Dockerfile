FROM node:20 AS build
ARG PUBLISH_TOKEN
ARG REACT_APP_BASE_URL
WORKDIR /app
COPY . .
RUN npm install
RUN npm run build

FROM node:alpine
COPY --from=build /app/build /app/build
WORKDIR /app
RUN npm install -g serve
EXPOSE 3000
CMD ["serve", "-s", "dist"]
