#
# Nasqueron - Jenkins slave Docker image for Rust applications
#

FROM nasqueron/jenkins-slave-barebone
MAINTAINER Sébastien Santoro aka Dereckson <dereckson+nasqueron-docker@espace-win.org>

#
# Prepare the container
#
# Rustup installation and libs to use Diesel from https://github.com/emk/rust-musl-builder
#

RUN apt-get update && \
    apt-get install -y build-essential cmake git curl nano vim file \
                   libpq-dev libsqlite-dev pkgconf sudo xutils-dev openssl \
                   strace gdb libssl-dev wget libpcre3-dev && \
    apt-get autoremove && apt-get clean && \
    groupadd -r app -g 433 && \
    mkdir /home/app && \
    useradd -u 431 -r -g app -d /home/app -s /bin/sh -c "Default application account" app && \
    chown -R app:app /home/app && \
    chmod 711 /home/app

USER app
ENV TOOLCHAIN=nightly

RUN curl https://sh.rustup.rs -sSf | sh -s -- -y --default-toolchain $TOOLCHAIN && \
    /home/app/.cargo/bin/rustup component add clippy-preview --toolchain=nightly && \
    /home/app/.cargo/bin/rustup component add rustfmt-preview --toolchain=nightly
