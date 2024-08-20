FROM node:20-alpine AS base

FROM base AS dependecies

WORKDIR /app

COPY package.json .
COPY package-lock.json .
RUN npm ci

FROM base AS builder

WORKDIR /app

COPY --from=dependecies /app/node_modules ./node_modules
COPY . .

RUN npm run build

FROM base AS runner

WORKDIR /app

COPY --from=builder /app/public ./public

RUN mkdir .next

COPY --from=builder /app/.next/standalone .
COPY --from=builder /app/.next/static ./.next/static

CMD node server.js
