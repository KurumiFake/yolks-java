FROM        --platform=$TARGETOS/$TARGETARCH debian:buster-slim

LABEL       author="Michael Parker" maintainer="parker@pterodactyl.io"

LABEL       org.opencontainers.image.source="https://github.com/KurumiFake/yolksfake"
LABEL       org.opencontainers.image.licenses=MIT

RUN         apt update && apt upgrade -y \
		&& apt install -y libc++-dev curl libc6 iproute2 liblzo2-2 libatomic1 \
			libfontconfig libicu63 libunwind8 libssl-dev sqlite3 libsqlite3-dev \
			libmariadbclient-dev libduktape203 locales ca-certificates tzdata \
		&& apt remove -y --allow-remove-essential bash \
		&& update-locale lang=en_US.UTF-8 \
		&& dpkg-reconfigure --frontend noninteractive locales \
		&& useradd -m -d /home/container -s /bin/dash container

USER        container
ENV         USER=container HOME=/home/container
ENV         DEBIAN_FRONTEND noninteractive

WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/dash", "/entrypoint.sh" ]
