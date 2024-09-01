#simple nginx image

FROM ubuntu:bionic

ENV NGIX_VERSION 1.14.0-0ubuntu1.11

RUN apt-get update && apt-get install -y curl
RUN apt-get update && apt-get install -y nginx=$NGIX_VERSION

CMD ["nginx", "-g", "daemon off;"]
