#backend
FROM node:18-alpine
WORKDIR /app
COPY package*.json .
RUN npm install
COPY . .
EXPOSE 4000
HEALTHCHECK --interval=30s --timeout=10s --retries=3 CMD curl -f http://localhost:4000/ || exit 1
CMD ["npm", "start"]