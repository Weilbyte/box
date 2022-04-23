#armv7
FROM debian:bullseye-slim as build

RUN apt-get update && \
    apt-get install --yes --no-install-recommends git python3 build-essential cmake ca-certificates gcc-arm-linux-gnueabihf && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/{apt,dpkg,cache,log} /tmp/* /var/tmp/*

RUN git clone https://github.com/ptitSeb/box86.git; mkdir /box86/build

WORKDIR /box86/build
RUN cmake .. -DCMAKE_BUILD_TYPE=RelWithDebInfo && \
    make -j$(nproc) && \
    make install DESTDIR=/tmp/install

FROM debian:bullseye-slim
LABEL "maintainer"="Weilbyte <me@weilbyte.dev>"
LABEL "org.opencontainers.image.source"="https://github.com/weilbyte/box"

COPY --from=build /tmp/install /

ENTRYPOINT ["box86"]