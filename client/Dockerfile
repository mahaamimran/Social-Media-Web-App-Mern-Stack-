#frontend
FROM node:18 AS builder
WORKDIR /app
COPY package.json .
RUN npm i
COPY . .
RUN  npm run build
#healthcheck
HEALTHCHECK --interval=30s --timeout=10s --retries=3 CMD curl -f http://localhost:4000/ || exit 1
FROM nginx 
COPY --from=builder /app/dist /usr/share/nginx/html
EXPOSE 80
CMD [ "nginx", "-g", "daemon off;" ]
