# Build stage
FROM node:18 AS build

WORKDIR /app

# Install dependencies first
COPY package*.json ./
RUN npm install

# Copy source files
COPY . .

# Build app — make sure this line has correct syntax
RUN npm run build -- --configuration=production

# Serve stage
FROM nginx:alpine

# Make sure the dist path matches what's generated
COPY --from=build /app/dist/frontend /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
