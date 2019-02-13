FROM ubuntu:18.04

ENV UNITY3D_VERSION '2018.3.0f2'
ENV DEBIAN_FRONTEND=noninteractive

RUN apt-get update;
RUN apt-get install -y --no-install-recommends apt-utils;
RUN apt-get install -y libsoup2.4 libarchive-dev;
RUN apt-get install -y git gconf-service lib32gcc1 lib32stdc++6 libasound2;
RUN apt-get install -y libc6 libc6-i386 libcairo2 libcap2 libcups2 libdbus-1-3;
RUN apt-get install -y libexpat1 libfontconfig1 libfreetype6 libgcc1 libgconf-2-4;
RUN apt-get install -y libgdk-pixbuf2.0-0 libgl1-mesa-glx libglib2.0-0 libglu1-mesa;
RUN apt-get install -y libgtk2.0-0 libnspr4 libnss3 libpango1.0-0 libstdc++6;
RUN apt-get install -y libx11-6 libxcomposite1 libxcursor1 libxdamage1 libxext6;
RUN apt-get install -y libxfixes3 libxi6 libxrandr2 libxrender1 libxtst6 zlib1g;
RUN apt-get install -y debconf npm xdg-utils lsb-release libpq5;
RUN apt-get install -y xvfb wget;
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

ADD https://beta.unity3d.com/download/6e9a27477296/UnitySetup-${UNITY3D_VERSION} /opt/Unity
RUN chmod +x /opt/Unity
RUN mkdir /opt/Unity-${UNITY3D_VERSION} && yes | /opt/Unity --unattended --install-location /opt/Unity-${UNITY3D_VERSION} && rm -rf /tmp/* /var/tmp/*