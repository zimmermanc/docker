FROM nginx
RUN apt-get update && apt-get install -y procps
RUN apt-get install -y net-tools 
RUN apt-get install -y vim
RUN apt-get install -y inetutils-ping
RUN rm /etc/nginx/conf.d/default.conf
RUN rm /usr/share/nginx/html/*
COPY ./content/index.htm /usr/share/nginx/html/
COPY ./conf.d/default.conf /etc/nginx/conf.d/default.conf
