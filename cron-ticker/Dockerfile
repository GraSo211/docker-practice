FROM node:19.2-alpine3.16 AS deps

WORKDIR /app

COPY package.json ./

RUN npm install 


FROM node:19.2-alpine3.16 AS builder

WORKDIR /app

COPY --from=deps /app/node_modules /app/node_modules

COPY . .

RUN npm run test


FROM node:19.2-alpine3.16 AS runner

WORKDIR /app

RUN rm -rf test && rm -rf node_modules

RUN npm install --prod

CMD ["node", "app.js"]
