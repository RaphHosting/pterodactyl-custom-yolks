FROM        --platform=$TARGETPLATFORM debian:bookworm-slim

LABEL       author="Michael Parker" maintainer="parker@pterodactyl.io"

LABEL       org.opencontainers.image.source="https://github.com/pterodactyl/yolks"
LABEL       org.opencontainers.image.licenses=MIT

RUN apt-get update && \
    apt-get install -y --no-install-recommends \
    gcc g++ gdb \
    git wget curl \
    tar zip unzip xz-utils \
    binutils \
    iproute2 net-tools netcat-openbsd telnet \
    libssl-dev \
    libsqlite3-dev sqlite3 \
    libmariadb-dev \
    zlib1g-dev \
    rapidjson-dev \
    liblua5.3-dev \
    locales \
    ffmpeg \
    ca-certificates \
	sudo \
    tzdata \
	python3 \
    python3-pip \
	systemd \
	wine \
	wine64 \
	xvfb \
	procps \
	coreutils \
	bash \
    && rm -rf /var/lib/apt/lists/*
RUN curl -LsSf https://astral.sh/uv/install.sh | sh
RUN export PATH="$HOME/.local/bin:$HOME/.cargo/bin:$PATH"

USER        root
ENV         USER=root HOME=/home/container
ENV         DEBIAN_FRONTEND=noninteractive

WORKDIR     /home/container

COPY        ./entrypoint.sh /entrypoint.sh
CMD         [ "/bin/bash", "/entrypoint.sh" ]
