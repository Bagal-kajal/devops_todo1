# Stage 1: Build Stage
FROM node:18-alpine AS builder

WORKDIR /app

# Copy package.json and package-lock.json, then install dependencies
COPY package*.json /app
RUN npm install

# Copy the rest of the application code
COPY . .

# Optional: Check the files after copying
RUN ls -al /app/

# Stage 2: Production Stage
FROM node:18-alpine AS runner

WORKDIR /app

# Copy necessary files from the builder stage
COPY --from=builder /app /app

# Expose port 8080
EXPOSE 3000

# Run the application
CMD ["node", "server.js"]
