FROM node:alpine
WORKDIR '/app'
COPY package*.json ./
RUN npm install
COPY ./ ./
RUN npm run build

FROM nginx:1.18.0
EXPOSE 3000
COPY ./nginx/default.conf /etc/ngnix/conf.d/000_my_config.conf
COPY --from=0 /app/build /usr/share/nginx/html

