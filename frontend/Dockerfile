FROM node:10 as base

WORKDIR /app

COPY package*.json ./

RUN npm install 

COPY . .

RUN npm run build:production

FROM nginx:stable-alpine

COPY --from=base /app/build /usr/share/nginx/html

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]
