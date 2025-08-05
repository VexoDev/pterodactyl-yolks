FROM        --platform=$TARGETOS/$TARGETARCH eclipse-temurin:24-jdk-alpine

LABEL       author="Vexonic" maintainer="sysadmin@vexonic.cc"

LABEL       org.opencontainers.image.source="https://github.com/vexodev/pterodactyl-yolks"
LABEL       org.opencontainers.image.licenses=MIT

RUN         rm -rf /bin/dd \
						&& rm -rf /usr/bin/fallocate \
						&& rm -rf /usr/bin/truncate \
RUN         apk update \
						&& apk add curl

RUN         curl -sSL https://github.com/OpticFusion1/MCAntiMalware/releases/latest/download/MCAntiMalware.jar \
						-o /MCAntiMalware.jar

RUN 				apk add jq unzip bash lsof ca-certificates openssl git tar sqlite fontconfig freetype tzdata iproute2 libstdc++ \
						&& adduser -D -h /home/container container

USER        container
ENV         USER=container HOME=/home/container
WORKDIR     /home/container

COPY        ./../entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]