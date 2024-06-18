FROM debian:12-slim

RUN apt-get update \
    && apt-get install -y curl ca-certificates openssl \
    && rm -rf /var/lib/apt/lists/*

COPY Cloudflare_CA.pem .
RUN mv Cloudflare_CA.pem /usr/local/share/ca-certificates/Cloudflare_CA.crt && \
    dpkg-reconfigure -f noninteractive ca-certificates

WORKDIR /app

COPY ./entrypoint.sh .

ENTRYPOINT [ "/app/entrypoint.sh" ]