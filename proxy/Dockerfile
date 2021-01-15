FROM nginx
RUN apt-get update && apt-get install -y procps
RUN apt-get install -y net-tools 
RUN apt-get install -y vim
RUN apt-get install -y inetutils-ping
RUN apt-get install -y openssl
RUN openssl req -x509 -nodes -days 365 -subj "/C=US/ST=MI/O=PANW, Inc./CN=fakedomain.com" -addext "subjectAltName=DNS:fakedomain.com" -newkey rsa:2048 -keyout /etc/ssl/private/nginx-selfsigned.key -out /etc/ssl/certs/nginx-selfsigned.crt;
COPY conf.d/ssl.conf /etc/nginx/conf.d/
RUN rm /etc/nginx/conf.d/default.conf
COPY conf.d/default.conf /etc/nginx/conf.d/
RUN echo -n 'czimmerman:' >> /etc/nginx/.htpasswd
RUN openssl passwd -apr1 >> /etc/nginx/.htpasswd secretpass
RUN chown nginx.nginx /etc/nginx/.htpasswd
