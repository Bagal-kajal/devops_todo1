# Build Stage
FROM node:16 as build
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Production Stage
FROM node:16-alpine
WORKDIR /app
COPY --from=build /app/build /app
CMD ["node", "server.js"]
EXPOSE 3000
