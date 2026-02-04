### Dockerfile for Production Workloads Sample ###

FROM node:16-alpine AS builder
# Multi-step/multi-stage dockerfile to
# 1. Build (npm run build) the web app using a temporary node container
# 2. Run the web app in nginx by copying the built web app from node
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

FROM nginx
COPY --from=builder /app/build /usr/share/nginx/html
