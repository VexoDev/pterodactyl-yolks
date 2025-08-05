FROM        --platform=$TARGETOS/$TARGETARCH eclipse-temurin:18-jdk-centos7

LABEL       author="Vexonic" maintainer="sysadmin@vexonic.cc"

LABEL       org.opencontainers.image.source="https://github.com/vexodev/pterodactyl-yolks"
LABEL       org.opencontainers.image.licenses=MIT

RUN		 	sed -i 's/mirrorlist/#mirrorlist/g' /etc/yum.repos.d/CentOS-*
RUN			sed -i 's|#baseurl=http://mirror.centos.org|baseurl=http://vault.centos.org|g' /etc/yum.repos.d/CentOS-*

RUN         rm -rf /usr/bin/dd \
						&& rm -rf /usr/bin/fallocate \
						&& rm -rf /usr/bin/truncate \
                        && rm -rf /usr/bin/xfs_mkfile

RUN         yum update -y \
						&& yum install -y curl

RUN         curl -sSL https://github.com/OpticFusion1/MCAntiMalware/releases/latest/download/MCAntiMalware.jar \
						-o /MCAntiMalware.jar

RUN 				yum install -y jq unzip lsof ca-certificates openssl git tar sqlite fontconfig freetype tzdata iproute libstdc++ \
						&& useradd -d /home/container -m container

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]