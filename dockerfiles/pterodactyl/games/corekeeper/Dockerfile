FROM  --platform=$TARGETOS/$TARGETARCH ubuntu:22.04

LABEL author="Karsten Fiedler" maintainer="karsten@fiedleronline.net"

ENV   DEBIAN_FRONTEND noninteractive

## add container user
RUN   useradd -m -d /home/container -s /bin/bash container



RUN         dpkg --add-architecture i386 \
            && apt update \
            && apt upgrade -y \
			&& apt install -y libcurl4-gnutls-dev:i386 libssl3:i386 libcurl4:i386 lib32tinfo6 libtinfo6:i386 lib32z1 lib32stdc++6 libncurses5:i386 libcurl3-gnutls:i386 libsdl2-2.0-0:i386 \
 				gcc g++ libgcc1 libc++-dev gdb libc6 curl tar iproute2 net-tools libatomic1 libsdl1.2debian libsdl2-2.0-0 \
        		libfontconfig locales libcurl3-gnutls libpulse-dev libpulse0 gettext xfvb

## configure locale
RUN   update-locale lang=en_US.UTF-8 \
        &&   dpkg-reconfigure --frontend noninteractive locales


ENV         USER=container HOME=/home/container
WORKDIR     /home/container


COPY  ./entrypoint.sh /entrypoint.sh
CMD   [ "/bin/bash", "/entrypoint.sh" ]
