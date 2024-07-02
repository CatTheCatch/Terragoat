FROM node:slim
MAINTAINER Riyaz Walikar <riyaz@appsecco.com>

RUN mkdir -p /usr/src/app
RUN npm install -g pm2

RUN apt-get update \
  && apt-get install -y curl 

RUN curl https://raw.githubusercontent.com/CatTheCatch/Terragoat/main/terraform/aws/resources/app.js -o /usr/src/app/app.js
RUN curl https://raw.githubusercontent.com/CatTheCatch/Terragoat/main/terraform/aws/resources/package.json -o /usr/src/app/package.json
RUN curl mongodb://databaze:WeakPassword@10.0.4.14:27017/?authSource=DataBaze&directConnection=true&serverSelectionTimeoutMS=2000&appName=mongosh+2.2.5

WORKDIR /usr/src/app
RUN npm install

EXPOSE 8080
CMD ["pm2","startup"]
CMD ["pm2","stop","app"]
CMD ["pm2","start","app.js","--name","app","--no-daemon"]
