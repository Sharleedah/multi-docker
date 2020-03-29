# Purpose: Install Dependencies + Setup Application
FROM node:alpine as builder 
WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . . 
RUN npm run build

#Pro Block nur ein FROM - Statement
FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
