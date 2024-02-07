FROM ubuntu:20.04 #server image

MAINTAINER JUNGWOO 

# apt 미러서버 미국(default) -> 한국 변경
RUN sed -i 's@archive.ubuntu.com@kr.archive.ubuntu.com@g' /etc/apt/sources.list


RUN \
    apt-get update && \
    apt-get install -y nginx mariadb:10.4 


WORKDIR /home/user1

# node exporter 1.3.1
RUN \
    wget https://github.com/prometheus/node_exporter/releases/download/v1.3.1/node_exporter-1.3.1.linux-amd64.tar.gz && \
    tar -zxf node_exporter-1.3.1.linux-amd64.tar.gz && \
    mv node_exporter-1.3.1.linux-amd64 node_exporter && \
    rm -rf node_exporter-1.3.1.linux-amd64.tar.gz

ENTRYPOINT /home/user1/node_exporter/node_exporter --web.listen-address=:9500 & bash

ENV \
    MARIADB_ROOT_PASSWORD=test123 \
    MARIADB_DATABASE=docker \
    MYSQL_USER=docker \
    MYSQL_PASSWORD=docker \








#Nginx
EXPOSE 80
#https
EXPOSE 443
#mariadb
EXPOSE 3306
#node-exporter
EXPOSE 9500 
#cAdvisor
EXPOSE 8080




CMD [ "nginx", "-D", "FOREGROUND" ]
CMD [ "mariadb", "-D", "FOREGROUND" ]
CMD [ "", "-D", "FOREGROUND" ]
CMD [ "mariadb", "-D", "FOREGROUND" ]
