FROM node:12-alpine

RUN apk add --no-cache \
        ca-certificates \
        gcc

ENV RUSTUP_HOME=/usr/local/rustup \
    CARGO_HOME=/usr/local/cargo \
    PATH=/usr/local/cargo/bin:$PATH \
    RUST_VERSION=1.43.1

RUN set -eux; \
    url="https://static.rust-lang.org/rustup/archive/1.21.1/x86_64-unknown-linux-musl/rustup-init"; \
    wget "$url"; \
    echo "0c86d467982bdf5c4b8d844bf8c3f7fc602cc4ac30b29262b8941d6d8b363d7e *rustup-init" | sha256sum -c -; \
    chmod +x rustup-init; \
    ./rustup-init -y --no-modify-path --profile minimal --default-toolchain $RUST_VERSION; \
    rm rustup-init; \
    chmod -R a+w $RUSTUP_HOME $CARGO_HOME; \
    rustup --version; \
    cargo --version; \
    rustc --version;

RUN cd /usr/local/bin; \ 
    wget https://975-25250913-gh.circle-artifacts.com/0/releases/shadowsocks-v1.8.12.x86_64-unknown-linux-musl.tar.xz; \
    tar Jxvf shadowsocks-v1.8.12.x86_64-unknown-linux-musl.tar.xz; \
    rm -rf shadowsocks-v1.8.12.x86_64-unknown-linux-musl.tar.xz; \
    npm i -g shadowsocks-manager --unsafe-perm;
ENTRYPOINT [ "/usr/local/bin/ssmgr" ]