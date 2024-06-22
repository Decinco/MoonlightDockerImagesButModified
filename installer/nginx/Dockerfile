FROM --platform=$TARGETOS/$TARGETARCH debian:latest

ENV         DEBIAN_FRONTEND noninteractive

RUN apt update 
RUN apt install curl ca-certificates nginx -y
RUN apt install php-common php-fpm libapache2-mod-php php-cli -y

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY ./entrypoint.sh /entrypoint.sh

CMD ["/bin/bash", "/entrypoint.sh"]
