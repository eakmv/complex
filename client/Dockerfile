FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build

FROM nginx 
EXPOSE 3000
COPY ./nginx/defautl.conf /etc/nginx/conf.d/default.conf
COPY --from=buidler /app/build /usr/share/html/nginx/html