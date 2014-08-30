### Dockerfile
#
#   See https://github.com/russmckendrick/docker/

FROM russmckendrick/base:latest
MAINTAINER Russ McKendrick <russ@media-glass.es>

ADD nginx.repo /etc/yum.repos.d/
RUN yum -y install nginx tar && yum clean all
RUN sed -i '/worker_processes  1;/a daemon off;' /etc/nginx/nginx.conf
RUN sed -i 's/# server_names_hash_bucket/server_names_hash_bucket/g' /etc/nginx/nginx.conf

RUN mkdir /app
WORKDIR /app
ADD . /app

RUN tar -xvzf docker-gen.tar.gz
RUN curl -o /usr/local/bin/forego https://godist.herokuapp.com/projects/ddollar/forego/releases/current/linux-amd64/forego
RUN chmod u+x /usr/local/bin/forego

EXPOSE 80
ENV DOCKER_HOST unix:///tmp/docker.sock

CMD ["forego", "start", "-r"]