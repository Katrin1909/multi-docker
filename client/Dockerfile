FROM node:alpine as builder

WORKDIR '/app'
COPY ./package.json ./
# RUN npm config set proxy http://rgb-proxy.avl.com:8080
# RUN npm config set https-proxy http://rgb-proxy.avl.com:8080
RUN npm install
COPY . .

RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html