FROM node:slim
MAINTAINER Riyaz Walikar <riyaz@appsecco.com>

RUN mkdir -p /usr/src/app
RUN npm install -g pm2

RUN curl https://raw.githubusercontent.com/CatTheCatch/Terragoat/main/terraform/aws/resources/app.js -o /usr/src/app/app.js
RUN curl https://raw.githubusercontent.com/CatTheCatch/Terragoat/main/terraform/aws/resources/package.json -o /usr/src/app/package.json

WORKDIR /usr/src/app
RUN npm install

EXPOSE 8080
CMD ["pm2","startup"]
CMD ["pm2","stop","app"]
CMD ["pm2","start","app.js","--name","app","--no-daemon"]
