#simple nginx image

FROM ubuntu:bionic

ENV NGIX_VERSION 1.14.0-0ubuntu1.11

RUN apt-get update && apt-get install -y curl
RUN apt-get update && apt-get install -y nginx=$NGIX_VERSION

WORKDIR /var/www/html
#WORKDIR /var

#WORKDIR www

#WORKDIR html

#COPY index.hml ./

ADD index.html ./

EXPOSE 80

CMD ["nginx", "-g", "daemon off;"]

STOPSIGNAL SIGTERM

HEALTHCHECK CMD curl localhost:80
