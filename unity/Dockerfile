FROM ubuntu:18.04

RUN apt-get update;
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

RUN wget -nv https://beta.unity3d.com/download/6e9a27477296/UnitySetup-2018.3.0f2 -O unity.deb; \
  # compare sha1 if given
  if [ -n "${SHA1}" -a "${SHA1}" != "" ]; then \
    echo "${SHA1}  unity.deb" | shasum -a 1 --check -; \
  else \
    echo "no sha1 given, skipping checksum"; \
  fi

# install unity
RUN dpkg -i unity.deb && rm unity.deb
  # make a directory for the certificate Unity needs to run
RUN mkdir -p $HOME/.local/share/unity3d/Certificates/

ADD CACerts.pem $HOME/.local/share/unity3d/Certificates/

# Clean up
RUN rm -rf /tmp/* /var/tmp/*