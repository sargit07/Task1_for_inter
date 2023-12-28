FROM node:16-alpine AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

FROM node:16-alpine AS runner

WORKDIR /app

COPY --from=builder /app/build /app
COPY --from=builder /app/package*.json ./

RUN npm install --production

EXPOSE 3000

CMD ["node", "server.js"]