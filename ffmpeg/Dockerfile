FROM ubuntu:18.04

LABEL authors="Takukobayashi<keep_slimbody@yahoo.co.jp>"

RUN apt-get update && apt-get install -y git wget xz-utils

WORKDIR /tmp

RUN wget http://johnvansickle.com/ffmpeg/releases/ffmpeg-release-64bit-static.tar.xz
RUN tar Jxvf ./ffmpeg-release-64bit-static.tar.xz
RUN cp ./ffmpeg*64bit-static/ffmpeg /usr/local/bin/

CMD /bin/bash