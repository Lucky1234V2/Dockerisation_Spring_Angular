# Étape de construction
FROM node:18 AS build
WORKDIR /app
COPY frontend/package.json frontend/package-lock.json ./
RUN npm install
COPY frontend/ ./
RUN npm run build

# Étape de mise en production
FROM nginx:alpine
COPY --from=build /app/dist/frontend /usr/share/nginx/html
