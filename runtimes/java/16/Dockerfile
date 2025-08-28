FROM        --platform=$TARGETOS/$TARGETARCH debian:latest

LABEL   	author="Jesper Richert" maintainer="dm@xyzjesper.dev"

RUN 		apt update -y \
			&& apt -y upgrade

RUN  		apt install -y \
				temurin-16-jdk \
				curl \
				git \
				iproute2 \
				ipset \
				sqlite3 \
				tar \
				tzdata \
				libfreetype6 \
				nginx

RUN     	useradd -m -d /home/container -s /bin/bash container
USER    	container
ENV     	USER=container HOME=/home/container
WORKDIR 	/home/container

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]