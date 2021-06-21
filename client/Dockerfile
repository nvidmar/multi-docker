FROM node:alpine as builder

WORKDIR '/usr/src/app'

COPY ./package.json ./
# To Fix Permissions for Packages
RUN npm config set unsafe-perm true
RUN npm install
COPY . .
RUN npm run build

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /usr/src/app/build /usr/share/nginx/html