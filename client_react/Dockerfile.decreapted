FROM node:alpine

WORKDIR '/app'

COPY package*.json ./
RUN npm install 
COPY . .
# 这边之间 build 整个 react 的项目
RUN npm run build 

# 因为react 项目 build 完之后，没有 server 能够支持，所以我们需要 nginx 
FROM nginx 
EXPOSE 80
COPY --from=0 /app/build /usr/share/nginx/html 
# 上面这个 copy的意思就是从 build 中拿出来我们要的文件，然后复制到我们想要复制到的 位置