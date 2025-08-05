FROM        --platform=$TARGETOS/$TARGETARCH eclipse-temurin:20-jdk-ubi9-minimal

LABEL       author="Vexonic" maintainer="sysadmin@vexonic.cc"

LABEL       org.opencontainers.image.source="https://github.com/vexodev/pterodactyl-yolks"
LABEL       org.opencontainers.image.licenses=MIT

RUN         rm -rf /usr/bin/dd \
						&& rm -rf /usr/bin/fallocate \
						&& rm -rf /usr/bin/truncate \
                        && rm -rf /usr/bin/xfs_mkfile

RUN         microdnf update -y

RUN         curl -sSL https://github.com/OpticFusion1/MCAntiMalware/releases/latest/download/MCAntiMalware.jar \
						-o /MCAntiMalware.jar

RUN 				microdnf install -y jq unzip lsof ca-certificates openssl git tar sqlite fontconfig freetype tzdata iproute libstdc++ \
						&& useradd -d /home/container -m container

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]