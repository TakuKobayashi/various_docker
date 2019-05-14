FROM ubuntu:18.04
FROM node:10.15.3-jessie

RUN apt-get update
RUN apt-get install -y git wget xz-utils build-essential cmake libfreetype6-dev libsdl2-dev libass-dev git-core libva-dev libvdpau-dev automake autoconf zlib1g-dev libtool libx264-dev libvorbis-dev libxcb1-dev libxcb-shm0-dev libxcb-xfixes0-dev pkg-config texinfo 

# YASM
WORKDIR /opt
RUN wget http://www.tortall.net/projects/yasm/releases/yasm-1.3.0.tar.gz
RUN tar xf yasm-1.3.0.tar.gz
WORKDIR /opt/yasm-1.3.0
RUN ./configure
RUN make
RUN make install

# YASM
WORKDIR /opt
RUN wget https://www.nasm.us/pub/nasm/releasebuilds/2.14.02/nasm-2.14.02.tar.bz2
RUN tar xjvf nasm-2.14.02.tar.bz2
WORKDIR /opt/nasm-2.14.02
RUN ./autogen.sh
RUN ./configure
RUN make
RUN make install

# x264
WORKDIR /opt
RUN git clone --depth 1 git://git.videolan.org/x264.git
WORKDIR /opt/x264
RUN ./configure --enable-static
RUN make
RUN make install

# fdk-aac
WORKDIR /opt
RUN git clone --depth 1 git://github.com/mstorsjo/fdk-aac.git
WORKDIR /opt/fdk-aac
RUN autoreconf -fiv
RUN ./configure --disable-shared
RUN make
RUN make install

WORKDIR /opt
RUN wget https://ffmpeg.org/releases/ffmpeg-4.1.3.tar.bz2
RUN tar xjf ffmpeg-4.1.3.tar.bz2
WORKDIR /opt/ffmpeg-4.1.3
RUN ./configure --enable-gpl --enable-libaom --enable-libass  --enable-libfdk-aac --enable-libfreetype --enable-libmp3lame --enable-libopus --enable-libvorbis --enable-libvpx --enable-libx264  --enable-libx265 --enable-nonfree
RUN make
RUN make install

CMD /bin/bash