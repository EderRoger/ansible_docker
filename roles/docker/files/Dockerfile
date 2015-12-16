FROM ubuntu:14.04
MAINTAINER Eder Roger "eder.roger.souza@gmail.com"
ENV REFRESHED_AT 2015-12-01

RUN apt-get update && apt-get install -y nginx

RUN mkdir -p /var/www/html/website

ADD /tmp/index.html /var/www/html/website/index.html

ADD /vagrant/roles/docker/files/global.conf /etc/nginx/conf.d/
ADD /vagrant/roles/docker/files/nginx.conf /etc/nginx/nginx.conf

ENTRYPOINT ["/usr/sbin/nginx", "-g", "daemon off;"]

EXPOSE 80
