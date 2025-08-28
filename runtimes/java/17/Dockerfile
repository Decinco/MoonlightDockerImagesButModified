FROM        --platform=$TARGETOS/$TARGETARCH debian:latest

LABEL   	author="Jesper Richert" maintainer="dm@xyzjesper.dev"

RUN 		apt update -y \
			&& apt -y upgrade

RUN 		apt install -y wget apt-transport-https gpg

RUN			wget -qO - https://packages.adoptium.net/artifactory/api/gpg/key/public | gpg --dearmor | tee /etc/apt/trusted.gpg.d/adoptium.gpg > /dev/null

RUN 		echo "deb https://packages.adoptium.net/artifactory/deb $(awk -F= '/^VERSION_CODENAME/{print$2}' /etc/os-release) main" | tee /etc/apt/sources.list.d/adoptium.list

RUN 		apt update -y \
			&& apt -y upgrade

RUN  		apt install -y \
				temurin-17-jdk \
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